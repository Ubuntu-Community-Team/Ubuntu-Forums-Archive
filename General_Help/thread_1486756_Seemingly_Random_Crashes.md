---
title: "Seemingly Random Crashes"
date: 2010-05-18
forum: General Help
---

### Post by Jimbo8098 on 2010-05-18
I experience random crashes when i open , close or use firefox. It is really annoying because when it happens i cant do anything about it , nothing will open and the only way to fix it is by hard shutdowns. One person has suggested that I install updates but i have checked using the update manager and it appears my system is up to date.

> 
u235sentinel:

                                  **Re: Unreal Tournament 2004 on Ubuntu? Show me!**             
                                                                     Quote:
                                                                      Originally Posted by **Jimbo8098**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9316454#post9316454")                 
                 *Im using Lucid Lynx right now but  is this really on the install cd? Why didnt it install during initial  install?*
                                 
because the update come out after the cd/dvd was created.  There  were several updates actually.  The latest works great :grin:
So whaere do i find the updates this guy is talking about?

---

### Post by mörgæs on 2010-05-18
If you have installed 10.04, the upgrades to it will come automatically just like in the older versions.

---

### Post by Jimbo8098 on 2010-05-18
> **mörgæs said:**
> If you have installed 10.04, the upgrades to it will come automatically just like in the older versions.

Ye I have 10.04 but i still experience these problems and i have no idea as to why they happen. Somethimes it will be when im loading a page in firefox , others might just happen out of nowhere when im doing nothing and will make the panel disappear.

---

### Post by mörgæs on 2010-05-18
You could try a complete removal of Firefox and a reinstall:

[http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/](http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/)

---

### Post by aphatak on 2010-05-18
Does your computer freeze, or does the screen get garbled?  If it is the freeze, I think the problem might go beyond Firefox.
I had Lucid Lynx freeze on me.  What I did was install Kubuntu Desktop - Kubuntu never froze.  I don't want to assume that you need me to tell you how to install Kubuntu Desktop into your existing system.  If you do, let me know - I will post instructions.

---

### Post by Jimbo8098 on 2010-05-18
I like the gnome desktop so i might not like to go to kubuntu if it is a new type of appearance , i really like the features of the ubuntu default panel but if the kubuntu one is similar or the same then please tell me how to install it.

Im surprised the os hasnt worked right out of the box because alot of the other features of ubuntu are very well made. I like how you can download applications through the software package manager. Its just too bad the vitals havent worked properly. If i could find out what was causing the problem i might be able to investigate it myself but as i stand , with some to very little ubuntu knowledge , and having never adjusted to ubuntu's advanced console i may well find it hard to get to the bottom of these problems simpljy because like many people i was born and bread using windows os.

I dont know if it would be possible to get some people on the this problems case since it would seem to be a simple problem to fix but this person i have quoted , sentinel , seems to have a fair idea as to what the problem was and how it was fixed , but unfortunately , he has not shown me how to fix the problem yet ... :(

---

### Post by MIJ-VI on 2010-05-18
> **Jimbo8098 said:**
> _I experience random crashes when i open , close or use firefox_. It is really annoying because when it happens i cant do anything about it , nothing will open and the only way to fix it is by hard shutdowns. One person has suggested that I install updates but i have checked using the update manager and it appears my system is up to date.

So whaere do i find the updates this guy is talking about?

Are you using any add-ons with Firefox? One of them may be out-of-date or corrupted.

Have you tried (in Firefox) Tools-->Clear Recent History? There may be a corrupted cookie etc.

---

### Post by hawthornso23 on 2010-05-18
Have just fixed a similar problem which turned out to be faulty memory. Try running memtest (from grub menu) to see if faulty memory is causing your problems. 

What shows up in dmesg after such a crash?

---

### Post by aphatak on 2010-05-18
> **Jimbo8098 said:**
> I like the gnome desktop so i might not like to go to kubuntu if it is a new type of appearance , i really like the features of the ubuntu default panel but if the kubuntu one is similar or the same then please tell me how to install it.

If you use Synaptics, fire it up, search for 'kubuntu-desktop', mark it for installation and then hit 'apply'.  If you use the command line instead of Synaptics, the command is 'sudo apt-get install kubuntu-desktop'.  In either case, the Kubuntu desktop requires a number of packages to be downloaded and installed.  Once the installation is done, log out (you will be logging out of the Gnome desktop environment, not Ubuntu).  When you see the log-in screen, click your name.  You will notice a small drop down (or should I say drop-up?!?) box showing the default value 'of 'GNOME'.  Open it and select KDE in this box.  Key in your password and hit 'login'.   Try it out, and see if the screen freezes.  If you prefer Gnome to KDE, you can always select GNOME the next time you log in.

> **Jimbo8098 said:**
> Im surprised the os hasnt worked right out of the box because alot of the other features of ubuntu are very well made. I like how you can download applications through the software package manager. Its just too bad the vitals havent worked properly. If i could find out what was causing the problem i might be able to investigate it myself but as i stand , with some to very little ubuntu knowledge , and having never adjusted to ubuntu's advanced console i may well find it hard to get to the bottom of these problems simpljy because like many people i was born and bread using windows os.

I agree - I like Ubuntu (and all its flavors).

> **Jimbo8098 said:**
> I dont know if it would be possible to get some people on the this problems case since it would seem to be a simple problem to fix but this person i have quoted , sentinel , seems to have a fair idea as to what the problem was and how it was fixed , but unfortunately , he has not shown me how to fix the problem yet ... :(

I have been trying to help pin the bug down - as, I'm sure, a lot of other folks are.  This bug is elusive - it seems to occur only when a very definite set of conditions arises.  There are a number of other threads where you might find useful info, and of course if you have something useful, you could publish it.

---

### Post by Jimbo8098 on 2010-05-19
what about using chromium instead of firefox?Maybe firefox is the problem here.

Does anyone happen to know what these "optimal conditions" for this bug are?

The memory is new performance stuff. I got it a couple of months ago now. Ill look into that.

---

### Post by Catharsis on 2010-05-19
What graphics card do you have?
```
lspci | grep VGA
```

---

### Post by Jimbo8098 on 2010-05-19
I/O

```

jimbo8098@jimbo8098-desktop:~$ lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

```

---

### Post by Catharsis on 2010-05-19
Are you using the proprietary driver in System->Administration->Hardware Drivers?

If not, try it. If so, you might want to try the open-source -nouveau driver and see if it works better.

---

### Post by Jimbo8098 on 2010-07-14
I tried both and they never worked i dont think. Though i have a new graphics card now but ive not had a good chance to see if this is still the case since ive been having problems getting the right config of drivers.

I think it seems more stable but i also think that i may have foud out why this problem is occuring. I think it is due to my swap part. there was a thread talking about how to fix it but i cant link right now... Ill link when i get home :)

Thanks for everyones help so far :)

---

### Post by RJARRRPCGP on 2010-07-14
> **aphatak said:**
> Does your computer freeze, or does the screen get garbled?  

Sounds like major hardware issues. Bad caps can cause that. Sorry. :(

[http://badcaps.net](http://badcaps.net)

---

