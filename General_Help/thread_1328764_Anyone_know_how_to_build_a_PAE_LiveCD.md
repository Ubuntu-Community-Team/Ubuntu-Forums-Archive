---
title: "Anyone know how to build a PAE LiveCD?"
date: 2009-11-16
forum: General Help
---

### Post by lotuseclat79 on 2009-11-16
I have been attempting to do this for Karmic 9.10 using the released distribution as a starting point roughly following the article, How-To: Customize your Ubuntu Live CD (2 web pages) located at: [http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd)

To top it off, I am working in the Karmic LiveCD 9.10 environment w/4GB RAM - you know what I'm after!  However, I have built a staging area on my hard disk for the livecd and its subdirectories which seems workable.

First off, in the chrooted environment on hard disk, I do remove all non-english language-packs to save space and I plan to remove games as well - this helps greatly vs not doing it to make the LiveCD burnable.

Of course, there are several problems when the non-pae linux-image linux-generic and linux-headers are removed and the PAE versions are substituted via apt-get remove and apt-get install commands and everything is burned into what should (in theory) be a working PAE Live CD with no problems (ok, there are some problems).

The first problem I ran into is that my CDROM with a setup script that I use to help initialize my LiveCD environment cannot be mounted (I have a 2nd CDROM drive) - this has always worked with previous releases.  I get the following message:
Unable to mount CDROM

Error mounting: mount exited with exit code 32: mount:
block device /dev/sr1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr1,
   missing codepage or helper program, or other error
   In some cases useful info is found in syslog - try
   dmesg | tail or so

The second problem I ran into is that iptables which depends on the /lib/modules/2.6.31-14-generic directory components (compiled into iptables which iptables depends upon) does not want to play with the /lib/modules/2.6.31-14-generic-pae components (even with a symbolic link of the non-pae directory to the new pae directory) and puts out a message that indicates Invalid module format, and says Perhaps iptables or your kernel needs to be upgraded, and also do you need to insmod?

The third problem is a real stumper.  When I do a dpkg-query on the sizeof the intalled packages for one of the linux-image-generix packages I get that a 4.8 MB size is installed, however, when I go over to /var/lib/dpkg/info for the LiveCD pae version that I burned, and issue an ls -lt <pkgname.list> command for it, it yields that there are no files in the list with a size of 0?  Here is the data I generated:
4:86.0391  MB  linux-image-2.6.31-14-generic
and
-rw-r--r-- 1 root root      0 2009-11-16 12:50 linux-image-2.6.31-14-generic.list

It is beginning to look like the only way to succeed at building a PAE Karmic LiveCD for Ubuntu is to compile the entire kernel for PAE - is that the ticket?  Or, does everything in the Karmic 9.10 LiveCD release need to be compiled for PAE?

-- Tom

---

