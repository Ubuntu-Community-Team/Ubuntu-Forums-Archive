---
title: "Stopping Automatic Crash Report Generation [FAIL]"
date: 2011-07-21
forum: General Help
---

### Post by DugMatt77 on 2011-07-21
Hey. Recently installed Ubuntu 10.04 (i think) on my laptop as a dual boot with windows. Now, whenever I start my computer, the grub menu boots and I choose to run the generic ubuntu. However, I get the message:

Stopping Automatic Crash Report Generation [FAIL]

And the screen freezes at that. No further progress is made and I have to restart my computer. The only way I can run ubuntu is by running it in safe mode with low graphics. 

Anyone got a solution to this? I have read other posts but it doesn't seem to solve my problem.

Thanks!

---

### Post by wildmanne39 on 2011-07-21
Hi, see if you can use the method in this link to get you into ubuntu so you can check your video card driver and with log file viewer look at your system,xorg and dmesg logs to see if you see an error message besides what you see at the boot screen.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by DugMatt77 on 2011-07-21
I can't access the Ubuntu screen because the computer freezes before it gets that far! 
I highly doubt it will be the graphics card.. As I have integrated graphics!
It pretty much freezes whilst analysing/doing the system check, or should I say the cursor continues to blink but goes no further. I figured if I can fix the "stopping automatic crash report generation" error, then it should run fine.

---

### Post by G9xPq9mu on 2011-07-21
[check this]("http://ubuntuforums.org/showthread.php?t=1745793")
hi, i registered to this forum coz i have probably the same problem and can't find any solution.
//i have toshiba satellite p750 10q, 64-bit natty, kernel 2.6.38-10-generic, gnome

here's what happened and what i was doing:
1. i was chilling out after i've customized my new computer, rhythmbox  was playing music. when the screensaver showed, i moved the cursor so i  could change the music. and i realized, the system frozed. i could move  the cursor, but nothing happened. music was still playing. tried to  restart x, nothing happened, so i had to use the power button to close  system. everything was okay.
2. and today same situation - but after restart screen got purple, then  black as it was normally checking things. everything was okay except one  line: stopping automatic crash report generation [fail] ([like this]("http://i.stack.imgur.com/aIXUc.jpg"))
3.rebooting didn't change anything. so i get in text mode (ctrl+alt+f2), login and:
4. [found it in web] checked if it shows sbin instead of bin at /etc/X11/default-display-manager (yup, it showed sbin)
5. tried to run gdm (sudo gdm), didn't work. restart.
5. set 1 to enabled in apport (/etc/default), saved, tried to run gdm, restarted.
6. still nothng changes so.. i removed apport
7. and now when i start the computer i don't get that [fail]. although it still stops loading after checking battery state...

so after all it's not apport that failed... nvidia drivers? i really  don't know what to do now, reinstall is said not to change that, so i  won't try.

---

### Post by wildmanne39 on 2011-07-21
> **DugMatt77 said:**
> I can't access the Ubuntu screen because the computer freezes before it gets that far! 
I highly doubt it will be the graphics card.. As I have integrated graphics!
It pretty much freezes whilst analysing/doing the system check, or should I say the cursor continues to blink but goes no further. I figured if I can fix the "stopping automatic crash report generation" error, then it should run fine.
Hi, do what is in that link I gave you and you should be able to boot. It tells you how to start the system when you can not boot all the way. I am not going to be on much today I have a family emergency.

---

### Post by DugMatt77 on 2011-07-21
Well, I followed the link can now run the generic ubuntu! No more running in that graphics failsafe mode.
Now, hopefully I dont come across any other complications.. Such as overheating..

Time to figure out how to make the windows vista the primary boot and ubuntu secondary.

Thanks a lot :D

---

