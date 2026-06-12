---
title: "How to use Mondo Rescue at Ubuntu 10.4 LTS?"
date: 2010-05-16
forum: General Help
---

### Post by erdanblo on 2010-05-16
Hi!

I want to use Mondo Rescue with Ubuntu 10.4 LTS, but don't work by GRUB version.

Mondo try to rescue /etc/grub.conf or similar, but with the new version of grub, all boot system has been changed.

Any ideas?

Can i to change Grub to a lower version (witch use /boot/grub/menu.lts, and similar? How?

Thank you.

---

### Post by mfseeker on 2010-06-04
Create a symbolic link called /etc/grub.conf linked to /boot/grub/grub.cfg.

---

### Post by robinbillings on 2010-07-20
Why doesn't ubuntu make the version that corrects this problem 2.2.9.4 available as the default package, rather than one that is dated (2.2.7-2.1) and just doesn't work with the new grub?

Robin

---

### Post by cadriel on 2010-07-28
The other issue is that Ubuntu seems to think it has the newest version of the software, even after you add the mondo source into apt sources list.

It's a pain, since you can't gracefully update using mondo's sources.

This really needs to be resolved!

---

### Post by cadriel on 2010-07-28
Here's a solution to this problem for now;

[http://trac.mondorescue.org/wiki/FAQ#Q11DoesmondoworkwithDebianUbuntudistributions](http://trac.mondorescue.org/wiki/FAQ#Q11DoesmondoworkwithDebianUbuntudistributions)

---

### Post by MakOwner on 2010-10-07
> **cadriel said:**
> Here's a solution to this problem for now;

[http://trac.mondorescue.org/wiki/FAQ#Q11DoesmondoworkwithDebianUbuntudistributions](http://trac.mondorescue.org/wiki/FAQ#Q11DoesmondoworkwithDebianUbuntudistributions)

I don't see anything in this link that describes a fix for 10.4LTS and the grub versioning. 

Is there a PPA that can be used to get a working version of Mondo?

---

### Post by andy987 on 2010-10-27
I think it would be a bad idea to downgrade grub, or link to V2 grub config, and I didn't like the look of the instructions in the above link....

So I did the following and it works just fine. The new grub file is found and mondo built my ISO's.

Don't use the old version of mondo in the ubuntu repository (as at 27-Oct-2010 at least). Remove mondo and mindi with dpkg, if necessary.

Fix (Tested on Ubuntu 10.10):
[LIST]
[*]cd /var/tmp
[*]wget [ftp://ftp.mondorescue.org/ubuntu/10.04/mindi_2.0.7.5-1_i386.deb](ftp://ftp.mondorescue.org/ubuntu/10.04/mindi_2.0.7.5-1_i386.deb)
[*]wget [ftp://ftp.mondorescue.org/ubuntu/10.04/mondo_2.2.9.4-1_i386.deb](ftp://ftp.mondorescue.org/ubuntu/10.04/mondo_2.2.9.4-1_i386.deb)
[*]wget [ftp://ftp.mondorescue.org/ubuntu/10.04/mindi-busybox_1.7.3-1_i386.deb](ftp://ftp.mondorescue.org/ubuntu/10.04/mindi-busybox_1.7.3-1_i386.deb)
[*]dpkg -i mondo_2.2.9.4-1_i386.deb mindi_2.0.7.5-1_i386.deb mindi-busybox_1.7.3-1_i386.deb
[/LIST]

Confirm you have the following (or later versions) of the required packages:
[FONT="Courier New"]**dpkg -l mondo mindi mindi-busybox**
[INDENT]ii  mindi          2.0.7.5-1      creates boot/root disks based on your system
ii  mindi-busybox  1.7.3-1        creates a busybox version suited for mindi
ii  mondo          2.2.9.4-1      powerful disaster recovery suite[/INDENT][/FONT]

Now build your backup ISO with mondoarchive!

---

### Post by aalopes on 2010-11-02
I'm using Ubuntu 10.04 and I'm using mondo 2.2.9.4-1_i386. After using mondoarchive and performing a full system backup to the disk (an ISO I latter burned to a DVD which is working BTW) there appears an unmounted FAT 16 loop device in Disk Utility (check attached image). However when I do

```
losetup -a
```I find no loop devices. And loop device /dev/loop0 appears to be unused.
Also the only way I have found of removing it is by doing

```
sudo palimpsest
```and going to the "Check Filesystem" button which gives me the error "Filesystem is not clean" and simply removes the loop device.
What behavior is this? Is this a normal mondo thing? And is there a cleaner way of removing the loop device?

---

### Post by Axis Mann on 2010-11-15
Yeah?  What's everyone doing about authentication?  When I try to install the latest version of mondo from mondorescue.org, ubuntu 10.04 tells me that it can't authenticate the packages.  I go to mondo rescue but find no references to a gpg key.  Also, the ftp  URL listed in the sources.list file at mondo for the latest deb seems malformed to me ([ftp://ftp.mondorescue.org//ubuntu](ftp://ftp.mondorescue.org//ubuntu) 10.04 contrib).  I tried changing the //ubuntu to /ubuntu and updating the preference file but then I started getting the authentication warnings using either Ubuntu Software Center or Synaptic.  I tried Synaptic after the Ubuntu Software Center refused to load the latest version.  It looked like Synaptic might have let me load but I didn't try since it wanted to know if it was ok to proceed without authentication.  Me thinks I still need a gpg key for the Software Sources Authentication tab but I can't find one anywhere.  Where can I get the release.gpg file that I need for successful authentication of the mondorescue packages for Ubuntu 10.04?

---

### Post by Axis Mann on 2010-11-15
The actual authentication error I was getting was "Requires installation of untrusted packages" when I tried to install the latest version of mondo from mondorescue.org.  It seems to me that the only way around that problem is for me to find a key file with which to update the Software Sources Authentication tab.  Is everyone else not getting that error;  cause I see nothing mentioned out there with regards to the workarounds for the non-working version supplied in the ubuntu repos?

---

