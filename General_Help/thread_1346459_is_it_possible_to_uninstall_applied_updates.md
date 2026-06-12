---
title: "is it possible to uninstall applied updates"
date: 2009-12-05
forum: General Help
---

### Post by stvdel on 2009-12-05
I checked the history in the Synaptic Manager, I am not sure but does this also show security updates? I am not sure what Ubuntu defines as security updates or how to check what these are and when they were applied.

---

### Post by hardfire_avk on 2009-12-05
To stop auto installation and ask for notifications

this is what happens in Ubuntu 9.10
Goto
System->Administration->Update Manager
Click on Settings
Select the Updates Tab
Automatic updates -> Only notify about available updates

---

### Post by slakkie on 2009-12-05
Yes, it is possible.

```

apt-cache policy iceweasel
iceweasel:
  Installed: 3.5.5-1
  Candidate: 3.5.5-1
  Version table:
 *** 3.5.5-1 0
        990 ftp://ftp.nl.debian.org unstable/main Packages
        100 /var/lib/dpkg/status
     3.0.14-1 0
        600 ftp://ftp.nl.debian.org testing/main Packages
     3.0.6-3 0
        500 http://security.debian.org lenny/updates/main Packages
     3.0.6-1 0
        500 ftp://ftp.nl.debian.org lenny/main Packages

```

Let's say I don't want 3.5.5-1, but I want the one from testing (3.0.14-1).

Then I would say:
aptitude install iceweasel=3.0.14-1

This will downgrade your iceweasel install.

You might want to change your policy in between so the updates are not applied automaticly, otherwise you can keep doing this :)

---

### Post by 3rdalbum on 2009-12-05
If a security update has caused problems for you, you should immediately notify the Ubuntu developers ([www.launchpad.net](www.launchpad.net) - try and find what package has affected the system and file a bug).

---

### Post by wilee-nilee on 2009-12-05
There is also a history in synaptic.

---

### Post by stvdel on 2009-12-05
Hello thank you for all your help, the problem is that because I had it set to automatically install these updates I don't know what the update was, how do I find out what the last update that got applied was so I can report a problem.

---

### Post by slakkie on 2009-12-05
check

/var/log/dpkg.log
/var/log/aptitude
/var/log/apt/term.log

---

### Post by stvdel on 2009-12-05
Thanks slakkie, can anyone see anything in here that might be a suspect? All I know is it was around this time today and my computer had a message pop up asking to restart.

2009-12-05 12:14:20 startup archives unpack
2009-12-05 12:14:44 install linux-image-2.6.31-16-generic <none> 2.6.31-16.52
2009-12-05 12:14:44 status half-installed linux-image-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:15:01 status unpacked linux-image-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:15:01 status unpacked linux-image-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:15:02 upgrade linux-generic 2.6.31.15.28 2.6.31.16.29
2009-12-05 12:15:02 status half-configured linux-generic 2.6.31.15.28
2009-12-05 12:15:02 status unpacked linux-generic 2.6.31.15.28
2009-12-05 12:15:02 status half-installed linux-generic 2.6.31.15.28
2009-12-05 12:15:02 status half-installed linux-generic 2.6.31.15.28
2009-12-05 12:15:02 status unpacked linux-generic 2.6.31.16.29
2009-12-05 12:15:02 status unpacked linux-generic 2.6.31.16.29
2009-12-05 12:15:03 upgrade linux-image-generic 2.6.31.15.28 2.6.31.16.29
2009-12-05 12:15:03 status half-configured linux-image-generic 2.6.31.15.28
2009-12-05 12:15:03 status unpacked linux-image-generic 2.6.31.15.28
2009-12-05 12:15:03 status half-installed linux-image-generic 2.6.31.15.28
2009-12-05 12:15:03 status half-installed linux-image-generic 2.6.31.15.28
2009-12-05 12:15:03 status unpacked linux-image-generic 2.6.31.16.29
2009-12-05 12:15:03 status unpacked linux-image-generic 2.6.31.16.29
2009-12-05 12:15:03 install linux-headers-2.6.31-16 <none> 2.6.31-16.52
2009-12-05 12:15:03 status half-installed linux-headers-2.6.31-16 2.6.31-16.52
2009-12-05 12:15:07 status unpacked linux-headers-2.6.31-16 2.6.31-16.52
2009-12-05 12:15:07 status unpacked linux-headers-2.6.31-16 2.6.31-16.52
2009-12-05 12:15:07 install linux-headers-2.6.31-16-generic <none> 2.6.31-16.52
2009-12-05 12:15:07 status half-installed linux-headers-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:15:09 status unpacked linux-headers-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:15:09 status unpacked linux-headers-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:15:09 upgrade linux-headers-generic 2.6.31.15.28 2.6.31.16.29
2009-12-05 12:15:09 status half-configured linux-headers-generic 2.6.31.15.28
2009-12-05 12:15:09 status unpacked linux-headers-generic 2.6.31.15.28
2009-12-05 12:15:09 status half-installed linux-headers-generic 2.6.31.15.28
2009-12-05 12:15:09 status half-installed linux-headers-generic 2.6.31.15.28
2009-12-05 12:15:09 status unpacked linux-headers-generic 2.6.31.16.29
2009-12-05 12:15:09 status unpacked linux-headers-generic 2.6.31.16.29
2009-12-05 12:15:09 upgrade linux-libc-dev 2.6.31-15.50 2.6.31-16.52
2009-12-05 12:15:09 status half-configured linux-libc-dev 2.6.31-15.50
2009-12-05 12:15:09 status unpacked linux-libc-dev 2.6.31-15.50
2009-12-05 12:15:09 status half-installed linux-libc-dev 2.6.31-15.50
2009-12-05 12:15:10 status half-installed linux-libc-dev 2.6.31-15.50
2009-12-05 12:15:11 status unpacked linux-libc-dev 2.6.31-16.52
2009-12-05 12:15:11 status unpacked linux-libc-dev 2.6.31-16.52
2009-12-05 12:15:11 startup packages configure
2009-12-05 12:15:11 configure linux-image-2.6.31-16-generic 2.6.31-16.52 2.6.31-16.52
2009-12-05 12:15:11 status unpacked linux-image-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:15:11 status half-configured linux-image-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:17:24 status installed linux-image-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:17:24 configure linux-image-generic 2.6.31.16.29 2.6.31.16.29
2009-12-05 12:17:24 status unpacked linux-image-generic 2.6.31.16.29
2009-12-05 12:17:24 status half-configured linux-image-generic 2.6.31.16.29
2009-12-05 12:17:24 status installed linux-image-generic 2.6.31.16.29
2009-12-05 12:17:24 configure linux-generic 2.6.31.16.29 2.6.31.16.29
2009-12-05 12:17:24 status unpacked linux-generic 2.6.31.16.29
2009-12-05 12:17:24 status half-configured linux-generic 2.6.31.16.29
2009-12-05 12:17:24 status installed linux-generic 2.6.31.16.29
2009-12-05 12:17:24 configure linux-headers-2.6.31-16 2.6.31-16.52 2.6.31-16.52
2009-12-05 12:17:24 status unpacked linux-headers-2.6.31-16 2.6.31-16.52
2009-12-05 12:17:24 status half-configured linux-headers-2.6.31-16 2.6.31-16.52
2009-12-05 12:17:24 status installed linux-headers-2.6.31-16 2.6.31-16.52
2009-12-05 12:17:24 configure linux-headers-2.6.31-16-generic 2.6.31-16.52 2.6.31-16.52
2009-12-05 12:17:24 status unpacked linux-headers-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:17:24 status half-configured linux-headers-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:17:27 status installed linux-headers-2.6.31-16-generic 2.6.31-16.52
2009-12-05 12:17:27 configure linux-headers-generic 2.6.31.16.29 2.6.31.16.29
2009-12-05 12:17:27 status unpacked linux-headers-generic 2.6.31.16.29
2009-12-05 12:17:27 status half-configured linux-headers-generic 2.6.31.16.29
2009-12-05 12:17:27 status installed linux-headers-generic 2.6.31.16.29
2009-12-05 12:17:27 configure linux-libc-dev 2.6.31-16.52 2.6.31-16.52
2009-12-05 12:17:27 status unpacked linux-libc-dev 2.6.31-16.52
2009-12-05 12:17:27 status half-configured linux-libc-dev 2.6.31-16.52
2009-12-05 12:17:27 status installed linux-libc-dev 2.6.31-16.52

---

### Post by blueridgedog on 2009-12-05
> **stvdel said:**
> Thanks slakkie, can anyone see anything in here that might be a suspect? All I know is it was around this time today and my computer had a message pop up asking to restart.



What is the issue?  That would help connect it with a package.

---

