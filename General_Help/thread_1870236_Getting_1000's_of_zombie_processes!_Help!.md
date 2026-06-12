---
title: "Getting 1000's of zombie processes! Help!"
date: 2011-10-26
forum: General Help
---

### Post by Zewtastic on 2011-10-26
I just tilted up this new lamp install of 11.10 64 bit server.

But all of a sudden I am getting 10K+ zombie processes. Seen as many as 32K.

It seems as though they are coming from Fuser but I dont think that is right.

I ran a ps aux | awk '{ print $8 " " $2 " " $11}' | grep -w Z to try and identify the processes.

I am a bit new to Ubuntu so am unclear what is actually causing all these zombie processes and how to diagnose and fix.

Any tips and ideas appreciated.

---

### Post by Zewtastic on 2011-10-26
Ok I restarted once, they were stil there.

Restarted a 2nd time. All zombies gone.

And 5 minutes later, 32K zombie processes back.

What is going on?

---

### Post by Mydoom666 on 2011-10-30
Yup,

I had the same issue.

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/876387](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/876387)

---

### Post by Zewtastic on 2011-10-30
I think mine was related to a lot of bad php code.

I spent a lot of time going through my apache errors.log and cleared everything I found. A lot of abusive attempts by bots to exploit code.

I have not had any zombie issues since I reduced the errors down to essentially zero.

---

