---
title: "Keyboard no longer active during boot, so I'm stuck at GRUB"
date: 2011-01-06
forum: General Help
---

### Post by mjpatey on 2011-01-06
Hi, all-

I just replaced my RAM, and searched for the best way to do a memory test in Ubuntu.  I ran across this page:

[https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

...which says:> 


[LIST=1]
[*]Turn On or Restart the system
[*]Hold down Shift to bring up the GRUB menu.
[*]Use the arrow keys to move to the entry labeled Ubuntu, memtest86+
[*]Press Enter. The test will run automatically, and continue until you end it by pressing the Escape key
[*]Allow the test to run for at least one full pass
[/LIST]
So I did exactly that.  The GRUB menu appeared, but I had no keyboard control, and thus couldn't select anything.  I've tried rebooting several times with different keyboards, and they all show 3 green lights at the very beginning of boot, but become unavailable by the time GRUB appears.

So I booted to a Live CD and the keyboard worked just fine inside that session.  But it's still gone during boot.  When I'm booting without a CD in the drive (booting to the internal HD as usual), it goes straight to the GRUB list, with no keyboard control, and I'm stuck indefinitely.

Any idea how to either bypass this stuck GRUB screen, or somehow restore normal keyboard functionality during early boot?  Thanks in advance for any light you can shed!

-Mark

EDIT:  I'm running Ubuntu 10.10 64-bit.

---

### Post by ububaba on 2011-01-06
I was just starting to write when I discovered your message.
My problem is 100% ditto. I have gone through the motions, no
respite.  

> **mjpatey said:**
> Hi, all-

I just replaced my RAM, and searched for the best way to do a memory test in Ubuntu.  I ran across this page:

[https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

...which says:So I did exactly that.  The GRUB menu appeared, but I had no keyboard control, and thus couldn't select anything.  I've tried rebooting several times with different keyboards, and they all show 3 green lights at the very beginning of boot, but become unavailable by the time GRUB appears.

So I booted to a Live CD and the keyboard worked just fine inside that session.  But it's still gone during boot.  When I'm booting without a CD in the drive (booting to the internal HD as usual), it goes straight to the GRUB list, with no keyboard control, and I'm stuck indefinitely.

Any idea how to either bypass this stuck GRUB screen, or somehow restore normal keyboard functionality during early boot?  Thanks in advance for any light you can shed!

-Mark

EDIT:  I'm running Ubuntu 10.10 64-bit.

---

### Post by Bucky Ball on 2011-01-06
When you boot to the Grub screen there is not a countdown and it goes to the login screen if you leave it? I have a similar issue. I have no keyboard at the grub menu. I let the countdown go and it boots normally. Once booted, I can restart and when I get to the grub menu I have keyboard. That's what I need to do if I want to boot into another kernel or Windows.

---

### Post by ububaba on 2011-01-06
However I have an additional problem. Countdown does not apppear at all. 
I can spend the whole day, just waiting.

---

### Post by mjpatey on 2011-01-06
@Bucky Ball-

Ah, that gives me a clue, then... I have no countdown, so there's a GRUB config file that needs editing somewhere (to set the countdown timer to something other than 0).  I will look into that and post back here if it works!

Thanks!

-Mark

---

### Post by Bucky Ball on 2011-01-06
Timer set to 0 will just skip the grub screen altogether and take you to the login screen. If you are not getting a list with a selection of kernels to boot into, when you start the machine and it goes through the set up for the machine, start pressing escape. That will get you to the menu.

You should have keyboard at that stage as hasn't actually logged into the OS startup yet.

---

### Post by mjpatey on 2011-01-06
This is odd; I don't seem to have a /boot/grub.menu.lst, so I can't edit it.  Well, off I go to try the ESC key method... thanks for the suggestions, and I'll be back shortly one way or the other!

-Mark

---

### Post by Bucky Ball on 2011-01-06
> **mjpatey said:**
> This is odd; I don't seem to have a /boot/grub.menu.lst, so I can't edit it.  Well, off I go to try the ESC key method... thanks for the suggestions, and I'll be back shortly one way or the other!

-Mark

grub2 is used now and is very different to grub. ;)

Check section 4 here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Generally, /etc/default/grub is where you set most things up now.

---

### Post by ububaba on 2011-01-06
I think the cause must be something else even if one gets stuck in the grub.
I have tried three different hard drives with different versions of Ubuntu.
Result is the same in each case!!!!

---

### Post by mjpatey on 2011-01-06
So once I've edited /etc/default/grub, I have to run "sudo update-grub" to update the contents of /boot/grub/grub.cfg.  The problem is, while I'm editing this, I'm booted into a live CD session, not the Ubuntu installation that's having the problem (because I can't).  Because of this, won't that command update the grub.cfg for my temporary live CD session, instead of the grub.cfg on my hard drive?

-Mark

---

### Post by mjpatey on 2011-01-06
OK, I'm back!  Not sure if the keyboard is back to being active at boot, but I was able to bypass GRUB finally. :-)

Here's what I did:

In the same directory as GRUB2's grub.cfg, there's a file called "grubenv". At one point in its header, /etc/default/grub checks to see if grubenv contains the string "recordfail", and if so, the timeout is set to -1 (which I assume means to wait indefinitely for keyboard input, as that's what was happening to me).  If that condition isn't met, then it counts down from 10 and proceeds to load the default OS.

So I opened my grubenv and saw that it did contain "recordfail=1" as shown below in the contents of the file:

> # GRUB Environment Block
recordfail=1
##########################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################

I made a backup of the file, then edited the original, removing the line with "recordfail=1" and rebooted.

Well, it worked!  I am now typing this post from my normal desktop.  :-)

Now off I go to see if my keyboard still isn't working during boot...

Thanks, Bucky Ball!  And ububaba, tread lightly with this stuff... it worked for me, but certainly I'm no expert at this stuff, and it may have hurt more than it helped, for all I know.

-Mark

---

### Post by mjpatey on 2011-01-06
Just rebooted and my keyboard still is not active during the early stages of boot.  In fact, pressing "caps lock" does nothing (caps lock light doesn't come on) until I see my login screen.

So keyboard is fine in Ubuntu, but is no longer picked up by my BIOS, maybe?  I'm going to mark this thread as "solved" (since I did find a way to get out of the infinite GRUB wait) and start a new one about just the keyboard.

Thanks again, everyone!

-Mark

---

### Post by mjpatey on 2011-01-06
Keyboard problem also solved!  See here:

[http://ubuntuforums.org/showthread.php?t=1661610](http://ubuntuforums.org/showthread.php?t=1661610)

:-)

---

### Post by Bucky Ball on 2011-01-07
Well done! You sound like you now have my problem. I boot to the kernel menu (grub) with all OS options and no keyboard. At the login screen everything is fine. Doesn't bother me too much but kinda curious.

When you are into Ubuntu and go for a restart, can you then select things in the menu and keyboard works??? That's what's happening here.

*** EDIT: Got you, just read your other post. I'm on a laptop so my keyboard obviously not plugged into a port.

Enjoy ... ;)

---

### Post by mjpatey on 2011-01-07
I didn't try that when I was still having the problem... but check the link in my earlier post to the solution I found to the keyboard problem.  Basically, I had my keyboard (a PS/2 keyboard) plugged into the **mouse** port.  Ubuntu had no problem working around my mistake, but the BIOS wasn't so forgiving.  Now that the keyboard is plugged into the correct PS/2 port, the BIOS is recognizing my keyboard once again!

---

