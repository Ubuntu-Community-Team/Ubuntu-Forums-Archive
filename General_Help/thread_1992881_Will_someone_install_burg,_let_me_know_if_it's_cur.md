---
title: "Will someone install burg, let me know if it's currently working?"
date: 2012-06-01
forum: General Help
---

### Post by mikeeey on 2012-06-01
I've tried for days to get burg working, on 3 separate versions of Linux (Ubuntu 12.04, Linux Mint, and Pinguy), and I just can't get it working. During the download/install I noticed some error messages, including 404 not found errors. I'm starting to think there's something wrong with the repository (ppa:bean123ch/burg).
But there's always the possibility it's my computer too.
Would someone be able to install burg and let me know if it's working for them?

[http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/)

The MOST I've been able to get out of it is THIS message:
BURG  version 1.98+20100623-2.3

```
   Minimal BASH-like line editing is supported. For the first word, TAB
   lists possible command completions. Anywhere else TAB lists possible
   device or file completions.

grub>
```

Thanks!

---

### Post by satish_j on 2012-06-01
you can configure themes for grub menu without installing burg..
You just have to download a theme,copy it to /boot/grub/themes folder and make a entry for it in /etc/default/grub as:
GRUB_THEME=<path to theme.txt>
run 'sudo update-grub' and it should detect the theme right away..

---

### Post by wilee-nilee on 2012-06-01
The last release supported in that PPA is maverick.

This one is updated though for precise.
[https://launchpad.net/~n-muench/+archive/burg](https://launchpad.net/~n-muench/+archive/burg)

---

### Post by mikeeey on 2012-06-01
> **wilee-nilee said:**
> The last release supported in that PPA is maverick.

This one is updated though for precise.
[https://launchpad.net/~n-muench/+archive/burg](https://launchpad.net/~n-muench/+archive/burg)

added this one and installed all of the burg packages (from Ubuntu Software Center). Nothing changed. Still getting the same thing.

Even sudo update-burg still doesn't work, it just says:
```
/usr/sbin/burg-mkconfig: 8: /etc/default/burg: Syntax error: "(" unexpected

```

---

### Post by wilee-nilee on 2012-06-01
> **mikeeey said:**
> added this one and installed all of the burg packages (from Ubuntu Software Center). Nothing changed. Still getting the same thing.

Even sudo update-burg still doesn't work, it just says:
```
/usr/sbin/burg-mkconfig: 8: /etc/default/burg: Syntax error: "(" unexpected

```

You have to load burg to the mbr once set up. I have never seen an error with burg, so I can't really help there.

All you had to do was before using the new PPA was to remove the not working PPA then run

```
sudo apt-get purge burg-pc burg-common
```Then with the new ppa installed after running a 

```
sudo apt-get update
```then 

```
sudo apt-get install burg-pc burg-common
```And when asked where burg goes choose the HD only no partitions. 

I have never used any extra burg stuff, and never use the software center as well.

I suspect you have not cleaned out the original burg stuff with a purge, and maybe have tried to install burg extras which are not compatible, having not run a update after adding a repo.

Note that when you purge a bootloader, install another or you will not be booting in.

---

### Post by mikeeey on 2012-06-03
> **wilee-nilee said:**
> You have to load burg to the mbr once set up. I have never seen an error with burg, so I can't really help there.

All you had to do was before using the new PPA was to remove the not working PPA then run

```
sudo apt-get purge burg-pc burg-common
```Then with the new ppa installed after running a 

```
sudo apt-get update
```then 

```
sudo apt-get install burg-pc burg-common
```And when asked where burg goes choose the HD only no partitions. 

I have never used any extra burg stuff, and never use the software center as well.

I suspect you have not cleaned out the original burg stuff with a purge, and maybe have tried to install burg extras which are not compatible, having not run a update after adding a repo.

Note that when you purge a bootloader, install another or you will not be booting in.

That fixed it! Thank you!!!:KS
Now I wonder why these steps weren't mentioned in any of the guides?

The main thing I did incorrectly was during the first time install when it asks where I want Burg to install I told it hd0 or hd1. I wasn't aware I could proceed without typing anything. After that I used the burg-emu from burg manager and it showed the way it should. After restart I still had grub, and I realized I had to click "restore burg to MBR" through burg manager.

As far a purging, I had never done it up to this point. My purge was formating and reinstalling Ubuntu lol.

Thanks again! Hopefully this topic will help anyone searching that was in the same boat as me.

---

### Post by wilee-nilee on 2012-06-03
> **mikeeey said:**
> That fixed it! Thank you!!!:KS
Now I wonder why these steps weren't mentioned in any of the guides?

The main thing I did incorrectly was during the first time install when it asks where I want Burg to install I told it hd0 or hd1. I wasn't aware I could proceed without typing anything. After that I used the burg-emu from burg manager and it showed the way it should. After restart I still had grub, and I realized I had to click "restore burg to MBR" through burg manager.

As far a purging, I had never done it up to this point. My purge was formating and reinstalling Ubuntu lol.

Thanks again! Hopefully this topic will help anyone searching that was in the same boat as me.

No problem, burg is pretty much a version of grub2 that has built in themes, and I'm a little familiar with grub 2 and have used burg, so enjoy. ;)

---

