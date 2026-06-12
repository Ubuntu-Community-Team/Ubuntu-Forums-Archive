---
title: "Blank screen after Ubuntu splash"
date: 2010-06-27
forum: General Help
---

### Post by 6tonspacefly on 2010-06-27
Hi.  I have been using Ubuntu 10.04 for some time now and everything was working fine until this morning.  When I start up my computer it goes through its normal things, gets the the Ubuntu splash screen - the one with the little white dot progress bar - and then when that goes away it just goes to a blank screen.  I have no ability to do anything at that point, Num Lock and Caps Lock don't work either - the little lights don't illuminate on my keyboard.  The most recent thing that I did was install the Important Security Updates that Ubuntu told me to install last night.  Other than that I haven't changed my system in anyway.  Thank you.

---

### Post by Spr0k3t on 2010-06-27
There's a couple things I know to try...

When the computer system is booting up, hold down the shift key and get into the grub2 menu.  From there, select an older kernel or try the recovery mode.  In the recovery mode, you can get into a shell and check logs etc.  Also, try and repair any broken packages.

The other thing you can try ([thanks to UbuntuGeek]("http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html"))
> Restarting Ubuntu safely when it is frozen

If anyone faces a freeze with Ubuntu where you cannot do anything, then this will certainly be helpful if you want to reboot the OS as cleanly as possible without damaging their HDD&#8217;s or losing their data.

In case of a freeze where you cannot do anything, simply press Alt+PrintScreen+R+E+I+S+U+B, keep in mind that the underlined keys must be kept pressed through the rest of the sequence AND that you will need to keep holding the sequence keys for a small period of time before going to the next one so that their actions can be carried out properly (For example, hold the R key for about 1-2 seconds before moving on to S). If the sequence does not work at first, then increase the time period between each sequence key press and try again.

If anyone requires a good way of remembering the sequence R+E+I+S+U+B, just remember &#8220;Reboot Even If System Utterly Broken&#8221;.

Raw (take control of keyboard back from X), tErminate (kill -15 programs, allowing them to terminate gracefully), kIll (kill -9 unterminated programs), Sync (flush data to disk), Unmount (remount everything read-only), reBoot.

NOTE:- This keystroke does not work in the event of a kernel freeze as the keystroke sequence depends on the kernel in order to unmount and make the required steps before the restart.

---

### Post by 6tonspacefly on 2010-06-27
Wow!  Thank you so much Spr0k3t.  I didn't know how to get to the loader screen, I tried everything BUT holding shift.  With that I was able to get into a low graphics mode.  Since it booted into low graphics that tipped me off to the fact that it may be a graphics issue.  I reinstalled my ATI drivers and the problem was resolved.  Thank you.

---

### Post by Spr0k3t on 2010-06-27
Rock on 6ton!  Don't forget to mark the thread as solved so others will be able to benefit from the same information.

---

