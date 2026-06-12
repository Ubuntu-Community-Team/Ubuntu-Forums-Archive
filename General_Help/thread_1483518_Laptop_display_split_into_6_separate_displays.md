---
title: "Laptop display split into 6 separate displays"
date: 2010-05-14
forum: General Help
---

### Post by Kochamok on 2010-05-14
I am running ubuntu 9.10, on a Lenovo laptop.
Has been working perfectly until now. But now my screen is split into 6 very small screens which all work in synch. That is - I have 6 mouse pointers - it is really like having 6 very small screens.
All software is still working. 
However - I need to go back to only one screen in full-size.
Has anyone ever experienced this.
Using Nvidia accelerated graphics driver.

---

### Post by tgalati4 on 2010-05-14
Open a terminal if you can:

metacity --replace

Perhaps you have some Compiz window switcher enabled?  Try turning it off.

Once you have that figured out:

compiz --replace

---

### Post by Kochamok on 2010-05-14
Thanks for the tip - but it didn't do the trick.
I suspect the problem originates from a software update. Not 100% certain as I have been on vacation for some time.
But the computer worked perfectly alright when I turned it off the last time. 
And when turning on again after some days - this problem appears.
Can't remember for sure, but I may have added some updates before leaving for vacation.
Is ther any way of backing out updates again ?

---

### Post by 2hot6ft2 on 2010-05-14
[http://ubuntuforums.org/showthread.php?t=1468568](http://ubuntuforums.org/showthread.php?t=1468568)
> **wojox said:**
> You need to edit /etc/X11/xorg.conf and add this under Section "Device"

Option "ModeValidation" "NoTotalSizeCheck"
To edit the file use
```
gksu gedit /etc/X11/xorg.conf
```
in a terminal
Applications > Accessories > Terminal
:popcorn:

---

### Post by Kochamok on 2010-09-28
Thanks to everybody providing hints, tips and ideas on how to solve this problem.
I tried it all - and a lot more - but with no success. Eventually I ended up re-installing Windows7 which was originally supplied with the laptop. I needed to find out if the problem was related to Ubuntu or not.
Installing windows actually made the laptop work fine - almost. Windows was running fine, but I didn't get the initial boot-up screen with the black-and-white Lenovo logo and the Bios options.
If I connected an external monitor - I did get the boot-up screen.
This made me certain that my problem was hardware related, so I reported it to the vendor. They confirmed this and replaced the LCD on my laptop.
So - now my laptop is working again - and I am back running Ubuntu - really nice.
This took me quite a while to figure out, but this is just to let you all know that this type of problem can be hardware related and is not necessarily related to the xorg-configuration, even though this provides many options and many pitfalls.

---

### Post by Atcold on 2012-08-26
> **2hot6ft2 said:**
> [http://ubuntuforums.org/showthread.php?t=1468568](http://ubuntuforums.org/showthread.php?t=1468568)

To edit the file use
```
gksu gedit /etc/X11/xorg.conf
```
in a terminal
Applications > Accessories > Terminal
:popcorn:
I love you man!
Actually, my laptop was shutting down just after the (6-screens) login. Therefore, for making the trick, I had to switch to Ctrl+Alf+F1, and from there I managed to do the job.
Many thanks indeed, really!

---

