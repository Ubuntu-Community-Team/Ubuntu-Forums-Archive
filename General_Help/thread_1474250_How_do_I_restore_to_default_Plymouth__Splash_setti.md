---
title: "How do I restore to default Plymouth / Splash settings?"
date: 2010-05-05
forum: General Help
---

### Post by crjackson on 2010-05-05
Here's the deal.  After installing the proprietary nVidia drivers for my 8800 GT, the purple UBUNTU ..... boot screen got gigantic and ugly.

So...  I installed startupmanager and changed the settings from 640x480 to 1024x768.

The result was a garbage (scrabbled) boot up splash (UBUNTU ...).  That didn't work out so I set everything back to 640x480 but that made it go to no splash on boot (black screen until GDM), and a garbage UBUNTU ... splash on shut down.

How can I just put it back to the ugly / gigantic boot screen that was there before I screwed it all up?

I'd hate to reinstall fresh just to fix this, but I'm picky like that.

Thanks

---

### Post by crjackson on 2010-05-05
> **crjackson said:**
> Here's the deal.  After installing the proprietary nVidia drivers for my 8800 GT, the purple UBUNTU ..... boot screen got gigantic and ugly.

So...  I installed startupmanager and changed the settings from 640x480 to 1024x768.

The result was a garbage (scrabbled) boot up splash (UBUNTU ...).  That didn't work out so I set everything back to 640x480 but that made it go to no splash on boot (black screen until GDM), and a garbage UBUNTU ... splash on shut down.

How can I just put it back to the ugly / gigantic boot screen that was there before I screwed it all up?

I'd hate to reinstall fresh just to fix this, but I'm picky like that.

Thanks

Okay, so I have tried every setting known to man using startupmanager and the results are the same still.

Then I went to synaptic and reinstalled all the currently marked packages and the result was no change.

Can someone who KNOWS what they're doing (as opposed to me who knows nothing about Plymouth and booting) PLEASE advise me how to fix the damned thing?

---

### Post by WorMzy on 2010-05-05
Try the following:

```
sudo dpkg-reconfigure plymouth && sudo update-initramfs -u
```

---

### Post by crjackson on 2010-05-05
> **WorMzy said:**
> Try the following:

```
sudo dpkg-reconfigure plymouth && sudo update-initramfs -u
```

Cool.  I'll give that a try in the morning.  Already in bed and on the laptop right now :-)

---

### Post by pizza-is-good on 2010-05-05
I had the same problem. Solved it [here]("http://ubuntuforums.org/showthread.php?t=1472951").

Hope you get it working.

~pizza

---

### Post by crjackson on 2010-05-06
> **WorMzy said:**
> Try the following:

```
sudo dpkg-reconfigure plymouth && sudo update-initramfs -u
```

okay ran this.  I have a decent shutdown splash screen and NO boot splash/animation at all.  The grub menu is now tiny, screen goes black for several seconds, then I get the Login GDM.

---

### Post by crjackson on 2010-05-06
> **pizza-is-good said:**
> I had the same problem. Solved it [here]("http://ubuntuforums.org/showthread.php?t=1472951").

Hope you get it working.

~pizza

Okay I'll try this link and see what happens.  It's looking more and more like a clean install is coming.

---

### Post by crjackson on 2010-05-06
> **pizza-is-good said:**
> I had the same problem. Solved it [here]("http://ubuntuforums.org/showthread.php?t=1472951").

Hope you get it working.

~pizza

Okay, so I did this and it helped.  It now looks strange but I do get a boot splash once again.  It's small and has horizontal lines running through it like an old lowrez RGB monitor would have.  I'll play with the resolution a little and see if I can't solve that.

My Grub menu however is still too small and in high-res. I wasn't able to make a change there and it's livable but it sucks.

---

### Post by crjackson on 2010-05-06
Okay, I'm making much progress.  I followed the "Graphical Solution" as well and now I have a "CLOSE" to normal Plymouth screen.  The screen has 2 wide black bars (blank spaces) where the screen is not filled on the sides.  I think (and hope) that changing the resolution will fix that problem, I'll let you know how it turns out.

Also, my grub2 menu still won't go back to the default resolution but it may not be possible to have it that way.  I can live with the Grub.

---

### Post by crjackson on 2010-05-06
> **crjackson said:**
> Okay, I'm making much progress.  I followed the "Graphical Solution" as well and now I have a "CLOSE" to normal Plymouth screen.  The screen has 2 wide black bars (blank spaces) where the screen is not filled on the sides.  I think (and hope) that changing the resolution will fix that problem, I'll let you know how it turns out.

Also, my grub2 menu still won't go back to the default resolution but it may not be possible to have it that way.  I can live with the Grub.

It looks like I'm stuck with the black vertical bars.  As far as I can tell, the monitor is running at a different freq. during the boot process when Plymouth is displayed.  If I could freeze the booting process at that point (while the purple ubuntu screen is showing) I could adjust the monitor controls to compensate, but I don't know how to freeze it at that spot.

Does anyone know how to halt booting when the splash screen is showing and leave it in tact so I can adjust my monitor?

---

### Post by Shakz on 2010-05-06
Dont be afraid of the command line solution. Make sure you set to to match your desktop resolution. For my latptop its 1280X800.

Command line :

     gksu gedit /etc/default/grub 

 and add the line in BOLD.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via  VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
[B]GRUB_GFXPAYLOAD_LINUX=1680x1050

[/B]The resolution chosen should be your monitors native resolution.
Save the file and run

     sudo update-grub 



Reboot...should be golden.

---

### Post by crjackson on 2010-05-06
> **Shakz said:**
> Dont be afraid of the command line solution. Make sure you set to to match your desktop resolution. For my latptop its 1280X800.

Command line :

     gksu gedit /etc/default/grub 

 and add the line in BOLD.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via  VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
[B]GRUB_GFXPAYLOAD_LINUX=1680x1050

[/B]The resolution chosen should be your monitors native resolution.
Save the file and run

     sudo update-grub 



Reboot...should be golden.

Shakz,

I'm anything but afraid of the command line.  When I said I did the graphical solution, I was referring to th LINK in the previous post that was labeled graphical solution.

I actually did do everything by the command line, and it's all good now except, that the boot up freq. for that screen isn't configured properly on my CRT monitor.  If I could freeze the bootup process when the purple UBUNTU logo with the animation is on screen, I could adjust my monitor and make it PERFECT.

I'm done tweaking the OS boot process.  It's golden.  I need to tweak my monitor now.

Do you know how to freeze the boot process without getting dumped to a text output?

---

### Post by isbiyanto on 2010-05-08
> **WorMzy said:**
> Try the following:

```
sudo dpkg-reconfigure plymouth && sudo update-initramfs -u
```

worked for me, thanks

---

### Post by undoIT on 2010-05-11
> **Shakz said:**
> 

```
gksu gedit /etc/default/grub
```

and add the line in BOLD.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via  VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
[B]GRUB_GFXPAYLOAD_LINUX=1280x800

[/B]The resolution chosen should be your monitors native resolution.
Save the file and run

sudo update-grub

Reboot...should be golden.

Finally!!! No more big ugly 16 color 1995 boot splash! Thank you. Now I can boot my Macbook without feeling embarrassed for Ubuntu when people are looking over my shoulder ;)

(except for the low graphics mode bug that pops up randomly because of the crappy Nvidia proprietary driver). One bug at a time...

---

### Post by crjackson on 2010-05-11
> **undoIT said:**
> (except for the low graphics mode bug that pops up randomly because of the crappy Nvidia proprietary driver). One bug at a time...

What driver version do you have?

---

### Post by undoIT on 2010-05-12
> **crjackson said:**
> What driver version do you have?

I think I may have solved that as well today. I was using nvidia-current (19x series). Just for the hell of it, and because I was totally fed up with this bug, I decided to try the 173 driver.

Wow! Not only is the low graphics mode bug gone, I'm also not getting the freezes anymore when the graphics card is running above 61 degrees celsius. Karmic, Lucid and even OS X where plagued with freezes and I was sure that it was a hardware issue. I'm not so sure anymore.

I got the graphics card up to 84 degrees celsius for around 15 minutes earlier today, no crashes. And, I've been running glxgears with a youtube video for over 30 minutes now, GPU at 75 degrees and CPUs much hotter than normal, still no crashes. I need to do more testing, but I am beginning to think that the newer Nvidia drivers (for both Linux and OS X) are total crap, at least for the 9400m card.

---

### Post by crjackson on 2010-05-12
> **undoIT said:**
> I think I may have solved that as well today. I was using nvidia-current (19x series). Just for the hell of it, and because I was totally fed up with this bug, I decided to try the 173 driver.

Wow! Not only is the low graphics mode bug gone, I'm also not getting the freezes anymore when the graphics card is running above 61 degrees celsius. Karmic, Lucid and even OS X where plagued with freezes and I was sure that it was a hardware issue. I'm not so sure anymore.

I got the graphics card up to 84 degrees celsius for around 15 minutes earlier today, no crashes. And, I've been running glxgears with a youtube video for over 30 minutes now, GPU at 75 degrees and CPUs much hotter than normal, still no crashes. I need to do more testing, but I am beginning to think that the newer Nvidia drivers (for both Linux and OS X) are total crap, at least for the 9400m card.

Glad you got it worked out.  I wouldn't say the newer drivers are total crap though.  They are working great for many people (myself included).  I have no issues with heat or locking up.

---

### Post by undoIT on 2010-05-12
> **crjackson said:**
> Glad you got it worked out.  I wouldn't say the newer drivers are total crap though.  They are working great for many people (myself included).  I have no issues with heat or locking up.

I guess I'm biased, because I've had nothing but issues with Nvidia cards. The newer drivers (18x series and 19x series) seem to cause freezes with the 9400m card in my Macbook 5.1, not to mention the low graphics mode bug which makes the Macbook almost unusable in Lucid.

And, with the Dell Latitude E6400 I've owned for the past year+ with Nvidia 160m, I have never been able to run compiz in either Kubuntu Jaunty or Karmic, because after maybe an hour or so with compiz enabled, X will freak out with all of this garbage on the screen, the computer becomes unresponsive and I have to hold down the power button to do a cold reboot.

I have purchased a Lenovo ThinkPad T410s to replace the E6400 and it is running perfectly fine with Intel integrated card. I have never had any issues with any of the laptops I have owned that use Intel cards.

I think it is much more likely that these Nvidia driver issues would've been fixed by now if Nvidia provided open source versions. Nvidia seems to have no interest at all in supporting an open source version of their drivers. After reading this:

[http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1)

I decided that I will not be purchasing any laptops with Nvidia cards in the future.

---

### Post by brendanpiater on 2011-03-26
> **WorMzy said:**
> Try the following:

```
sudo dpkg-reconfigure plymouth && sudo update-initramfs -u
```

Worked for me, thank you.

---

