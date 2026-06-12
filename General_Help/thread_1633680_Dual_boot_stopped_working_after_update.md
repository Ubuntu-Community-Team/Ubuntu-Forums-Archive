---
title: "Dual boot stopped working after update"
date: 2010-11-29
forum: General Help
---

### Post by colmeweb on 2010-11-29
Hi I have been running 10.04 in dual boot with Vista on a Toshiba Satellite A215 for the last 4 or 5 months. Last night I did a standard update and when I turned my computer on this morning I was given the standard prompt for Vista or Ubuntu. Every time I select Ubuntu the computer just restarts and gives me the same prompt.

I have been looking over the forums, but most of the fixes seem to be done in Ubuntu, which I can't get into. I am fairly sure that it is an issue with GRUB. Does anybody know how to fix this problem from windows?

---

### Post by rummy77 on 2010-11-29
I don't know how you would fix it from windows, but I had a little bit of experience with a dual-boot Lucid/Vista and once had a similar problem.  I tried selecting all of the other options on GRUB (recovery modes), but when that didn't work I used a flash drive with a 10.04 image on it to get into a RAM-based Lucid.  Because windows won't open your linux storage drive, you'll need to somehow get into linux and then be able to mount your hard drive; the flash drive option should at least allow you to do that.

---

### Post by Rubi1200 on 2010-11-29
Hi and welcome to the forums colmeweb :)

Is this a Wubi install?

---

### Post by colmeweb on 2010-11-29
Not 100% on what wubi is (sorry) but I installed off of a cd iso. 

@rummy77
    I am going to dig up a flash drive and try to adjust the settings that way. Thanks.

---

### Post by rummy77 on 2010-11-29
wubi is the ubuntu environment that can be installed from windows as a .exe file.  It's a good way to try out ubuntu, but isn't really made to be permanent.  

Any boot-CD or flash drive image should work.  Try using the CD that you installed with, as that one definitely works with your machine without problems.

---

### Post by JDailey on 2010-11-30
I have the same problem.  Vista/Ubuntu 10.10 and when choosing Ubuntu nothing happens but a restart.  watching the screen carefully it is saying that something is not found.  Mine is a WUBI install.  Any ideas?

---

### Post by colmeweb on 2010-11-30
I actually gave away the CD I used to install the first time, trying to spread the love :) but I got it to work with a USB. Unfortunately my problem is persistent. 

On the chance that this might help somebody that knows how to fix my problem the following thread seems to be talking about the same problem as me 

[http://ubuntuforums.org/showthread.php?t=1629755](http://ubuntuforums.org/showthread.php?t=1629755)


Thanks again to anybody that offers advice to others.

---

### Post by xCasualty on 2010-11-30
If you updated Vista, load it and do a recovery to the date before the most previous update.

---

### Post by mr.farenheit on 2010-11-30
what about using ext2explore for viewing the linux partition. hopefully it also allows you to write on the linux partition as well.

---

### Post by Rubi1200 on 2010-11-30
For Wubi installs ONLY; there is a problem at the moment with GRUB updates breaking Wubi installs.

Forum member bcbc has worked tirelessly to come up with fixes for this:
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

---

### Post by rummy77 on 2010-11-30
I think the easiest thing when you have a Wubi install is not to run the update manager.  Wubi is a good way to try ubuntu, but it's really not a permanent install.  I've installed Wubi on some work computers so I don't have to use windows, and everytime the update manager ran, Wubi had problems.

---

### Post by Rubi1200 on 2010-11-30
There is also another possibility:
lock the GRUB packages in Synaptic.

See here for more details:
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

---

### Post by colmeweb on 2010-12-01
Problem solved. Thanks to Rubi 1200 for showing me the answer, and big thanks to bcbc for posting it. 

If anybody ells is have the same problem go here for the answer.

[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

---

### Post by Rubi1200 on 2010-12-01
You are more than welcome colmeweb :)

And, of course, kudos to bcbc for the hard work put in to help Wubi users.

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

### Post by colmeweb on 2010-12-02
Thanks again, I was wondering how to do that. :)

---

