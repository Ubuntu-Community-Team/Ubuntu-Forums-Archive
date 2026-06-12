---
title: "Local time problem"
date: 2010-05-25
forum: General Help
---

### Post by CrazySat on 2010-05-25
Hi all,

I have recently installed ubuntu 10.04 LTS and I have apparently a local time problem.
I live in GMT+1 Time zone (at moment with DST it is GMT+2)


I run this command to select correct data :

~$ sudo dpkg-reconfigure tzdata

Current default time zone: 'Europe/Rome'
Local time is now:      Tue May 25 06:59:22 CEST 2010.
Universal Time is now:  Tue May 25 04:59:22 UTC 2010.

and my BIOS time has been set to Universal Time so that whenever I reboot and I use Win XP, I have a wrong time 04:59:22 in place of 06:59:22.

How can I please solve this problem and such mismatch between ubuntu and windows time ?
All was fine with ubuntu 8.04 LTS which I have been using till few days ago.

The only idea I had is to set windows time zone to GMT+3 in place of GMT+1 ...

Any help and any idea are appreciated.
Thank you.

---

### Post by CrazySat on 2010-05-25
I found the solution here
[http://ubuntuforums.org/showpost.php?p=889138&postcount=4](http://ubuntuforums.org/showpost.php?p=889138&postcount=4)

Problem is [SOLVED]

---

