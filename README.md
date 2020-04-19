# Riot Messaging Application for the Desktop

_Riot messaging client packaged (RPMs) for Fedora, CentOS, Red Hat Enterprise Linux, and OpenSUSE_

Riot is a client implementing the matrix protocol enabling decentralized, secure messaging for collaborative groups. It's a great client, but it needed RPM packages built for the Red Hat family of Linux operating systems. So... here they be!

_**What is Riot (and Matrix)?**_ In short, Riot is an open source, decentralized, end-to-end encrypted team collaboration platform who's often compared to IRC, Rocket Chat, Mattermost, Slack, etc.

This GitHub repository maintains source RPM packages and spec files so you can rebuild Riot if you are so inclined. From these source packages runnable binaries have been conveniently built for you. See below for how to install and run Riot on your Linux desktop.

All \*.src.rpm packages provided in this GitHub repository should be signed with [my GPG key](https://keybase.io/toddwarner/key.asc)<br />All binary RPMs are signed with the [Fedora Project's](https://fedoraproject.org/) [COPR GPG signing key](https://copr-be.cloud.fedoraproject.org/results/taw/Riot/pubkey.gpg)

#### More about...

* Riot: <https://riot.im/> and <https://github.com/vector-im/riot-web>
* Matrix: <https://matrix.org/> and <https://en.wikipedia.org/wiki/Matrix_(communication_protocol)>
* A couple reviews from [some dude](http://www.1500wordmtu.com/2016/slack-no-more-why-you-should-use-riotim-and-matrixorg), [TechCrunch](https://techcrunch.com/2016/09/19/riot-wants-to-be-like-slack-but-with-the-flexibility-of-an-underlying-open-source-platform/), and the [Slant community](https://www.slant.co/options/12764/~matrix-review)<br />_Unsurprisingly, I personally think Riot is superior to Slack and Rocket Chat._

# tl;dr ...

## I just want to install Riot!

It's easy to install and run Riot. Currently built for these platforms (x86\_64 only)...  
_Note: I will stop building for any version of an OS that is itself no longer supported_

* Fedora: versions 30+
* CentOS (and RHEL): Riot 1.5 and older. See also GitHub issues [#31](https://github.com/taw00/riot-rpm/issues/31) and [#33](https://github.com/taw00/riot-rpm/issues/33).
* OpenSUSE:
  - Tumbleweed: all versions of Riot
  - Leap 15.1: Riot 1.5 and older. See also GitHub issue [#32](https://github.com/taw00/riot-rpm/issues/32).
  - Leap 15.2: We'll see. See also GitHub issue [#34](https://github.com/taw00/riot-rpm/issues/34).
* The test repositories: I will usually try to build test packages for any OS that is in beta if I have time.
* Flatpak: Though I personally view Flatpaks as last resort packaging solutions (they are a brute force / relatively-inefficient method of packaging), they do serve their purpose. Leap 15.1 and EL8(RHEL/CentOS) folks can use the Riot-team supplied Flatpak: <https://flathub.org/apps/details/im.riot.Riot>

### For Fedora...

_Note that, by default, the 'riot-stable' repository will be enabled and 'riot-testing' will not._ 

**Prep...**
```bash
# Snag the repository configuration (should only need to do once)
sudo rpm --import https://keybase.io/toddwarner/key.asc
sudo dnf install -y https://github.com/taw00/riot-rpm/raw/master/toddpkgs-riot-repo.fedora.rpm
```
**Install...**
```bash
# install Fedora's distribution GPG keys (should only need to do once)
sudo dnf install -y distribution-gpg-keys
# Install riot
sudo dnf install -y riot --refresh
```

### For RHEL/CentOS version 8...

_Note that, by default, the 'riot-stable' repository will be enabled and 'riot-testing' will not._ 

**Prep...**
```bash
# Snag the repository configuration (should only need to do once)
sudo rpm --import https://keybase.io/toddwarner/key.asc
sudo dnf install -y https://github.com/taw00/riot-rpm/raw/master/toddpkgs-riot-repo.epel.rpm
```
**Install...**
```bash
# install Fedora's distribution GPG keys (should only need to do once)
sudo dnf install -y distribution-gpg-keys
# Install riot
sudo dnf install -y riot --refresh
```

### For CentOS or RHEL version 7...

_Note that, by default, the 'riot-stable' repository will be enabled and 'riot-testing' will not._ 

**Prep...**
```bash
# Snag the repository configuration (should only need to do once)
sudo rpm --import https://keybase.io/toddwarner/key.asc
sudo yum install -y https://github.com/taw00/riot-rpm/raw/master/toddpkgs-riot-repo.epel.rpm
```
**Install...**
```bash
# install distribution GPG keys (should only need to do once)
sudo yum install -y distribution-gpg-keys
# Clean out the cache in case the change didn't get picked up
sudo yum clean expire-cache
# Install riot
sudo yum install -y riot
```

### For OpenSUSE...

**Prep (OpenSUSE Leap)...**
```bash
# Snag the repository configuration (should only need to do once)
sudo rpm --import https://keybase.io/toddwarner/key.asc
sudo zypper install https://github.com/taw00/riot-rpm/raw/master/toddpkgs-riot-repo.suse.leap.rpm
sudo zypper modifyrepo -er "riot-stable"
```

**Prep (OpenSUSE Tumbleweed)...**
```bash
# Snag the repository configuration (should only need to do once)
sudo rpm --import https://keybase.io/toddwarner/key.asc
sudo zypper install https://github.com/taw00/riot-rpm/raw/master/toddpkgs-riot-repo.suse.tw.rpm
sudo zypper modifyrepo -er "riot-stable"
```

**Install...**
```bash
# Clean out the cache in case the change didn't get picked up
sudo zypper refresh
# Install riot
sudo zypper install riot
```

## I installed it, now I want to run Riot!

Search for and select "Riot" from your desktop or run `riot` from the command line.

Note: If none of this made sense or you couldn't get it to work, Riot can also be run as directly from your browser at <https://riot.im/app>

## I installed it, now I want to ensure I get future updates!

Once you have followed the repository and installation instructions above, you should be notified of any future updates enabling you to update the software automatically. And you can always force a check with...

Note that with updates you may have to do a `killall riot-web` (`riot-desktop` in Riot v1.6). Quiting the application doesn't really "quit it" nor does the flush cache reload function in the UI.

```bash
# Fedora (any version) and RHEL/CentOS (version 8)...
sudo dnf upgrade
```
```bash
# CentOS or RHEL version 7...
sudo yum update
```
```bash
# OpenSUSE...
sudo zypper update
```

I do this as a hobby, but I will try to be timely with my updates.

## I live on the edge! Do you have test packages available?

Yes!

1. Follow the steps described above to install the repository configure file.  
   _You will have to refresh it if you have done this before today._
2. Disable the stable repository and enable the testing repository...
```
# Fedora (any version) and RHEL/CentOS (version 8) only
sudo dnf config-manager --set-disabled riot-stable
sudo dnf config-manager --set-enabled riot-testing
sudo dnf list --refresh |grep riot
```


# Disclaimer

I built these for my own use. I offer these builds for your own convenience. If it 'splodes your computer, I am sorry, but buyer beware. :) I am in no way affiliated with the originators of Riot -- [New Vector](https://vector.im/) -- but I do thank them for their contribution.

# Questions or comments...

Contact: **t0dd_at_protonmail.com** or find me at **@t0dd:matrix.org** after you have installed Riot!
