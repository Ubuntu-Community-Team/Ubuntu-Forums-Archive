---
title: "did upgrades froze ubuntu?"
date: 2010-11-06
forum: General Help
---

### Post by Fardin on 2010-11-06
I installed ubuntu less than 2 weeks ago.
yesterday it gave me a message for installing available 147 upgrades!
I clicked ok
today after playing 10 minutes of a game on ubuntu it froze
I have tried to reboot many times, it goes to login page and freezes
I tried booting ubuntu recovery, after writing whole bunch of stuff, it stops and no where to go
I tried the memory test, it was 100% ok
why is it frozen? 
should I reinstall it by live cd?
should I ever let it to install upgrades or updates ?

---

### Post by Fardin on 2010-11-06
I installed ubuntu less than 2 weeks ago.
yesterday it gave me a message for installing available 147 upgrades!
I clicked ok
today after playing 10 minutes of a game on ubuntu it froze
I have tried to reboot many times, it goes to login page and freezes
I tried booting ubuntu recovery, after writing whole bunch of stuff, it stops and no where to go
I tried the memory test, it was 100% ok
why is it frozen? 
should I reinstall it by live cd?
should I ever let it to install upgrades or updates ?

---

### Post by cgroza on 2010-11-06
Something went wrong during upgrade. I guess reinstall is the quickest way to go. You say its freezing very soon after boot. I do not know how you can fix it like that.

---

### Post by Fardin on 2010-11-06
> **cgroza said:**
> Something went wrong during upgrade. I guess reinstall is the quickest way to go. You say its freezing very soon after boot. I do not know how you can fix it like that.
now when I reboot it does not count down to automatically start 
it waits till i choose (ubuntu , ubuntu recovery, memory test, widows, etc) and the top of screen shows: gnu grub version 1.98+20100804-5ubuntu3

when i choose ubuntu it freezes

anyhow if i reinstall it again, is it safe to install upgrades when it automatically ask you that upgrades are available?

---

### Post by Rubi1200 on 2010-11-06
If you are able to boot into Ubuntu, run the following commands (separately) and post the results back here please:

```
lspci | grep VGA
```

```
sudo dpkg --configure -a
```

Thanks.

---

### Post by cariboo on 2010-11-06
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Fardin on 2010-11-06
> **Rubi1200 said:**
> If you are able to boot into Ubuntu, run the following commands (separately) and post the results back here please:

```
lspci | grep VGA
``````
sudo dpkg --configure -a
```Thanks.
I can't type, none of the keys on key board work:

at the login screen it freezes, I tried all the keys on laptop none worked, the mouse pad also does not work.
Then I noticed every time i reboot, the clock shows the correct time so it's alive!
then I connected a mouse to my laptop now i can use the mouse and click in to log in
however can not type only the attached mouse seem to be working
the game that crashed the system is the only game that does not start other games seem to be fine
No keys on keyboard work, attached mouse works 
ubuntu seem to be ok but can not type or use any keys what should i do?
thanks

---

### Post by Fardin on 2010-11-06
in addition to information i wrote above,
when i login to ubuntu, on the top-right corner, there is a (red icon), when i place the mouse on it, it reads:
"
An error occured, place run package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: 'Error:BrokenCount>0' This usually means that your installed packages have unmet dependencies"

however when i try to follow the above it asks me for password and none of the keys on keyboard works!

---

### Post by Fardin on 2010-11-06
ok, I connected an external keyboard to laptop and was able to enter password.
then ubuntu started completing package installation, however after few minuted it gave me a package operation failed message the detail is lengthy
should I just reinstall the whole thing or should i wait?

---

### Post by Fardin on 2010-11-06
After trying for hours, i used gparted to delete the sda7 and 8 that linux was on.
Now after reboot all i get is:
grub failed

help.

 can not even go to windows anymore.  laptop seem to be infested.

are those automatic 147 updates virus free?

I'll never install any updates again

someone please help

---

### Post by Rubi1200 on 2010-11-07
Hi,
if you have a LiveCD/USB boot the computer with it and choose to try Ubuntu in live mode.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results back here.

I find it hard to believe that the updates could have caused so many problems, but post the results and we will take things from there.

Thanks.

---

### Post by Fardin on 2010-11-08
Thanks for reply

I spent all Sat and got very frustrated.
Finally I loaded my windows os and reinstalled the windows.
After reinstallations everything looked fine
so decided to reinstall ubuntu
ubuntu started the installation, however in the middle of installation it gave me an error message saying could not complete the installation
(my fault not taking notes of the exact error message)
any way when i rebooted on my surprise ubuntu seemed to be installed.
But the error message had caused me to decide to remove ubuntu and reinstall it so i used gparted to remove, after removal I could not go into windows again I was getting a message:
error: file system not found
grub rescue>
then used live cd again and noticed that gparted could not find any partition any longer
rebooted went to BIOS the hard drive had disapeard.
At the moment I'm trying to nuke the hard drive
sorry if i did not take exact notes of error messages so on
it's been a very frustrating process

At the very beginning of all these issues, when updates started to install, soon it looked like there was nothing going on that's when I started to play a game and crash happened 
I don't know if the updates were silents or not?

---

### Post by Rubi1200 on 2010-11-08
Fardin,
I am sorry to hear that you are having these difficulties.

However, there is no need to take drastic actions like > trying to nuke the hard drive

If Windows was working fine, then all you need to do is restore its bootloader.

This link explains how to do this:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Removing Ubuntu left remnants of its bootloader in the MBR, which is why you got the GRUB errors you saw. Restoring the Windows bootloader will resolve that problem.

I am still not convinced that the updates caused the level of damage you described and experienced.

But, computers and operating systems are quirky creatures sometimes, so who knows?

I suggest you get Windows up and running again and then post a screenshot of your setup from GParted so we can see how the drive is partitioned.

Then, we can hopefully guide you through getting Ubuntu going again without these problems.

---

### Post by Fardin on 2010-11-10
I had to nuke my hard drive because the hard drive was not being detected in BIOS or anywhere else (the gparted in live cd could not see any partition saying no devices, my windows OS could not find any hard drive)

Anyway, I tried to nuke and at the end of nuking session, I got messeges:
RDMDD010E, can not write sector at LBA 0x0000000....; error code is ca.

I tried and installed windows OS on the laptop.
It works fine.
Apparently there are some sectors defected on my hard drive, and when ubuntu tried to install updates, it probably ran into those defected sectors and the chaos started.

Now that I have nuked the hard drive and repartitioned and reformatted, I'm going to let the laptop work on windows only for a while, if things don't go wrong I may try ubuntu again.

My conclusion is that the problem was caused because of my hard drive defected sectors.  I think ubuntu is a wonderful program, if my hard drive was perfect I would install it again right away.
Thanks for following up.:popcorn:

---

### Post by Rubi1200 on 2010-11-10
You are more than welcome :)

I suggest you start some benchmarking now to test the integrity of the drive and whether or not you need to consider replacing it.

It is likely that you have only resolved the problem temporarily.

Keep backups of all data.

If you do decide to try and reinstall Ubuntu, post here and we will try and help as best we can to get you up and running with it.

Good luck whatever you decide.

---

