---
title: "Problem Updating"
date: 2010-09-16
forum: General Help
---

### Post by slotto on 2010-09-16
Hi,
I am fairly new to Linux - approx 1 year. About every 3 months or so I have problems with the update manager. I let it update when it asks and periodically it becomes corrupt and I get frustrated and have to reinstall. I'm starting to learn the terminal commands to try to repair using tips from this forum but I am at my wits end. Also wondering if this is attributed to a hardware issue like maybe RAM.

I would love to be able to fix my problems without having to reinstall every time.
Here's my problem this time:

```
steve@steve-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bogofilter bogofilter-bdb bogofilter-common firefox firefox-3.5
  firefox-3.5-branding firefox-3.5-gnome-support firefox-branding
  firefox-gnome-support lftp libsmbclient libwbclient0 libwww-perl
  samba-common samba-common-bin smbclient sudo tzdata wget xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support xulrunner-1.9.2
22 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/50.2MB of archives.
After this operation, 4,096B disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libhtml-parser-perl' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```If anyone could help I sure would appreciate it.
Thanks,
Steve

---

### Post by searchfgold6789 on 2010-09-16
Just to clarify:
this happens *every* time even if you reinstall?

---

### Post by slotto on 2010-09-16
about 3 months after a reinstall. It's really frustrating. It's on an older dell box.

I have 9.10 installed on a newer laptop and I never have any problems with it.

---

### Post by ubunterooster on 2010-09-16
sudo apt-get autoclean?

---

### Post by slotto on 2010-09-16
I did the autoclean... then update then upgrade and I get the same final result...
```
steve@steve-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bogofilter bogofilter-bdb bogofilter-common firefox firefox-3.5
  firefox-3.5-branding firefox-3.5-gnome-support firefox-branding
  firefox-gnome-support lftp libsmbclient libwbclient0 libwww-perl
  samba-common samba-common-bin smbclient sudo tzdata wget xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support xulrunner-1.9.2
22 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.4MB/50.2MB of archives.
After this operation, 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic-updates/main xulrunner-1.9.1-gnome-support 1.9.1.13+build1+nobinonly-0ubuntu0.9.10.1 [40.6kB]
Get:2 http://security.ubuntu.com karmic-security/main firefox-gnome-support 3.6.10+build1+nobinonly-0ubuntu0.9.10.1 [76.4kB]
Get:3 http://us.archive.ubuntu.com karmic-updates/main xulrunner-1.9.1 1.9.1.13+build1+nobinonly-0ubuntu0.9.10.1 [7,999kB]
Get:4 http://security.ubuntu.com karmic-security/main firefox-branding 3.6.10+build1+nobinonly-0ubuntu0.9.10.1 [203kB]
Get:5 http://security.ubuntu.com karmic-security/main firefox 3.6.10+build1+nobinonly-0ubuntu0.9.10.1 [11.2MB]
Get:6 http://us.archive.ubuntu.com karmic-updates/main xulrunner-1.9.2 1.9.2.10+build1+nobinonly-0ubuntu0.9.10.1 [9,654kB]
Get:7 http://security.ubuntu.com karmic-security/main firefox-3.5 3.6.10+build1+nobinonly-0ubuntu0.9.10.1 [76.2kB]
Get:8 http://security.ubuntu.com karmic-security/main firefox-3.5-branding 3.6.10+build1+nobinonly-0ubuntu0.9.10.1 [75.9kB]
Get:9 http://security.ubuntu.com karmic-security/main firefox-3.5-gnome-support 3.6.10+build1+nobinonly-0ubuntu0.9.10.1 [75.9kB]
Fetched 29.4MB in 8s (3,427kB/s)                                               
Preconfiguring packages ...
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libhtml-parser-perl' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Is there something that I can delete then get fresh from the install cd?

thanks

---

### Post by searchfgold6789 on 2010-09-16
You said you were relatively new to linux... So, I'm going to run you by the basics if you don't mind!
Try the following solutions in this order.

[LIST=1]
[*]Use Synaptic to completely remove the packages libhtml-parser-perl and libwww-perl, then reinstall it.
[*]Check for broken packages. (in Synaptic: click custom filters, then click broken)
[*]Try looking in the forums for a way to totally avoid downloading libhtml-parser-perl whenever you upgrade. Or you could do an investigation and look on the debian.com website for the .deb installer for that package and see if you can install it manually.
[*]Make a new install CD. Make sure the checksums on the file you download match (google how to do this; it's easy), and burn the CD at the slowest speed available to you. Doing both of these will help you very much. I have wasted about 30 CD's (not kidding) because i am too lazy to checksum and burn safely.
[*]If this does not work, try a memory test. You can select memtest from the grub menu. If you get lots of errors, then it is probably upgrade time.
[*]You could also try a different distribution of ubuntu, or maybe even a different distribution of linux such as debian, redhat, or opensuse.
[/LIST]
I hope this helps!
 - search

---

### Post by slotto on 2010-09-17
Thanks search,
I've tried 1 & 2 with no luck. It appears that dpkg is corrupt. I will try your other suggestions. Thanks for the help!
Steve

---

### Post by Soul-Sing on 2010-09-17
```
gksudo nautilus
```

navigate to /usr/bin/dpkg/info
remove via the search-option: libhtml-parser-perl

close nautilus
```
sudo apt-get update
```

---

### Post by limestone on 2010-09-17
maybe fail in apt. try aptitude instead..
sudo aptitude update
sudo aptitude upgrade

---

### Post by searchfgold6789 on 2010-09-17
Before you do that...
Try reinstalling dpkg from the live CD.

[LIST=1]
[*]Boot from the live CD to get a desktop.
[*]Open up a terminal.
[*]Type in ```
sudo fdisk -l
``` to find out your main system partition. This is referred to as sdXX from now on.
[*]type in ```
sudo mount /dev/sdXX /mnt 
```
[*]```
sudo mount --bind /dev  /mnt/dev 
```
[*]```
sudo mount --bind /dev/pts  /mnt/dev/pts 
```
[*]```
sudo mount --bind /proc /mnt/proc 
```
[*]```
sudo mount --bind /sys  /mnt/sys 
```
[*]```
sudo chroot /mnt 
```
[*]Try:
[/LIST]

[LIST]
[*]sudo dselect update
[*]restart. If it still doesn't work do steps 1-9 all over again. Try:
[*]sudo apt-get remove dpkg
[*]sudo apt-get install dpkg
[*]restart, still doesnt work try: (boot up live cd)
[*]Open up the file on your home folder on the CD.
[*]Copy /var/lib/dpkg/available (this is a file) to the same directory on your harddisk.
[/LIST]
I hope this solves your problem; but if it doesn't work one of my other suggestions will certainly help.
 - search

---

### Post by slotto on 2011-03-18
It was bad ram. Thanks for your help!
slotto

---

