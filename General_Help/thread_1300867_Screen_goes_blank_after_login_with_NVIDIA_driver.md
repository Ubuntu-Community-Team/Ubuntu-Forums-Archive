---
title: "Screen goes blank after login with NVIDIA driver"
date: 2009-10-25
forum: General Help
---

### Post by piexing on 2009-10-25
I've installed the NVIDIA X driver and upon enabling it and restarting everything seemed fine, but when I logged in the screen went blank. ](*,) I started up again and restored the X.Org configuration file and it works like it did before enabling the NVIDIA driver. Without enabling the driver, the highest my screen resolution can go is 800x600.  Any help would be greatly appreciated.

---

### Post by macaholic on 2009-10-25
Could you post the xorg.conf file which does not seem to work?
Also, I'm assuming you installed the driver through the Hardware Drivers application, but note if you didn't.

---

### Post by ranch hand on 2009-10-25
It would help to know what release you are having this problem on and a little information on what it is installed on.

What else is on the box?

Basically something to work with.

If you are using 9.10 I would post this question to;
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

macaholic, you may see, is running 9.10 so that is good.  The thing is, there are a lot of changes to the basic system in 9.10 and that forum has the people, like macaholic, with the experience with that new system.

Many just do not have the time to be looking over here.

---

### Post by macaholic on 2009-10-25
> **ranch hand said:**
> It would help to know what release you are having this problem on and a little information on what it is installed on.

What else is on the box?

Basically something to work with.

If you are using 9.10 I would post this question to;
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

macaholic, you may see, is running 9.10 so that is good.  The thing is, there are a lot of changes to the basic system in 9.10 and that forum has the people, like macaholic, with the experience with that new system.

Many just do not have the time to be looking over here.

Excellent points, espcially about posting in the proper forum. While you will often be pointed in the right direction if you're in the wrong spot, it's obviously best to post in the right spot the first time.

As far as providing information goes, it is always advisable to post some basic system information, such as but not limited to: the numeric version of Ubuntu you're running, the desktop environment (GNOME,KDE, XFCE etc), what you've tried doing in resolving the problem thus far (installing drivers, commands you've run, etc.) Never be hesitant about posting information about your system that you think may not be relevant, the more information that's provided, the better grasp of the situation the person or people who are helping you will   This basic information is especially when dealing with hardware or driver issues, as those issues generally involve multiple variables which affect the potential solution.

I didn't mean to detract from the OP, but I thought I'd just give my two cents on forum posting :) .

---

### Post by joy23 on 2010-01-01
Even i have the same problem
After installing nvidia 9500 latest drivers on karmic
1st there was some root issue 
then there was some x-server issue
after sorting out all that and 2 harrowing days later i succeded then this my pc would never reach the login screen
on boot menu i select ubuntu and that's it the screen goes blank.
i have to manually turn it off.
i am a newbie so i really need help
it becomes far more frustrating if people around you haven't even seen linux but only the well old windows.
i also don't the commands and their execution in linux (i am trying to learn them)
it would be really helpful if any one could help me in this case

---

### Post by joy23 on 2010-01-02
Also I can't Access any nything even troubleshooting is becoming horrible!

Can nyone help :confused:

---

### Post by Groundswell on 2010-01-02
joy, recover your xorg like piexing did, via recovery mode from grub. it's one of the options that will be available. if that works, get on over to where ranch hand suggested. If you are unable to temporarily fix your system using that recovery mode, it's difficult to help you and a reinstall may be the easiest option, other wise you'll be in terminal mounting a usb disk manually and transferring  config files to it just to share them on the forum, and if you aren't familiar with terminal and the file system, if could just be a huge headache for you.

---

