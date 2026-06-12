---
title: "Alien fails on conversion of rpm files"
date: 2010-04-16
forum: General Help
---

### Post by malorzean on 2010-04-16
Having downloaded alien for the first time, and attempted to use it to convert an rpm file to a deb file (specifically asymptote located at asymptote.sourceforge.net), instead I found that it failed to do so. I've searched on google for a long while, and found that while this appears to be a problem encountered by multiple people, but there are no workarounds posted anywhere. Here is the error message that I am getting:

Unpacking of 'asymptote-1.92-1.fc12.i686.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 153.

I've tried running the following variants of commands and all fail with the same error:

sudo alien --to-deb --scripts --keep-version asymptote-1.92-1.fc12.i686.rpm

sudo alien -d asymptote-1.92-1.fc12.i686.rpm

sudo alien -k asymptote-1.92-1.fc12.i686.rpm

The errors reported by others are on a variety of packages, so it seems to me that it is an bug with alien itself and not with the package, but that is only a guess.

And related to this, Alien is version 8.69, perl 5.8.8 and ubuntu is 8.04.

Are there any suggestions?

---

### Post by srs5694 on 2010-04-16
First, asymptote is available in Ubuntu -- at least, it shows up in Synaptic on my Ubuntu 9.10 system. You should be able to install it using Synaptic or by typing "sudo apt-get install asymptote".

Second, I've encountered the problem you're reporting, but it appears to be dependent on the version of rpmbuild used to create the RPM file. I haven't traced the specifics, but recent versions of Fedora (meaning anything from the last year or two) create RPM files that alien can't parse. Older packages work fine. I haven't been following alien development all that closely; perhaps a newer version than you or I are using would work better. (The latest on [the alien Web site](http://kitenet.net/~joey/code/alien/) is 8.79.)

FWIW, I use a bizarre system to create the binaries for my own [GPT fdisk](http://sourceforge.net/projects/gptfdisk/files/) package: I build a source RPM on a Gentoo system, then build binary RPMs for i386, x86-64, and PPC on Ubuntu, Gentoo, and Debian systems, respectively, and then create Debian packages using alien. I do this partly because of what I happen to have installed on various real and virtual machines but partly because alien can't parse the RPMs created by Fedora 12. Oddly, the Gentoo-, Debian-, and Ubuntu-generated RPMs seem to install more easily on a wide variety of RPM-based systems than do RPMs built on RPM-based distributions (Fedora or SUSE).

---

### Post by nothingspecial on 2010-04-16
Why not just build it

```
sudo apt-get install subversion build-essential
svn co http://asymptote.svn.sourceforge.net/svnroot/asymptote/trunk/asymptote
cd asymptote
./autogen.sh
./configure
make all
sudo make install
```

I can also see a link to some debs on sourceforge aswell, but can`t seem to post them here, for some reason

---

### Post by malorzean on 2010-04-18
Thanks a lot for the advice.

---

