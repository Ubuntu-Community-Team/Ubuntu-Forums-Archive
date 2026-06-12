---
title: "Need Help With dpkg, libc6"
date: 2009-07-09
forum: General Help
---

### Post by AClark on 2009-07-09
I just installed XUbuntu Jaunty 32 on an old HP Laptop w/AMD processor & 512Meg Memory

I am setting this up for a friend's 2 young daughters to use and have done very little so far.

I installed Wine & VLC with Synaptics and as Synaptics was finishing configuring the installs I received an error telling me to run dpkg --configure -a from terminal

Here is the terminal output:

```
townsley@HP-ZE-1000:~$ sudo dpkg --configure -a
[sudo] password for townsley: 
Setting up libc6 (2.9-4ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Illegal instruction
dpkg: subprocess post-installation script returned error exit status 132
townsley@HP-ZE-1000:~$ 
```With other packages I might have tried a "dpkg --remove -purge" and reinstall
Since this package is critical to the system I suspect that Ubuntu wouldn't let me even if I tried.

In any case I would appreciate some guidance on how  to resolve this.

In case it's of any help here is the relevant info from /var/lib/dpkg/status

***************************************
Package: libc6
Status: deinstall ok half-configured
Priority: required
Section: libs
Installed-Size: 10904
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: glibc
Version: 2.9-4ubuntu6
Config-Version: 2.9-4ubuntu6
Replaces: belocs-locales-bin
Provides: glibc-2.9-1
Depends: libgcc1, findutils (>= 4.4.0-2ubuntu2)
Suggests: locales, glibc-doc, libc6-i686
Conflicts: libterm-readline-gnu-perl (<< 1.15-2), tzdata (<< 2007k-1), tzdata-etch, nscd (<< 2.9)
Conffiles:
 /etc/init.d/glibc.sh 2c80f6dbaf625f97ce29f96700779ab5
 /etc/ld.so.conf.d/i486-linux-gnu.conf 36f09aeeab18f6af453d0a1db0a0942c
 /etc/ld.so.conf.d/libc.conf d4d833fd095fb7b90e1bb4a547f16de6
 /etc/gai.conf ab538b366edabe44a9a4020fdd3d93a4
 /etc/bindresvport.blacklist db84c47f31f8d5a334a4053d8368e902
Description: GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
***************************************************************

ps - I ran "sudo dpkg -r libc6 figuring because of dependencies it would not allow removing and the resulting output might give me a clue -

Edit- Both Wine & VLC seem to be working OK

---

### Post by AClark on 2009-07-09
Bump

---

### Post by AClark on 2009-07-10
Anybody ??

---

### Post by michy99 on 2009-07-10
Try backing up the status file and replacing it with the old file.```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.backup
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```If it works, you can delete the backup.```
sudo rm /var/lib/dpkg/status.backup
```

---

### Post by AClark on 2009-07-10
Thanks for the answer.

Unfortunately renaming status-old doesn't help because when I ran dpkg -r to see if the output would help me to understand what was happening a new status file was created and the status-old overwritten with the then current status file.

I have tried to be patient and figure this out without making things worse but in this case not patient enough I guess.

I don't have a great deal of time invested in this install so far - So I guess I could just reinstall, but I am at least as interested in understanding what is happening and how  to deal with it as I am in getting the system set up.

---

### Post by michy99 on 2009-07-10
If you have backed up the status file, try deleting it and see if updating works.```
sudo rm /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by AClark on 2009-07-11
Deleting /var/lib/dpkg/status caused dpkg to complain that it couldn't open the status file - how  logical :)

I found some archived backups in /var/backups (again - logical) I restored the newest one that had Package: libc6 as installed ok.

I was then able to run apt-get upate and the update manager came up listing 10 updates that were available - libpurple, libtiff, pidgin, hal & libxcb.  I chose to install, they downloaded and as updates were being configured the following message came up and I am back where I started.

I am puzzled that libc6 is being configured since it wasn't ever listed as an update.

[IMG]http://img17.imageshack.us/img17/7222/libc6.png[/IMG]

Then the message telling me to run dpkg --configure -a  and the same results as in my first post.

Thanks for your encouragement - I am definitely learning more about how dpkg works - just not enough yet.

This all started as I was installing VLC & Wine with Synaptic - I don't know if it is significant but the status file shows VLC as installed ok but no sign of WINE.

 (Ignore *Wine-Error - thats just the name I gave to the file on the desktop where I saved the output from dpkg when it first happened & I thought it was related to WINE)

---

