---
title: "Ubuntu won't log in!"
date: 2010-07-10
forum: General Help
---

### Post by Dishin Nutrition on 2010-07-10
I'm running a 64-bit Ubuntu 10.04 LTS on my Compaq laptop. Originally it came with Windows 7 but I cleared the partition and installed Ubuntu 9.10 64-bit instead. Worked flawlessly. No problems. I decided to upgrade (through the update manager) to Ubuntu 10.04 LTS. 

It worked for a few days then I noticed that the mouse wouldn't work (I had a Logitech mouse plugged into a USB port) at random times. Like I'd be browsing the web and then it would stop working. But the mouse wouldn't just stop working. The whole computer just froze on me and I had to hold the power button on the laptop and restart the computer. And then it was only a matter of time in the next session of using the laptop until the mouse froze again.

So, a few days after all these mouse problems occurred, I tried starting up the laptop. Everything seemed fine but when I got to the screen where I select the user I want to log in as and put in the password, the background came up normally but in the middle it was a plain white rectangle with no way to get around it. And the mouse froze too. Occasionally if i keep rebooting, I can get to the log in screen but before I can log in, the mouse freezes again (even if i have the USB mouse unplugged and I'm using the actual pad on the laptop). So, i just want to make this clear, it happens even when the mouse isn't plugged in. I highly doubt the problem is the mouse.

I pressed the Esc button on start up to run self tests on the system and everything passes. All tests. I seriously don't know what to do and I have files very valuable to me and I want this problem fixed. I love Ubuntu and I've NEVER had a problem this bad with it until now. Please help. Thanks in advance

---

### Post by davebgimp on 2010-07-10
Download and burn an Ubuntu CD and run a live-disk session on the laptop and see if you can get at your files there and back them up to an external drive or something. You could also try shelling in if you've already got an ssh server running on it.

After that, I'd try a CD install.

---

### Post by Dishin Nutrition on 2010-07-10
Ok how would i go about running a live-disk session? I'm sorry but I don't know too much about Ubuntu. I'm learning as I go

---

### Post by davebgimp on 2010-07-10
> **Dishin Nutrition said:**
> Ok how would i go about running a live-disk session? I'm sorry but I don't know too much about Ubuntu. I'm learning as I go

You'll first need to download and burn a CD for Ubuntu. Make sure that you burn the correct one, i86 or amd64.

Put it in the computer and boot, tapping whatever key you have to, to get into your system boot menu and boot from the CD.

When the disk menu comes up, choose the option to run ubuntu as a live disk (run from the CD).

---

### Post by Dishin Nutrition on 2010-07-10
Ok thank you very much. I'll let you know how it turns out

---

### Post by jwbrase on 2010-07-10
> **Dishin Nutrition said:**
> I'm running a 64-bit Ubuntu 10.04 LTS on my Compaq laptop. Originally it came with Windows 7 but I cleared the partition and installed Ubuntu 9.10 64-bit instead. Worked flawlessly. No problems. I decided to upgrade (through the update manager) to Ubuntu 10.04 LTS. 

It worked for a few days then I noticed that the mouse wouldn't work (I had a Logitech mouse plugged into a USB port) at random times. Like I'd be browsing the web and then it would stop working. But the mouse wouldn't just stop working. The whole computer just froze on me and I had to hold the power button on the laptop and restart the computer. And then it was only a matter of time in the next session of using the laptop until the mouse froze again.

So, a few days after all these mouse problems occurred, I tried starting up the laptop. Everything seemed fine but when I got to the screen where I select the user I want to log in as and put in the password, the background came up normally but in the middle it was a plain white rectangle with no way to get around it. And the mouse froze too. Occasionally if i keep rebooting, I can get to the log in screen but before I can log in, the mouse freezes again (even if i have the USB mouse unplugged and I'm using the actual pad on the laptop). So, i just want to make this clear, it happens even when the mouse isn't plugged in. I highly doubt the problem is the mouse.

I pressed the Esc button on start up to run self tests on the system and everything passes. All tests. I seriously don't know what to do and I have files very valuable to me and I want this problem fixed. I love Ubuntu and I've NEVER had a problem this bad with it until now. Please help. Thanks in advance

What's your video card?

Can you boot OK with a live CD, or does that also freeze? If a live CD freezes, it may be a hardware or overheating problem. If not, something probably got screwed up with your install.

Aside from that, if you press Ctrl-Alt-F1 (or F2-F6), can you get a text-mode login prompt? If you can, then while we're working on fixing this, shutdown by logging in there and typing "sudo shutdown -P now" so that you don't mess up your filesystem with hard shutdowns. It will also tell us if it's the whole system, or just X that's locking up. 

If Ctrl-Alt-F1 doesn't work, try holding down Alt-Sysreq and typing, with a few seconds pause between each letter, "R E I S U B". If your system isn't completely locked up straight down to the kernel, that should reboot it safely.

---

### Post by Dishin Nutrition on 2010-07-10
> **jwbrase said:**
> What's your video card?

Can you boot OK with a live CD, or does that also freeze? If a live CD freezes, it may be a hardware or overheating problem. If not, something probably got screwed up with your install.

Aside from that, if you press Ctrl-Alt-F1 (or F2-F6), can you get a text-mode login prompt? If you can, then while we're working on fixing this, shutdown by logging in there and typing "sudo shutdown -P now" so that you don't mess up your filesystem with hard shutdowns. It will also tell us if it's the whole system, or just X that's locking up. 

If Ctrl-Alt-F1 doesn't work, try holding down Alt-Sysreq and typing, with a few seconds pause between each letter, "R E I S U B". If your system isn't completely locked up straight down to the kernel, that should reboot it safely.

I booted onto the CD without installing. As the Ubuntu splash screen came up right after that to begin the session, everything froze. 

The computer is not hot and has never had problems booting up until Ubuntu 10.04.

I did the Ctrl-Alt-F1 method on both the CD and without the CD. Computer still froze with the CD. Without the CD, I got into the text login screen where it asked for my password but before I could finish typing it in (or if i just wait too long to start typing) the computer freezes and nothing happens. 

Right now, all I want to do is get the files I have off the computer. I have no problem reinstalling Ubuntu at all, but I need to get those files first. That's my only concern.

---

### Post by jwbrase on 2010-07-10
> **Dishin Nutrition said:**
> I booted onto the CD without installing. As the Ubuntu splash screen came up right after that to begin the session, everything froze.

Oh, did you do this with the Karmic CD or the Lucid one? If you still have the 9.10 one you should try it with that, since you didn't have problems before Lucid.

> 
The computer is not hot and has never had problems booting up until Ubuntu 10.04.

Nevertheless, overheating is one of the more common causes of lockups. If the 9.10 CD locks up, I'm going to say I have to suspect overheating, or else some piece of hardware going bad.

> 
I did the Ctrl-Alt-F1 method on both the CD and without the CD. Computer still froze with the CD. Without the CD, I got into the text login screen where it asked for my password but before I could finish typing it in (or if i just wait too long to start typing) the computer freezes and nothing happens.

I actually wanted you to hit Ctrl-Alt-F1 *after* it locked up in GUI mode, but the fact that it's freezing when you try using the text screen makes me suspect that it wouldn't work if you did it that way.

One thing though: People are sometimes confused by the fact that the text mode login does *not* even print out stars for the password. Since the computer locking up is already on your mind, you may be confusing this for a lock-up. Are you hitting "enter" when you type your password before you judge it to be locked up?

Other than that: When the computer locks up, in text or graphical mode, does Alt-Sysreq-R E I S U B reboot?

> 
Right now, all I want to do is get the files I have off the computer. I have no problem reinstalling Ubuntu at all, but I need to get those files first. That's my only concern.

If worst comes to worst, you can hook the hard drive up to another machine, but that will only be necessary if the computer has a hardware problem that is beyond repair.

Do you have separate root and home partitions? If so, it should be possible to reinstall without touching any of your data (though you'll still have to reinstall all your programs).

---

### Post by Dishin Nutrition on 2010-07-11
Ok I used to 9.10 disk and I used it to pull up Ubuntu 9.10 without installing it to see if I could get at the files from the real Ubuntu installation. Well I can get into the Documents folder from the original Ubuntu install but when I try to click on the folder containing all my documents, I don't have permission to access it. I can't even copy it onto a junk drive because I don't have permission to access it.

I think that it's because I didn't put in the password to access it (like when I log in on Ubuntu 10) but I don't know how to get around this. Please help

---

### Post by jwbrase on 2010-07-11
> **Dishin Nutrition said:**
> Ok I used to 9.10 disk and I used it to pull up Ubuntu 9.10 without installing it to see if I could get at the files from the real Ubuntu installation. Well I can get into the Documents folder from the original Ubuntu install but when I try to click on the folder containing all my documents, I don't have permission to access it. I can't even copy it onto a junk drive because I don't have permission to access it.

I think that it's because I didn't put in the password to access it (like when I log in on Ubuntu 10) but I don't know how to get around this. Please help

I *think* the Live CD allows you to sudo/gksudo without a password (but I've not used it for that purpose, and I don't really have time to figure it out right now). Try opening up a terminal and typing "gksudo nautilus", and see where that gets you.

---

### Post by Dishin Nutrition on 2010-07-11
Thank you so much. That got the files that I needed and now I can delete the partitions and install 9.10 again. Thanks!

---

