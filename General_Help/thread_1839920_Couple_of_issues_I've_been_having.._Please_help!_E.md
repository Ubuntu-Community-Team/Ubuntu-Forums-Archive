---
title: "Couple of issues I've been having.. Please help! Extreme novice."
date: 2011-09-06
forum: General Help
---

### Post by CJJones829 on 2011-09-06
Hi!

You all have been very helpful.  Please bare with me, as I'm an extreme novice!

I just bought a brand new laptop yesterday and installed Ubuntu the same day, because of all of the great stuff I've heard.  I'm still learning how to operate everything.

A few issues I've been having that I hope you guys might be able to guide me on:

1. Everything seems to freeze up 1-2 times a day, which forces me to reboot.  I'm scared this will mess me up when I start my classes and leaves my vulnerable to losing any work that I'm doing.  Seems to happen the most when my wireless internet is connecting and a browser/window is open.  It's happened a few other times randomly as well.  Is there something I can do to fix this?  Keep in mind, I don't have the biggest/best laptop out there.. it was a pretty cheap Toshiba Satellite.  So I was wondering, is there something I can do to maximize performance?

and..

2.  The cursor seems "off" sometimes.  When I go to certain websites, or sometimes when I click into folders, I'll have to click ABOVE the intended target to do what I want.  For example, clicking an inch above a hyperlink instead of the hyperlink itself.  Hopefully this makes sense.  Seems to happen randomly.

Thanks again for all of your help.  Again, I'm pretty new.. so bare with me!

I'm going back to work from my break and will jump back on here.  I just had to go ahead and get this out there, otherwise I'd never get around to it!

Thanks!!! :)

CJ

---

### Post by Beacon11 on 2011-09-06
Hey there CJ. I'm not sure what's going on off the top of my head, so let's try to work through it. First of all, did you install Ubuntu as a dual-boot from Windows, with Wubi, or with a clean wipe (replacing Windows)? Also, does the mouse issue occur only in your web browser (which I assume is Firefox)? Or does it also happen on, say, the Desktop, or in Nautilus, etc.?

---

### Post by mexicanseaf00d on 2011-09-06
I've got no solution, but: the mousecursor problem you described happened to me when I tried to connect an external monitor (via HDMI and also VGA). It seemed to me that it was somehow related to graphics resolution, because xrandr changed the Laptop res too. Unfortunately, I did not research that problem further then.

---

### Post by CJJones829 on 2011-09-06
> **Beacon11 said:**
> Hey there CJ. I'm not sure what's going on off the top of my head, so let's try to work through it. First of all, did you install Ubuntu as a dual-boot from Windows, with Wubi, or with a clean wipe (replacing Windows)? Also, does the mouse issue occur only in your web browser (which I assume is Firefox)? Or does it also happen on, say, the Desktop, or in Nautilus, etc.?

Thanks.  I did a clean wipe (replacing Windows) using a burned CD (after downloading Ubuntu onto it).  

Based on what I've seen so far.. it seems to only happen really in the browser.  I use Chromium.

Thanks for helping me with this!

---

### Post by CJJones829 on 2011-09-06
> **mexicanseaf00d said:**
> I've got no solution, but: the mousecursor problem you described happened to me when I tried to connect an external monitor (via HDMI and also VGA). It seemed to me that it was somehow related to graphics resolution, because xrandr changed the Laptop res too. Unfortunately, I did not research that problem further then.

Yeah, I'm not doing any of that stuff!

---

### Post by CJJones829 on 2011-09-06
Anybody able to help me with this?  :)

---

### Post by Beacon11 on 2011-09-07
> **CJJones829 said:**
> Anybody able to help me with this?  :)

Haha, patience-- you were posting while I was in bed. Could you do me a favor and try Firefox? Does it behave better? The mouse thing may be a Chrome bug, and not have anything to do with Ubuntu.

As for the freezing bug, first of all what graphics card do you have and what driver are you using? There are a couple things I'd like you to try so we can determine what kind of freeze is happening. Next time it happens, WHILE FROZEN answer these questions and report back after you reboot:

1. Can the cursor still move (just not click on anything)?

2. Is the clock updating (e.g. wait for 60 seconds and see if the minute updates)?

3. Does the caps lock key light update correctly when clicked?

4. Can you SSH into the machine? If so, ssh into the machine and run the following commands:

```
dmesg > ~/dmesg.txt
cat /var/log/Xorg.0.log > ~/xorg.txt
```

When you reboot, paste those files in here.

---

### Post by Helios747 on 2011-09-07
What is the model/manufacturer of the laptop?

---

### Post by Beacon11 on 2011-09-07
> **Helios747 said:**
> What is the model/manufacturer of the laptop?

Part of your question was answered in the original post:
> **CJJones829 said:**
> ... a pretty cheap Toshiba Satellite.

However, a model number could prove handy.

---

### Post by Helios747 on 2011-09-07
Derp. Apparently I can't read!


But yes, a model number would help. Some laptops have odd quirks.

---

### Post by Blasphemist on 2011-09-07
I suspect this is a video related problem. My satellite has the integrated Intel video but that doesn't mean yours does. What gpu does yours use? If you don't know for sure this will tell you.
```
lspci | grep VGA
```

---

### Post by CJJones829 on 2011-09-07
[**[SIZE=2][COLOR=#1a75cf]Toshiba Black 15.6" Satellite C655D-S5200 Laptop PC with AMD Dual-Core C-50 Processor and Windows 7 Home Premium [/COLOR][/SIZE]**]("http://www.walmart.com/catalog/product.do?product_id=16652445")
 
[http://www.walmart.com/catalog/product.do?product_id=16652445](http://www.walmart.com/catalog/product.do?product_id=16652445)

---

### Post by CJJones829 on 2011-09-07
> **Blasphemist said:**
> I suspect this is a video related problem. My satellite has the integrated Intel video but that doesn't mean yours does. What gpu does yours use? If you don't know for sure this will tell you.
```
lspci | grep VGA
```
 
I'm at work right now.. I can tell you later today.  Does the model # and all that stuff that I posted above help?  :)

---

### Post by CJJones829 on 2011-09-07
> **Beacon11 said:**
> Haha, patience-- you were posting while I was in bed. Could you do me a favor and try Firefox? Does it behave better? The mouse thing may be a Chrome bug, and not have anything to do with Ubuntu.
 
As for the freezing bug, first of all what graphics card do you have and what driver are you using? There are a couple things I'd like you to try so we can determine what kind of freeze is happening. Next time it happens, WHILE FROZEN answer these questions and report back after you reboot:
 
1. Can the cursor still move (just not click on anything)?
 
2. Is the clock updating (e.g. wait for 60 seconds and see if the minute updates)?
 
3. Does the caps lock key light update correctly when clicked?
 
4. Can you SSH into the machine? If so, ssh into the machine and run the following commands:
 
```
dmesg > ~/dmesg.txt
cat /var/log/Xorg.0.log > ~/xorg.txt
```
 
When you reboot, paste those files in here.
 
1.  Yes.  You just have to position it ABOVE the link or item you're trying to click.  I haven't really had THAT many issues with this lately.  But I did find it pretty weird.  Is Firefox the better browser for Ubuntu?  I deleleted it and went with Chromium because of the great experience I had with Google Chrome on Windows.
 
2.  Not sure what you mean on the clock thing.  Can you elaborate?
 
3.  Yes, cap locks key is fine.
 
4.  Sorry.. I have no idea what SSH'ing into the machine means!  
 
I feel so worthless, haha.  Sorry I'm not good on all of the lingo yet, but I'm trying to learn!
 
To give you an idea of what I was dealing with on my break today at lunch..
 
While typing this message ON the laptop (I'm now typing this on a PC at work), the computer froze for a few seconds randomly and then "ttttttttttttttttttttttttttt" etc. started scrolling in this message box.  I hit backspace and it stopped, and then I had to delete all of the t's.  A few minutes later, everything froze again and I had to restart.  That's the kind of stuff that's bothering me!  Especially since I plan on using this laptop as a tool for when I start school again in January.  It'd kill me to have the thing freeze and have to restart in the middle of typing a paper or something!
 
Another thing that seems to hamper me is inconsistent internet speed.  One minute it'll be great, the next everything is extremely sluggish.
 
I'm getting pretty cynical about everything because maybe I got in-over-my-head in doing this, but I really do want to learn and figure everything out.  I refuse to go back to Windows 7 so easily without fighting to learn and modify everything with Ubuntu to work properly!
 
Please be patient with me!  But I'm pretty optimistic considering all the help that is being offered here!
 
Thanks again!

---

### Post by Beacon11 on 2011-09-07
> **CJJones829 said:**
> I feel so worthless, haha.  Sorry I'm not good on all of the lingo yet, but I'm trying to learn!

I'm sorry CJ I just started thinking of things and listing them out-- don't feel worthless, you can't just suddenly know everything ;) . I just wasn't thinking while I was typing. Let me elaborate.

No, I would not say that Firefox is better than Chrome-- I actually use Chrome myself. I'm simply trying to help you determine where your mouse problem lies. Try installing Firefox again, and see if the mouse behaves as it should in Firefox even though it's busted in Chrome. If so, it implies that there's an issue with Chrome rather than Ubuntu. This is for the weird-mouse-offset problem only.

Those four steps I gave were for troubleshooting your freezing problem only (not your mouse). Write down or print out those steps and follow them the next time your computer freezes. Let me explain what each step will tell us.

1. Can the cursor still move (just not click on anything)?
This step will help determine at which level the problem lies. If your mouse can still move, it implies that your computer is not "hard frozen" if you will. This means X (the only reason you have a GUI instead of just a terminal) is having issues.

2. Is the clock updating (e.g. wait for 60 seconds and see if the minute updates)?
This will help determine if you're having a problem with keyboard and mouse input. Get a watch or a timer and wait for one minute while watching the Ubuntu clock. Does the minute on the clock update? If you can't move your mouse or type anything but the minute on the clock updates, it implies that X is fine (the screen is repainting) but you're having an input issue.

3. Does the caps lock key light update correctly when clicked?
Similar to (1).

4. Can you SSH into the machine?
SSH stands for "Secure Shell." It is a way of remotely accessing another machine. It is used very often for remote administration of headless (monitorless and keyboardless) servers, and it's also very useful for troubleshooting a machine that isn't responding to local input. However, it does require a second machine. Do you have one? It doesn't necessarily need Linux, but if it's running Windows you'll need to install something like PuTTY: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) . You'll also need to install the SSH server on your Linux laptop:

```
sudo apt-get install openssh-server
```

The login credentials are the ones you use to login to the machine. I can give more specific instructions once I know whether the second computer is Windows or Linux, but if you CAN SSH into your laptop while it's frozen, run those two commands I gave you in the terminal (more explanation below).


Again, the above four steps are meant to be taken while the laptop is FROZEN.

Now, it sounds like not all of your freezes are fatal (i.e. requiring a reboot). Next time you encounter one that is NOT fatal, when it recovers run the following commands in a terminal:

```
dmesg > ~/dmesg.txt
cat /var/log/Xorg.0.log > ~/xorg.txt
```

That will create two files in your home directory-- dmesg.txt and xorg.txt. Open those two files up and paste both of them in here, please.

I know this is frustrating, but don't lose hope yet!

---

### Post by dodo3773 on 2011-09-07
Try to avoid hard powering off your machine (if that is what your doing). Use magic sysrq keys

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

Also, are you sure that the cursor freezing and the system freezing are two different problems? Personally I have found that when I experienced problems similar to this they have almost always been related to either compositing (compiz, etc.. ) or very cpu intensive applications.

---

### Post by Beacon11 on 2011-09-07
> **dodo3773 said:**
> Also, are you sure that the cursor freezing and the system freezing are two different problems?

That's part of what we're in the process of finding out.

---

### Post by Blasphemist on 2011-09-07
You have the AMD Radeon HD 6250 gpu. This is pretty new and use kernel mode setting. Start with this.
> Add radeon.modeset=1 to your BootOptions to enable KMS (and DRI2) with the ati/radeon driver.

For Grub2 on Ubuntu 9.10 and later:

```
sudo nano /etc/default/grub.
```

Add radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT=.

Then sudo update-grub

Then reboot and make sure kms is now loaded.
> ```
dmesg | grep drm
```
This should indicate that the drm got initialized and set up, with maybe mention of the framebuffer and modes set. E.g.:


[    2.699321] [drm] Initialized drm 1.1.0 20060810
[    2.819877] [drm] set up 7M of stolen space
[    3.334947] [drm] TV-14: set mode NTSC 480i 0
[    3.493351] fb0: inteldrmfb frame buffer device
[    3.513539] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.627621] [drm] LVDS-8: set mode 1280x800 1d
[    4.227945] [drm] TV-14: set mode NTSC 480i 0

Then let us know if the issue is solved. Thanks.

---

### Post by CJJones829 on 2011-09-07
> **Blasphemist said:**
> You have the AMD Radeon HD 6250 gpu. This is pretty new and use kernel mode setting. Start with this.


Then reboot and make sure kms is now loaded.

Then let us know if the issue is solved. Thanks.

OK.. I'm already stuck in the beginning!  Give me a hand.. haha.

I typed this into the terminal, as you said:

```
sudo nano /etc/default/grub.
```

But, I'm confused by the next step:

> Add radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT=.

Then sudo update-grub

I don't get what you're saying.. Do I type in that radeon part AFTER something?  Because it's just pulling up a new menu called:

>     File: /etc/default/grub.  

It says that at the top.  But the actual area where you can type is completely blank.

So.. what exactly am I typing in?

Sorry.  :confused:

---

### Post by CJJones829 on 2011-09-07
> **dodo3773 said:**
> Try to avoid hard powering off your machine (if that is what your doing). Use magic sysrq keys

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

Also, are you sure that the cursor freezing and the system freezing are two different problems? Personally I have found that when I experienced problems similar to this they have almost always been related to either compositing (compiz, etc.. ) or very cpu intensive applications.

Cool resource.  Thanks!

I'll definitely have to print that out though.. no way I'll remember that! :D

---

### Post by CJJones829 on 2011-09-07
> **Beacon11 said:**
> I'm sorry CJ I just started thinking of things and listing them out-- don't feel worthless, you can't just suddenly know everything ;) . I just wasn't thinking while I was typing. Let me elaborate.

No, I would not say that Firefox is better than Chrome-- I actually use Chrome myself. I'm simply trying to help you determine where your mouse problem lies. Try installing Firefox again, and see if the mouse behaves as it should in Firefox even though it's busted in Chrome. If so, it implies that there's an issue with Chrome rather than Ubuntu. This is for the weird-mouse-offset problem only.

Those four steps I gave were for troubleshooting your freezing problem only (not your mouse). Write down or print out those steps and follow them the next time your computer freezes. Let me explain what each step will tell us.

1. Can the cursor still move (just not click on anything)?
This step will help determine at which level the problem lies. If your mouse can still move, it implies that your computer is not "hard frozen" if you will. This means X (the only reason you have a GUI instead of just a terminal) is having issues.

2. Is the clock updating (e.g. wait for 60 seconds and see if the minute updates)?
This will help determine if you're having a problem with keyboard and mouse input. Get a watch or a timer and wait for one minute while watching the Ubuntu clock. Does the minute on the clock update? If you can't move your mouse or type anything but the minute on the clock updates, it implies that X is fine (the screen is repainting) but you're having an input issue.

3. Does the caps lock key light update correctly when clicked?
Similar to (1).

4. Can you SSH into the machine?
SSH stands for "Secure Shell." It is a way of remotely accessing another machine. It is used very often for remote administration of headless (monitorless and keyboardless) servers, and it's also very useful for troubleshooting a machine that isn't responding to local input. However, it does require a second machine. Do you have one? It doesn't necessarily need Linux, but if it's running Windows you'll need to install something like PuTTY: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) . You'll also need to install the SSH server on your Linux laptop:

```
sudo apt-get install openssh-server
```

The login credentials are the ones you use to login to the machine. I can give more specific instructions once I know whether the second computer is Windows or Linux, but if you CAN SSH into your laptop while it's frozen, run those two commands I gave you in the terminal (more explanation below).


Again, the above four steps are meant to be taken while the laptop is FROZEN.

Now, it sounds like not all of your freezes are fatal (i.e. requiring a reboot). Next time you encounter one that is NOT fatal, when it recovers run the following commands in a terminal:

```
dmesg > ~/dmesg.txt
cat /var/log/Xorg.0.log > ~/xorg.txt
```

That will create two files in your home directory-- dmesg.txt and xorg.txt. Open those two files up and paste both of them in here, please.

I know this is frustrating, but don't lose hope yet!

OK, thanks!  I'll try to come back to this when it occurs.

We DO have another computer, but it's my wife's that she uses for work.. and I don't know how cool she'd be with me tinkering around with it too much (in terms of installing programs and etc.)  We'll see what I can pull off.. haha.

---

### Post by Beacon11 on 2011-09-08
> **CJJones829 said:**
> I typed this into the terminal, as you said:

```
sudo nano /etc/default/grub.
```

...

It says that at the top.  But the actual area where you can type is completely blank.

Yeah... remove the period :P . The command should be

```
sudo nano /etc/default/grub
```

---

### Post by Beacon11 on 2011-09-08
> **CJJones829 said:**
> We DO have another computer, but it's my wife's that she uses for work.. and I don't know how cool she'd be with me tinkering around with it too much (in terms of installing programs and etc.)  We'll see what I can pull off.. haha.

If it makes you feel better, if I remember correctly PuTTY doesn't actually need to install, it's just a standalone program. Regardless, if you can't do this step the others will still be helpful.

---

### Post by Bodsda on 2011-09-08
> **Beacon11 said:**
> If it makes you feel better, if I remember correctly PuTTY doesn't actually need to install, it's just a standalone program. Regardless, if you can't do this step the others will still be helpful.
 
There is a Putty installer and standalone packages. Either or.
 
Bodsda

---

### Post by CJJones829 on 2011-09-08
"quiet splash" is already after the DEFAULT= part.  Do I delete the quiet splash thing and then paste in what you told me to add?

---

### Post by Beacon11 on 2011-09-08
No CJ:

> **Blasphemist said:**
> Add radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT=.

Add it after the quiet splash, separated by a space from any other parameters. However, if you want to be more "correct" (no offense to Blasphemist), don't add it to that line, add it to the GRUB_CMDLINE_LINUX variable beneath it. For more information, please reference [http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Editing_etcdefaultgrub](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Editing_etcdefaultgrub) , which specifies that the GRUB_CMDLINE_LINUX_DEFAULT variable is for standard kernel options and should be left as it is.

---

### Post by CJJones829 on 2011-09-08
> **CJJones829 said:**
> OK, thanks! I'll try to come back to this when it occurs.
 
We DO have another computer, but it's my wife's that she uses for work.. and I don't know how cool she'd be with me tinkering around with it too much (in terms of installing programs and etc.) We'll see what I can pull off.. haha.
 
Froze on my break today!
 
1) The cursor will NOT move.
 
2) The clock is NOT updating (watched it for several minutes to see if it would EVER gets started.. never did.)
 
3) The caps lock light will NOT cut on!
 
So yeah.  As far #4, I still have to check with my wife on doing that.
 
I will tell you, it seems like I have most of these issues while trying to connect to a wireless network.  Not so much the one at home anymore (it connects automatically), but when I'm out and about, specifically at work.  The little wifi symbol will start blinking to indicate it's trying to connect, and it'll freeze "mid-blink".  So maybe that helps some.  Keep in mind, it's not like I'm trying to run all these different programs when this happens (or in general, for that matter).  I'm usually just trying to pull up Chromium.
 
Also, I've yet to run into a freeze where it eventually "came back."  So I'm unable to run that command.  I've always had to hard reset (uh oh, learned a new term!) to get it going.  This is after waiting for like 15-20 minutes too.  It's not like I'm just raging after 1 minute and immediately going for the power button.
 
ANYWAY.. help with this problem would be MUCH appreciated!!!
 
P.S. The thing you can do on Ubunto where you can switch between four different work stations (I think they're called work stations) is pretty awesome!  I love, love that feature.

---

### Post by CJJones829 on 2011-09-08
> **Beacon11 said:**
> No CJ:
 
 
 
Add it after the quiet splash, separated by a space from any other parameters. However, if you want to be more "correct" (no offense to Blasphemist), don't add it to that line, add it to the GRUB_CMDLINE_LINUX variable beneath it. For more information, please reference [http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Editing_etcdefaultgrub](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Editing_etcdefaultgrub) , which specifies that the GRUB_CMDLINE_LINUX_DEFAULT variable is for standard kernel options and should be left as it is.
 
Gotcha.  I'll give it a shot when I get off today (around 6ish).  Thanks for keeping up with this for me.  Greatly appreciated!

---

### Post by Beacon11 on 2011-09-08
> **CJJones829 said:**
> Also, I've yet to run into a freeze where it eventually "came back."  So I'm unable to run that command.

Well wait, what about this?

> **CJJones829 said:**
> While typing this message ON the laptop (I'm now typing this on a PC at work), the computer froze for a few seconds randomly and then "ttttttttttttttttttttttttttt" etc. started scrolling in this message box.  I hit backspace and it stopped, and then I had to delete all of the t's.  A few minutes later, everything froze again and I had to restart.

> **CJJones829 said:**
> Froze on my break today!
 
1) The cursor will NOT move.
 
2) The clock is NOT updating (watched it for several minutes to see if it would EVER gets started.. never did.)
 
3) The caps lock light will NOT cut on!
 
So yeah.  As far #4, I still have to check with my wife on doing that.
 
I will tell you, it seems like I have most of these issues while trying to connect to a wireless network.

Very good, we've determined that it's not X alone that is freezing. Next time it freezes, regardless if it's like the time I quoted above where it just hesitated for a few seconds or if it hard locks and you have to reboot, run all of these commands as soon as possible:

```
dmesg > ~/dmesg.txt
cat /var/log/Xorg.0.log > ~/xorg.txt
cat /var/log/syslog > ~/syslog.txt
```

That will create three files in your home directory: dmesg.txt, xorg.txt, and syslog.txt. Past the contents of all three in here.

Also, Blasphemist's idea may work, and is worth a shot. I hate problems like this because you never know for sure if you've fixed it!

---

### Post by Blasphemist on 2011-09-08
> **Beacon11 said:**
> No CJ:



Add it after the quiet splash, separated by a space from any other parameters. However, if you want to be more "correct" (no offense to Blasphemist), don't add it to that line, add it to the GRUB_CMDLINE_LINUX variable beneath it. For more information, please reference [http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Editing_etcdefaultgrub](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Editing_etcdefaultgrub) , which specifies that the GRUB_CMDLINE_LINUX_DEFAULT variable is for standard kernel options and should be left as it is.

Thanks for catching the errors. I pasted out of another document and not only didn't catch that it said to add to the wrong line but also left a period in the command.

Did you succeed in adding the kernel mode setting for radeon? I have a feeling the instruction may be incomplete or even wrong since the document barely includes your card (PALM). It is worth trying though.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

If this is a video issue (and what you've been asked to do should help determine that) it may be that either the xorg-edgers ppa should be tried or you could try the catalyst driver from ATI. I wouldn't send you in those directions without more research than I've done though. There could also just be a better kernel mode setting that I haven't seen documentation on yet. I'm just saying if it is video, there are still things to try.

---

### Post by CJJones829 on 2011-09-08
OK, still not getting this.

Here's what it looks like after I type those two things in:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="" radeon.modeset=1
sudo update-grub

```

As you can see, I added the "radeon.modeset=1" after the LINUX="", and then typed in "sudo update-grub" below that.

Two things..

1. Is that correct in adding the "sudo update-grub" below that?
and
2. When I do this, nothing happens.  What exactly is supposed to happen?

---

### Post by CJJones829 on 2011-09-08
> **Beacon11 said:**
> Well wait, what about this?





Very good, we've determined that it's not X alone that is freezing. Next time it freezes, regardless if it's like the time I quoted above where it just hesitated for a few seconds or if it hard locks and you have to reboot, run all of these commands as soon as possible:

```
dmesg > ~/dmesg.txt
cat /var/log/Xorg.0.log > ~/xorg.txt
cat /var/log/syslog > ~/syslog.txt
```

That will create three files in your home directory: dmesg.txt, xorg.txt, and syslog.txt. Past the contents of all three in here.

Also, Blasphemist's idea may work, and is worth a shot. I hate problems like this because you never know for sure if you've fixed it!

Good point, I forgot about that instance.  I guess my point is that the big freeze seems to happen A LOT more than the small ones.  But I definitely printed that out and will keep it handy incase the small freezing occurs.  Thanks.

---

### Post by Beacon11 on 2011-09-08
> **CJJones829 said:**
> Good point, I forgot about that instance.  I guess my point is that the big freeze seems to happen A LOT more than the small ones.  But I definitely printed that out and will keep it handy incase the small freezing occurs.  Thanks.

No problem-- keep it handy in case either the small OR the big freeze-- in the case of the big one, run it right after you reboot.

As for your grub issue, two things:

1. radeon.modeset=1 needs to go INSIDE the quotes.

2. sudo update-grub is the terminal command you need to run after you save and close the file-- it does not go in the file itself, so you can delete that line.

---

### Post by CJJones829 on 2011-09-08
Now I'm having another problem..

Going to the Software Center, I get a message that I need to do some repairs.

It's trying to download something called "Repairing broken deps".. it starts downloading and then I get this message continually:

> Package operation failed

The installation or removal of a software package failed.

installArchives() failed: E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/unity_3.8.16-0ubuntu1~natty2_i386.deb
debconf: apt-extracttemplates failed: Illegal seek
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/unity_3.8.16-0ubuntu1~natty2_i386.deb
debconf: apt-extracttemplates failed: Illegal seek
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/unity_3.8.16-0ubuntu1~natty2_i386.deb
debconf: apt-extracttemplates failed: Illegal seek
dpkg-deb: error: `/var/cache/apt/archives/unity_3.8.16-0ubuntu1~natty2_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/unity_3.8.16-0ubuntu1~natty2_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/unity_3.8.16-0ubuntu1~natty2_i386.deb


Not to mention, my Update Manager prompted me to do an update last night and even THAT'S not working.

Here's a description of the update that's attempting to be installed:

> Interface designed for efficiency of space and interaction

Changes for the versions:
3.8.16-0ubuntu1~natty1
3.8.16-0ubuntu1~natty2

Version 3.8.16-0ubuntu1~natty2: 

  * src/Launcher.cpp:
    - Launcher does not autohide after drag in Qt apps. (LP: #769703)

It's successfully DOWNLOADED, but cannot be INSTALLED.


Arghhhh.. kind of disheartening.

---

### Post by Beacon11 on 2011-09-09
Sounds like you downloaded a bad deb-- it happens sometimes. Please run the following commands:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Let us know if that problem is resolved.

---

### Post by CJJones829 on 2011-09-09
> **Beacon11 said:**
> Sounds like you downloaded a bad deb-- it happens sometimes. Please run the following commands:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Let us know if that problem is resolved.

Great!  Just ran them.

I did get this though:

```
corey@CJ-Satellite-C655D:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 unity : Depends: unity-common (= 3.8.16-0ubuntu1~natty1) but 3.8.16-0ubuntu1~natty2 is installed
E: Unmet dependencies. Try using -f.
corey@CJ-Satellite-C655D:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
corey@CJ-Satellite-C655D:~$ 

```

On the 3rd part.. to "upgrade".. everything seemed to be OK.

I ran the "-f install" command that it said I should, and I got that "are you root?" message.

What does that mean?  Is that something I need to correct?

Thanks a TON for your help.  Where do you get all of these codes from?!


***UPDATE*** That did the trick!  I am now able to download all of the updates. Awesome!!  I am curious about that "are  you root?" thing though.

---

### Post by CJJones829 on 2011-09-09
> **Beacon11 said:**
> No problem-- keep it handy in case either the small OR the big freeze-- in the case of the big one, run it right after you reboot.

As for your grub issue, two things:

1. radeon.modeset=1 needs to go INSIDE the quotes.

2. sudo update-grub is the terminal command you need to run after you save and close the file-- it does not go in the file itself, so you can delete that line.

Once I add the "radeon" part inside the quotes, how do I save?

---

### Post by CJJones829 on 2011-09-09
> **Blasphemist said:**
> You have the AMD Radeon HD 6250 gpu. This is pretty new and use kernel mode setting. Start with this.


Then reboot and make sure kms is now loaded.

Then let us know if the issue is solved. Thanks.

NEVERMIND!  I used Google and found out how to save and exit.

Now I'm about to reboot and check for the "kms" deal..

Making progress!!

---

### Post by CJJones829 on 2011-09-10
```
dmesg | grep drm
This should indicate that the drm got initialized and set up, with maybe mention of the framebuffer and modes set. E.g.:

```

Typing in the "dmesg" command doesn't do anything.

I went back into that other file to make sure, and the "radeon" thing is still saved in there.

What do you suggest?

---

### Post by Blasphemist on 2011-09-10
When you run the dmesg command is it possible that you aren't getting the right | character? On my keyboard the pipe, that is what it is called, is a shift of the backslash key. It looks like one line above the other on the physical keyboard. And when you say it doesn't do anything, does it cause any message after you press enter or do you just get the command prompt back?

On the other questions. Did you run this after saving the radeon.modeset=1 parameter?
```
sudo update-grub
```
By the way, sudo at the start of a command allows you to run the command with the privileges of root. You get prompted for the password (don't worry when the password doesn't show on the screen as you type it) and then the command runs with elevated privileges. When you ran apt-get -f install you needed to start that command with sudo. So the command is-
```
sudo apt-get -f install
```

---

### Post by Beacon11 on 2011-09-10
> **CJJones829 said:**
> ***UPDATE*** That did the trick!  I am now able to download all of the updates. Awesome!!  I am curious about that "are  you root?" thing though.

Yeah, anything that involves the package manager will require you to be root. That "sudo" bit means "let me be root for just this one command." It's a lot more secure than just being root all the time and praying you don't make a mistake. Blasphemist's solution should take care of the unmet dependencies.

And yeah, your dmesg command means that grep didn't return anything, implying that dms is not being loaded as Blasphemist had hoped.

---

### Post by Blasphemist on 2011-09-10
I looked for more information on the radeonHD 6250 graphics. The open source driver made it into the linux kernel in version 2.6.38 it seems. That may not have been the kernel version that installed from the natty cd. Now that you have succeeded with the updates you are definitely at that version of the linux kernel, or a newer one.

You may need to enable that driver but I don't think so. Are you running the Unity desktop? In unity, just press the BFB (big funny button) at the top left and key add. You'll see the additional drivers application icon. Press enter or click on that. If it shows your radeonHD driver, enable it.

The open source driver that is in the kernel seems to perform good and better than the ATI Catalyst (closed source) driver that can be had from ATI. Are you still having any issues?

---

