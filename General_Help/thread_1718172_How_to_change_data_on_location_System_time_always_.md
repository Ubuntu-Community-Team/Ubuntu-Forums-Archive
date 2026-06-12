---
title: "How to change data on location? System time always wrong on re-boot"
date: 2011-03-30
forum: General Help
---

### Post by DunZH on 2011-03-30
Hi I have an annoying problem, when I installed Ubuntu 9.10 I put in one time setting but it was wrong, and now I don't know where to change it.  I tried to change the time preferences, but on reboot I am back to the wrong time.  Its really annoying!  :P

I know the data is in there somewhere and I can change if I knew where it was.  

Any help pls??

---

### Post by papibe on 2011-03-31
Maybe you changed your time zone? Anyway, there's a lot of info and tricks in [this ]("https://help.ubuntu.com/community/UbuntuTime")tutorial.

Regards.

---

### Post by DunZH on 2011-03-31
Ok thanks for the help, I searched first but all the terms were too common to get a hit.

I tried out the first method, but it gave me a really weird result:

zhuang-desktop:~$ sudo dpkg-reconfigure tzdata
[After changes in the dialog]
Current default time zone: 'Asia/Chongqing'
Local time is now:      Fri Apr  1 01:01:06 CST 2011.
Universal Time is now:  Thu Mar 31 17:01:06 UTC 2011.

But that local time is wrong!  Its off by 12 hours, its 12 hours later than reality.

What the heck can cause that?

I will try some of the other methods there, maybe I can figure this out.  But that is weird.

---

### Post by DunZH on 2011-03-31
Thanks papibe, I installed the ntp and chose a close server and all is well now.

Its a big help for me, thanks a lot!!  :popcorn:

---

