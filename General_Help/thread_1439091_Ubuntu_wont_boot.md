---
title: "Ubuntu wont boot"
date: 2010-03-25
forum: General Help
---

### Post by blacknite12 on 2010-03-25
After having a lot of trouble with vista and no chance of getting Windows 7 anytime soon, I decided to get Ubuntu and use dual booting with vista.  I had recently installed it about two days ago and for the most part it worked pretty well.  That is until I installed the driver for my video card, an ATI Radeon HD2600 pro, then things went down hill for me.  Every time I try and boot Ubuntu it now goes to a black screen after the logo comes up and i am unable to do anything.  I have tried to look up some solutions, but I am still relatively new to programing and some of this stuff seems a bit complicated for me.  I have come here asking for some type of help, is there a simple solution to this that does not require a reinstall?

---

### Post by RemiemB on 2010-03-25
what kind of message does it give you? 

could you post the output?

---

### Post by Amof on 2010-03-25
We need a little info first.

Did you uninstall your old drivers first? By that I mean did you uninstall the drivers that Ubuntu installed when it was installed? ATI? Nvidia?

---

### Post by Serpher on 2010-03-25
The drivers ATI develop for Linux are pretty **** and half assed. Is there a reason you needed these drivers?

---

### Post by waynefoutz on 2010-03-25
try booting it up in the recovery mode, which will give you a command line.

then type

aptitude remove xorg-driver-fglrx

---

### Post by blacknite12 on 2010-03-26
I got the driver update from one of the menus in Ubuntu, sorry but I don't remember the name it was hardware something.  It said that it was getting the driver from AMD, I remember the message that came with it said that it was property of AMD and could not be changed and altered by Ubuntu.  That is all I can remember right now.  

Also waynefoutz I did try the code, but it didn't work for me.

---

### Post by Garibaldi3489 on 2010-03-26
Once it boots all the way (to the black screen), hit CTRL+ALT+F2 and then it should bring up a terminal where you can login. Then run
```
$ sudo dpkg-reconfigure xserver-xorg
```

This should generate a file called /etc/X11/xorg.conf which should contain the fallback video drivers.

---

### Post by ssparti on 2010-03-26
I am running into this same problem.  After the update that we got 2-3 days ago my computer runs the bios, shows the Ubuntu Logo and then goes to a black screen.  I can't type anything, and it won't take me to any menu if I push CRL-ALT-F1 or F2 or F3.  When it boots up I have to hold SHIFT then I can boot up in recovery mode.  I currently have to run off the CD just to get my computer to work.  I'll try some of the posts to see if I can get them to work, but nothing has helped yet.  I did get one message when this first started happening, when it started to run grub I got an environmental block message, but I went through that fix and now the message doesn't show up any more but it just goes to a black screen.  I'll post the output of the suggestions here.

---

### Post by blacknite12 on 2010-03-26
Since I'm still having problems I decided to remember as much as i can before I came to the forum and document everything that has happened after, here is what I have so far.

After I installed the driver I started having trouble with the black screen, after a while I tried running safe mode.  I then did a scan to check for errors, it turned up nothing, a few times after when I started it up instead of a black screen there were a bunch of fuzzy lines of coding.  After coming to this forum I tried the aptitude remove xorg-driver-fglrx command in safe mode, after that I received the following message.

E: could not open lock file /var/lib/dpkp/lock - open e 13 :permission denied
E:unable to lock the adminastration directory (/var/lib/dpkg), are you root?

Once I tried to boot again after that, the screen did that weird fuzzy lines of color thing.  I came back to read the latest post, i then tried to use CTRL+ALT+F2 and my keyboard was not responding.  I then loaded again and noticed a cursor before the black screen, I then tried it there.  It went black for a moment but then went back to a cursor, num lock, caps lock and scroll lock would now light up on my keyboard, but nothing I did caused anything to happen on the screen.  I then went to try the sudo dpkg-reconfigure command on safe mode, it then asked me for a sudo password and I then entered my password but nothing happened.  

This is as much detail as I have for everything that has happened so far, I am sorry about not having all of the details before.  I hope that all of this information helps lead to some conclusion to what can be done.

---

### Post by Garibaldi3489 on 2010-03-29
The reason why you couldn't remove xorg-driver-fglrx was because it looks like you weren't running aptitude as root try:
```
$ **sudo** aptitude remove xorg-driver-fglrx
```

---

