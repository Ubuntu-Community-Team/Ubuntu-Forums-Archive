---
title: "No keyboard after upgrade to 10.04"
date: 2010-08-15
forum: General Help
---

### Post by BSalters on 2010-08-15
After upgrading from 9.10 to 10.04, both my (USB) mouse as well as my (PS2) keyboard stopped working. After googling and trying for hours, I got my mouse to work, but not my keyboard.

The strange this is - if I start in recovery mode, and drop to a command prompt, my keyboard DOES work. I can then login, enter my password, and startx.

However, once the whole graphical interface has started, my keyboard has stopped working again.

For reference, the trick that made my mouse work again is described here:
[http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/](http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/)

There is a chance that I didn't fully understand the description; my setup (obviously) is a little different. The most obvious one is that there was a reference to a "Logitech USB optical mouse" (correct, I have one), and a reference to an "AT Translated Set 2 keyboard" (incorrect,it also is a Logitech).

Now, I don't know if I should have changed anything for that keyboard reference, or not; or that is has nothing to do with this problem altogether. Just figured mentioning it might trigger someone.

Oh yeah, I also tried the 'repair package' option from the recovery menu; no results.

Any ideas?

---

### Post by corrytonapple on 2010-08-15
If it "Magically" works when you start a terminal do this:
[http://ubuntuforums.org/showpost.php?p=9725046&postcount=24](http://ubuntuforums.org/showpost.php?p=9725046&postcount=24)
This will bring up a on screen keyboard. Unfortunately, this is a temporary fix. It is just so you can type while booted in Ubuntu.
Oh and install drivers:
[http://ubuntuforums.org/showpost.php?p=9724443&postcount=2](http://ubuntuforums.org/showpost.php?p=9724443&postcount=2)
This post was written for a wireless Internet issue. It should work the same for you.

---

### Post by BSalters on 2010-08-15
It's probably because I'm such a novice, but this
[http://ubuntuforums.org/showpost.php...6&postcount=24](http://ubuntuforums.org/showpost.php...6&postcount=24)

does not help me to get an onscreen keyboard. When i open a terminal, i cannot type anything; that's my entire problem. No option to type 'onboard'....

ABout the hardware drivers - it does give me 3 options for "Nvidia accelerated hardware drivers, although #3 is both (version current) as well as (recommended). I figure this means I'm already running the recommended version?

Then again, as the problems start once the graphical environment is started, could my non-funtional keyboard have anything to do with graphics drivers?

---

### Post by corrytonapple on 2010-08-15
No. I did not know if you could type in all terminal type applications. I think you might want to go back to 9.10. It is stable and worked for you. Recommended means it is recommended to install it.

---

### Post by BSalters on 2010-08-16
It might be me.... But going back to 9.10 (by the way - how?!) would truly feel like "giving up". 

I fail to see why my problem is so huge, so messed up, that the only solution is to go back to a previous version. Besides, somehow I have the idea that Ubuntu should be able to support a standard Logitech keyboard :)

Does anybody have at least some settings I could check? Some log files I could browse for signs of trouble?

---

### Post by BSalters on 2010-08-16
/edit

I have some extra information, which hopefully triggers someone. 
- I tried a USB keyboard, instead of my normal ps2. No effect, it still doesn't work.
- I found a suggestion, that since it seems related to the graphical environment of X, bad/corrupt video drivers might be the cause. The solution would be to delete Xorg.conf. This had no effect either (other than reducing the resolution of the login screen to something that looks like 640x480)
- The bootloader shows some stuff I don't fully understand. My options (7 in total), all start with "Ubuntu 8.10", even though I just upgraded to 10.04
- The kernel versions I can choose from, are 2.6.27-9, 2.6.27-7 and 2.6.22-14; all generic and recovery mode. Somewhere I read that never versions seem around (?)
- In the recovery panel there is an option to "update the GRUB bootloader". Could this have anything to do with my problem (given that Ubuntu seems to boot just fine)?

- Using the 10.04 live CD, the keyboard DOES work!

---

### Post by corrytonapple on 2010-08-16
> **BSalters said:**
> /edit

I have some extra information, which hopefully triggers someone. 
- I tried a USB keyboard, instead of my normal ps2. No effect, it still doesn't work.
- I found a suggestion, that since it seems related to the graphical environment of X, bad/corrupt video drivers might be the cause. The solution would be to delete Xorg.conf. This had no effect either (other than reducing the resolution of the login screen to something that looks like 640x480)
- The bootloader shows some stuff I don't fully understand. My options (7 in total), all start with "Ubuntu 8.10", even though I just upgraded to 10.04
- The kernel versions I can choose from, are 2.6.27-9, 2.6.27-7 and 2.6.22-14; all generic and recovery mode. Somewhere I read that never versions seem around (?)
- In the recovery panel there is an option to "update the GRUB bootloader". Could this have anything to do with my problem (given that Ubuntu seems to boot just fine)?

- Using the 10.04 live CD, the keyboard DOES work!
Have you installed something that could conflict? *(Thinking back to the Mac OS 9 Days)*? For GRUB see this: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275%5C"). This will remove the extra kernels and update grub. What is your specs for your machine? Is the other keyboard Logitech as well? Two keyboards on differnet interfaces don't work hmmmmmmmmmmmm;)
Congratulations on "Spilling the Beans". Now, pick them back up.:p

---

### Post by BSalters on 2010-08-17
- Have you installed something that could conflict?
Nope, nothing at all. I was just starting to work with Ubuntu, and had not attached or installed anything special. 

What is your specs for your machine?
- Relevant parts are an intel Q6600 CPU, Asus p5k-e motherboard, 4Gb of ram and a Nvidia GTS8800 videocard. About 3 years old, nothing really special I'd think.

-Is the other keyboard Logitech as well
Nope, the other keyboard I owned was a fairly standard microsoft USB keyboard. I never attached both of them at the same time though; just tried one, restarted, then the other, restarted again.

I'll have to look into the whole bootloader and GRUB thingie. I'm a bit careful, cause I have a nicely working triple-boot system with Vista, Win7 and Ubuntu now. It still uses the windows bootloader though to 'jumpstart' GRUB. It has always worked, so it isn't my first suspicion to cause a malfunctioning keyboard now. And it would, ehm, suck if an update attempt of GRUB results in a completely non-functioning multi-boot system; as Murphy's law dictates, that would probably mean Ubuntu is the only one left working, but without keyboard support...

---

### Post by corrytonapple on 2010-08-17
**Not **to say that is your Graphics card fault being it is a good card, but you should have everything updated. To go back to 9.10, you would have to do a clean install I believe. Anyway, upon setup did you choose the correct keyboard layout? IF you do not know, go to **System>Preferences>Keyboard **and see if things like response time and layout are correct. If not, fix them to your needs.

---

### Post by BSalters on 2010-08-19
> If you do not know, go to System>Preferences>Keyboard and see if things like response time and layout are correct. If not, fix them to your needs. 

Well, I don't really remember what type of keyboard I selected upon install. After all, my 'install' dates back to version 8.10. I can't remember selecting anything special.

Anyway, I tried several different settings for the keyboard. Different models, different manufacturers. No change whatsoever: no keyboard entries at all.

I'm starting to think that indeed, the only solution is the "good old" (ahum) windows trick of "just reinstall, and everything will be fine". Not exactly an encouragement to keep experimenting with Ubuntu, as a beginner :(

---

### Post by corrytonapple on 2010-08-19
Try another one on both keyboard interfaces. At this point the good ole' reinstall trick seems to be the best idea. I never have and won't upgrade. Clean install for me is the only way.

---

