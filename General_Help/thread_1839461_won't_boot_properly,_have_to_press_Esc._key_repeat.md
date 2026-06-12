---
title: "won't boot properly, have to press Esc. key repeatedly"
date: 2011-09-05
forum: General Help
---

### Post by LouManChu on 2011-09-05
Alas how problems seem to spring up again in Ubuntu 11.04.  I had previously threaded about how I decided I wanted to mount both of my hard drives at boot by editing the fstab file, found that that was a mistake, so I was able to reset the file using the Live CD and that seemed to fix things, or so I thought.  Somehow, even though the fstab file is exactly as it was before the edit (sudo cp /etc/fstab.bak fstab), I am now getting the GRUB boot loader screen with the choices of Linux Generic, Linux Recovery Mode, MEMTEST X86, and another version of X86.  After trial and error I have found that by selecting the generic option and then tapping the Esc. key about 20 times will eventually get me to the login screen.  If i don't tap the key and let it try on its own, i notice that the monitor on state, green, goes to off state, amber.  In that case I hit Esc. and then the monitor turns on and there is some text in the upper left corner of the screen that, unfortunately, I cannot read too well because the monitor deflection is overly to the left (monitor selection and settings wheel has never worked since I got this thing used - Dell D1226H).  I guess the question here is why do I keep getting this GRUB boot loader coming up?  This is a clean install of 11.04 and there is no other OS installed so from what I have learned this boot choice menu shouldn't be coming up, but it does.  I've been a DOS and Windows user for 20 years now but I might as well not know how to turn the thing on for all it's worth.

---

### Post by drs305 on 2011-09-05
For troubleshooting purposes, after you boot try opening /boot/grub/grub.cfg.

Find the 'recordfail' section and change the timeout from -1 to a 1. Save the file, do NOT run update-grub and see if the system boots without pausing. This will tell us if the problem is because Grub2 is reporting a 'recordfail' event.

```
gksu gedit /boot/grub/grub.cfg
```

> 
if [ "${recordfail}" = 1 ]; then
[COLOR="Red"][s]  set timeout=-1[/s][/COLOR]
  set timeout=1
else
  set timeout=10
fi

Note: If you are pressing ESC after selecting a Grub item this is unrelated to this post. This post deals only with the menu displaying and awaiting your input before proceeding.

---

### Post by LouManChu on 2011-09-05
Here was the lines in the config file as they were:

if [ "${recordfail}" = 1 ]; then
[COLOR=Red]  [/COLOR]set timeout=10
else
  set timeout=10
fi 			 		

I changed timeout=10 to timeout=1, should both entries be=1?  There is a 10 second delay in making a choice, very similar to Windows F8 at boot menu, in a way.  It also seems to be booting normally again (blinking cursor and monitor-off action gone now).  I really don't want a boot menu at all, just a clean boot to the login screen from power up.  I was reading tips on setting GRUB1.99 in Natty and I'm still having trouble comprehending the steps to accomplish my goal.  Sorry for all the hassle, you guys are probably as annoyed with newbs like us as I am with getting this platform working, lol.

---

### Post by drs305 on 2011-09-05
The original line should have had "-1" as the recordfail timeout, meaning that the boot process would stop and await input. The idea is that if Grub detected a problem on the last boot it would prefer to force you to choose an option (even if the same one) rather than trying the same selection again.

With "10" in each, then whether there was a problem or not, the menu should display for 10 seconds and then boot automatically to the default OS.

If it now boots normally, after 10 seconds, you should set the GRUB_TIMEOUT value in /etc/default/grub to 0. You might also make sure you have NOT placed a # symbol at the start of the "GRUB_HIDDEN_TIMEOUT=0" line. Run update-grub. 

One question is how the first recordfail timeout got from "-1" (the default) to "10" but it doesn't really matter at this point. 

Your system is probably detecting a recordfail event, and delaying boot by 10 seconds. To see, try doing the above to set the default timeout to 0 and update-grub. *Then* open /boot/grub/grub.cfg and set the first recordfail value as something longer, say 5 seconds. Save the file but don't update.

The next time you boot, it will either boot without seeing the menu (normal operation) or it will display 5 seconds, then boot (a recordfail problem).

---

### Post by LouManChu on 2011-09-05
I have to admit I'm confused.  Leaving all parameters thus far as is I get a failed boot every other time I restart after which either using Ctl/Alt/Del or a hard reset it will boot normally.  Nothing new has been installed and no files have been changed.  There are other problems here too, unrelated to booting.  This is the 5th install with formats in between.  This can't really be that hard that even a computer savvy guy like myself must spend hours on end at a machine just to get it to work.  Super frustrated now.

---

### Post by drs305 on 2011-09-05
It seems like I ran into this issue within the past few months with someone else but I'll have to try to track it down as the fix escapes me at the moment. I do recall that I was quite surprised as to me that what happened before Grub was invoked shouldn't have mattered (but did).

If I can locate the thread and it is relevant I'll post back.

---

### Post by drs305 on 2011-09-05
Since you are online and may have already read my previous post I'll start a new one.

I found the other thread but don't think it's relevant.

It may be helpful to describe what happens during the 'failed' boot. Do you see the Grub menu (note which kernel is highlighted if you do), splash screen, text, error messages, does it progress past the Grub menu, etc?  Do you have to manually select the kernel the second time, and is it the same as the default?

Do you have multiple kernel options? Grub 2 introduced (I think with Grub 1.99 but I'm not positive) a new feature in which if Grub can't boot a kernel it would try an alternative. I believe it was only if it couldn't use a menuentry and not actually for a failed boot (which is handled by recordfail). 

You could check the kernel version that successfully boots after a hard reset to see if it is the same as the one G2 attempts to boot on the first try (uname -r). Also see if the kernel options are the same if there are different menuentries. 

As you can probably tell, I don't have a definite idea of what your problem could be.... Posting a copy of the boot info script's RESULTS.txt wouldn't hurt if you think the problem is with Grub2. Click the BIS link in my signature line.

---

### Post by LouManChu on 2011-09-07
Thanks for the help but I finally just reformatted and reinstalled.  Everything is fine now.  I think I am going to wait on altering system files until I have a better grasp of the OS.  For now I think the simplest thing to do is to just mount the drives in the desktop.
LMC

I'm going to mark this as unsolved if I can.  Thanks again.

---

