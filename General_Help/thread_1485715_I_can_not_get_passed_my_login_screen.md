---
title: "I can not get passed my login screen"
date: 2010-05-17
forum: General Help
---

### Post by unknown23 on 2010-05-17
ok

i am using ubuntu version 9.10 karmic

i boot up my laptop, i get to the login screen

i enter my valid username and password

the screen flickers, and jumps right back to the login screen

i tried a lot since this happened last night at éam; i have not slept yet trying to fix this

if somebody can please help me

i am not a linux expert, i am a beginner, so linux lingo, is not going to help me

i can try to give you some output, but i am not on my pc; i am online on a friends computer

:confused:

---

### Post by wilee-nilee on 2010-05-17
Try the second line in the kernel, see if you can log in and that way. I forget what that line is called but it gets you to a basically recovery sort of gui. This worked for me when I got this same loop. If you get in set the computer to automatically login.

---

### Post by unknown23 on 2010-05-17
hi

many thanks for your reply

i tried your suggestion more than a few times last night

it does not work for me

so .... i just tried it again, so i get the blue scree recovery menu

*could not access PID file for nmbd

so, now what?

---

### Post by wilee-nilee on 2010-05-17
> **unknown23 said:**
> hi

many thanks for your reply

i tried your suggestion more than a few times last night

it does not work for me

so .... i just tried it again, so i get the blue scree recovery menu

*could not access PID file for nmbd

so, now what?

I would at that screen go to the root console and log in and run start x or start gdm

---

### Post by unknown23 on 2010-05-17
oh, i forgot to mention something really important

my dvd drive is completely broken

i can not do a cd reinstall

i tried from usb, and it just will not boot from usb

so; i really have to find a solution to fix this problem i am having

---

### Post by unknown23 on 2010-05-17
start x gives me

xauth: error in locking authority file /home/shadowcast/.Xauthority

---

### Post by wilee-nilee on 2010-05-17
> **unknown23 said:**
> oh, i forgot to mention something really important

my dvd drive is completely broken

i can not do a cd reinstall

i tried from usb, and it just will not boot from usb

so; i really have to find a solution to fix this problem i am having

Other then being able to load a thumb and reinstalling I am not sure whats next. There is a xfce forum you might try looking there for help.

---

### Post by unknown23 on 2010-05-17
tried both suggestions you just mentioned

nothing worked for me

xfce forum is like greek language for me, i do not understand any of what is suggested

my computer will not boot from my thumb drive at all

so, i really do not know what to do

---

### Post by wilee-nilee on 2010-05-17
So there are several types of thumb loaders, unetbootin, pendrivelinux and the startup disc creator in Ubuntu. When you say your computer can't boot from the usb is it that you can't get to the choice of booting from or that the usb just wont boot? Have you tried more then one usb loader? I would post a thread at the xfce forums if you haven't and just let them know your level of skill.

Also this thread is only 58 min old there are people on here who probably can help you just have to hang and bump. I would lokk for bumping at anytime after 9am pacific LA time.

---

### Post by unknown23 on 2010-05-17
well, i just want to thank you for your time, i will just let you know

my friend put the newest version of linux on a usb key for me

changed my boot sequence so that it should read the removveable device first

but it just goes into grub and dosent see the usb drive

i do not know what to do for this

---

### Post by wilee-nilee on 2010-05-17
> **unknown23 said:**
> well, i just want to thank you for your time, i will just let you know

my friend put the newest version of linux on a usb key for me

changed my boot sequence so that it should read the removveable device first

but it just goes into grub and dosent see the usb drive

i do not know what to do for this

On my computer if the f12 command is on in bios then hitting f12, for choices of booting then booting from the thumb may work. I have had problems on several computers with just setting the device to be booted from first in line. This is actually a good thing to get used to as it will save you from accidentally booting from something you don't want to by mistake.

---

### Post by unknown23 on 2010-05-17
xauth: error in locking authority file /home/shadowcast/.Xauthority

so? is this an indication on where i should proceed in order to fix this problem?

---

