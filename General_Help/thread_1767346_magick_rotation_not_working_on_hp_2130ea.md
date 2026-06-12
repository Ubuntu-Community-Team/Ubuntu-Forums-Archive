---
title: "magick rotation not working on hp 2130ea"
date: 2011-05-25
forum: General Help
---

### Post by Ger5 on 2011-05-25
hi folks fairly new to this i have joint the forums a while ago but just spent most of the time reading up on all this stuff and i have solved a lot of the problems i had by doing this however  

I have up graded to natty 11.04 and am trying to get magick rotation 1.4 working on my hp tx2000 model 2130ea.Iam new to this Ihave spent a lot of time reading the forums and trying stuff including breaking natty a few times and had ton do a reinstall.Anyway im not to sure what i am doing wrong missing a script or something I have tryed a few different ways to try and rotate screen at the moment i have magick rotation installed and the only thing i can do with it is turn on/off touch and if i move the courser over the green arrow icon a drop down box appears saying its loading.i did turn on the bug report and this is what it says i attached the log 

thanks

---

### Post by Favux on 2011-05-25
Hi Ger5,

Are you saying it doesn't rotate the screen at all or just to inverted?  They broke the Nvidia proprietary driver for cw and ccw rotation in Natty's Xserver.  So if it is portrait orientation you can't get and you installed the proprietary driver through Hardware Drivers that is why.  They have a fix and it is already in Natty proposed.  I installed it a couple of days ago and it works.  So it should be coming through the regular updates soon.

PS:  Your log didn't attach, but we might not need it.

---

### Post by Ger5 on 2011-05-25
thanks for the quick reply

yea it does not rotate at all . im still not sure if i have to put a script in somewhere  to tell xorg i have tablet pc foe magick 1.4.iv also tryed using auto magick rotation the only thing that works for me there is cellwriter appears when i rotate thats it screen still does not rotate whit this method either

thanks for your hely

---

### Post by Favux on 2011-05-25
It sounds like you see the green rotating arrow tray icon, so it installed.

Check in the magick-rotation folder and see if there is an executable binary called checkmagick64 (or 32 if you are using 32-bit).

What video driver do you have installed?

Does:
```
xrandr -o inverted
```
in a terminal rotate the screen orientation?  To go back to normal laptop orientation:
```
xrandr -o normal
```

---

### Post by Ger5 on 2011-05-25
Yes i see the green icon tray and i do have checkmagick 32 in the folder. video driver i have is nvidia .after entering the code this is what came up

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

This is what came up in the magick log file

2011-05-25 00:39:58: cur_state: 1 
2011-05-25 00:40:57: checking for rotation
2011-05-25 00:40:57: /home/ger/magick-rotation/checkmagick32
2011-05-25 00:59:52: cur_state: 1 
2011-05-25 01:01:01: checking for rotation
2011-05-25 01:01:01: /home/ger/magick-rotation/checkmagick32
2011-05-25 01:33:27: cur_state: 1 
2011-05-25 18:54:11: checking for rotation
2011-05-25 18:54:11: /home/ger/magick-rotation/checkmagick32

---

### Post by Favux on 2011-05-25
I'm guessing the proprietary Nvidia driver because that is the same error I'd see.  Except I could rotate inverted, just not clockwise or counterclockwise.

You would have had to install the proprietary driver.  The default is the Xorg nouveua driver for Nvidia.  If you have NVIDIA X Server Settings installed then you have the proprietary driver.  You can also tell by checking to see if you have an xorg.conf in /etc/X11.  The Nvidia proprietary driver creates an xorg.conf.

So the problem is the 1.10 Xserver in Natty and the fix should be coming within a few days unless you grab it from Natty proposed.  You should probably wait for it to come through the regular update.

Then you'll have to fix the bug in xf86-input-wacom.  There is a FAQ on the Magick Rotation site (first one in the list) on how to update xf86-input-wacom.  It's easy, so no problem.

The log is saying no rotation occured so Magick didn't do anything.

---

### Post by Ger5 on 2011-05-25
A nice one thanks very much

Yes every thing you said is exactly what i have on my tablet pc here Nvidia x/xorg etc. I just thought i was missing something when i was going through the process thks man ill hang on for the update although it is good fun messing around with this stuff you learn a lot.


Just to let you know i went back messing about with things and went back over everthing i done and managed to get things working with magick rotation. first i updated  xf86-input-wacom like you said  then done a bit more reading and searching. although magick installed and half of it was working i noticed the 62 magickrules were not in /etc/udev/rules.d. so i copyed them in there and done a reboot and everything worked rotation and all devices done a quick mess about with xournal no problems.ill play about a bit more tomorrow bit late now

---

### Post by Favux on 2011-05-25
Good job!

---

