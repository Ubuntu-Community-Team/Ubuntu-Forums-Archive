---
title: "Video card Drivers not recognized-No GUI"
date: 2010-12-26
forum: General Help
---

### Post by Cheetah1933 on 2010-12-26
I updated my video card drivers, but when I boot back up, I have no GUI and am given a terminal because it does not recognize the drivers. I have already changed "quiet splash" to "nomodeset" at the suggestion of another user. Any suggestions?

Specs:[SIZE=2]ATI Mobility Radeon 5650
[/SIZE]500GB (7200RPM) Hard Drive (SATA)
Intel Core i5-450M processor 2.40GHz with Turbo Boost Technology up to 2.66 GHz
4gb of ram
Ubuntu 10.10

Posted as a separate thread than my old one, because the other thread was originally about another issue.

---

### Post by davidmohammed on 2010-12-26
see if you have a file called xorg.conf - if you have rename it then reboot.

i.e.

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If it doesnt work please let everyone know what driver you installed (did you download it?) and how you installed it.

---

### Post by Cheetah1933 on 2010-12-26
I downloaded the drivers for the [SIZE=2]ATI Mobility Radeon 5650 through the driver manager that popped up on the menu bar. I used that to install them, and then it told me to reboot my system. I did that, and now I'm here. I'll find out the official name of the drivers in a minute, I need to boot up on my usb to do that and I'm currently copying files over from windows with it.
[/SIZE]

---

### Post by davidmohammed on 2010-12-26
ok,
  if that doesnt work - just need to confirm if you've got single or dual graphics etc.

can you run

lspci | grep VGA

what is displayed on the screen after running that command - should be something like

02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)

---

### Post by Cheetah1933 on 2010-12-26
> **davidmohammed said:**
> ok,
  if that doesnt work - just need to confirm if you've got single or dual graphics etc.

can you run

lspci | grep VGA

what is displayed on the screen after running that command - should be something like

02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)


It says
 01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 series]

---

### Post by davidmohammed on 2010-12-26
ok - did the mv /etc.... command work - possible either with nomodeset or without?


maybe you can get to a low graphics situation by using

nomodeset xforcevesa as your boot option instead of quiet splash

---

### Post by Cheetah1933 on 2010-12-26
no, it said there was no such file. I'm running 64 bit, would that make a difference? let me try the low graphics settings. This computer can also do switchable graphics, if that makes a difference either.

---

### Post by davidmohammed on 2010-12-26
file missing and 64bit is not the issue.

Did booting with nomodeset xforcevesa work?

---

### Post by davidmohammed on 2010-12-26
...

switchable graphics - is [this thread]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1629799") your issue?

---

### Post by Cheetah1933 on 2010-12-26
Edit: yeah, that was my issue. So sorry to waste your time XD but thank you so much for your help.

---

### Post by Mecasickle on 2010-12-26
got the same problem, but with my Nvidia Graphics card, I installed its driver and I get the tty1 black screen , and no desktop environment gets set up.

I looked up all the threads, but any ideas on how I can fix it?
Thanks!

---

