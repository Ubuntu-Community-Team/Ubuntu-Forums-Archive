---
title: "System Crash"
date: 2010-01-23
forum: General Help
---

### Post by hbsq on 2010-01-23
Dear all,


today morning I switch of the power in my laptop and then switch it on again, I know such act is not good but this what happen, anyway, system didn't run, I got the following error message, 

General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try


by the way, yesterday I got a message to update the system for some important security files, it was around 900 files and took too much time for downloading, after download I went to sleep and kept my laptop running.

( I got like this problem before but at that time I just re-install Ubuntu. Now I don't won't just re-install Ubuntu, I want to learn how to fix such a problem. I am a beginner in Linux word and asking for your help. ) 

I am waiting for your help and thanks a lot in advance.

---

### Post by byStanderone on 2010-01-23
...seems a weird problem, leaving many questions to answer! one curious point is the number of files that you mentioned, that's too many for a normal update!

---

### Post by d3v1150m471c on 2010-01-23
Try doing another update. If that doesn't fix the problem google how to do a hard reset for your specific computer and follow the directions. If that doesn't fix it then recover from the live cd.

---

### Post by pepe machine on 2010-01-23
we have the same problem.. hope theres a solution for us

---

### Post by d3v1150m471c on 2010-01-23
**Hard reset. **Sounds like a hardware issue and this almost always fixes it.

---

### Post by fjf314 on 2010-01-23
Does the error message you posted come up every time you power up the system now?

A quick search turned up the following thread with the same problem:

[http://ubuntuforums.org/showthread.php?t=1333302](http://ubuntuforums.org/showthread.php?t=1333302)

The issue may be in your /boot/grub/menu.lst file.

---

### Post by hbsq on 2010-01-23
> **byStanderone said:**
> ...seems a weird problem, leaving many questions to answer! one curious point is the number of files that you mentioned, that's too many for a normal update!

I really don't know what is the problem, because of what and how to solve it :( !!!

> **d3v1150m471c said:**
> Try doing another update. If that doesn't fix the problem google how to do a hard reset for your specific computer and follow the directions. If that doesn't fix it then recover from the live cd.

how to do the update from the maintenance shell? just to write " apt-get update ?!!??

> **d3v1150m471c said:**
> **Hard reset. **Sounds like a hardware issue and this almost always fixes it.

how to do Hard Resest?? 

> **fjf314 said:**
> Does the error message you posted come up every time you power up the system now?

A quick search turned up the following thread with the same problem:

[http://ubuntuforums.org/showthread.php?t=1333302](http://ubuntuforums.org/showthread.php?t=1333302)

The issue may be in your /boot/grub/menu.lst file.

yes, that is write. I am getting this message every time try to power up my system. I will take a look of the thread you told me about and update you later.


thanks a lot for you all :)

---

### Post by hbsq on 2010-01-23
I just want to add some details to make it clear for you. when I try to power up my laptop, first I get the list of available systems or kernels, I chose the one I used to use, then I get the the welcome screen which it will come when you start your system, after that I will get the said error.

I don't know whither what I mentioned above is useful for you to understand the problem I have or no/ 

thanks once again. :)

---

