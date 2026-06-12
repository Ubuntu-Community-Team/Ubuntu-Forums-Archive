---
title: "No Boot after update"
date: 2011-03-03
forum: General Help
---

### Post by Otto-C on 2011-03-03
Yesterday my 10.04 was fully up to date. Today brought some new updates. I did the updates and while not required I did a restart. Then it goes to a black screen with a solid white line in the top left corner (flashing). It does not boot. I held down the power button to shutdown. When I press the power button, I get the Dell splash screen, then it goes to a black screen with a solid white line in the top left corner (flashing). Nothing like this has happened before. Any help appreciated.
Computer is a Dell B130 laptop.
tia
otto-c

---

### Post by JKyleOKC on 2011-03-03
Take a look at [http://ubuntuforums.org/showthread.php?t=1699176](http://ubuntuforums.org/showthread.php?t=1699176) and follow the instructions I gave there in post #6...

---

### Post by Otto-C on 2011-03-03
Followed your instructions, nothing happened.

otto-c

---

### Post by JKyleOKC on 2011-03-03
In that case the problem may be something different; hopefully someone else will have more suggestions for you!

What happens if you press the left shift key while booting? If you get a menu of several choices, and more than the top two show as Linux versions, scroll down to the third line and hit Enter. This may get you back into operation and we can diagnose things in more detail.

If that also fails, try the same menu but choose one of the lines labeled "recovery" which will get you another menu that includes an option to fix broken video. That option may clear things up for you, or at least give more leads to help determine what is happening.

---

### Post by Otto-C on 2011-03-03
Left Shift key gives list of kernals.

Selected line 3 gave lengthy list of error messages.
Selected line 4 also gave long list of error messages.
Above repeated with lines 5 & 6 same results.

Live CD mode works just fine.

---

### Post by JKyleOKC on 2011-03-03
Perhaps it's time to re-install, then; you can use the Live CD to copy all the content of your home directory to an external drive, thus saving your data and configuration settings. However you may want to wait a day or two in hopes that someone else will have a less drastic idea to try...

EDIT: By the way, those may not be actual error messages. The traditional Linux boot process displays a steady stream of progress reports while booting. Default Ubuntu installations hide this stream beneath a splash screen so as not to cause confusion. What happens when the stream of messages stops? Does the system then come up, or prompt for a login? And do the messages stay on the screen at that time so that you can copy the last few lines or take a photo of the screen and post them here to help us tell what is happening?

---

### Post by Otto-C on 2011-03-03
Did not wait for the process to go to its conclusion.
Will do that tomorrow and post results.

Thanks for your help and interest.
otto-c

---

### Post by JKyleOKC on 2011-03-03
Could be interesting!

I've been on a couple of other threads with the same or very similar symptoms, and one of them just got solved. Turned out to be a totally failed hard disk. Even when booting from a CD or a USB stick, Ubuntu may look for a swap partition and will use it if it finds one. If the HD is bad, that can cause the boot process to lock up at that point.

It seems pretty unlikely to me that such a thing could happen three times in one day, but it's possible and might be worth looking into if all else fails...

---

### Post by Otto-C on 2011-03-04
Did a recovery mode attempt. Its a 60Gb Hdd and took 30 minutes to complete.
It appeared that in the stream of messages that there were errors. At the
end it showed:
Mountall: FSCK / [318] terminated with status 4
Mountall: File system has errors.
Errors were found while checking the disk drive for /
Press F to attempt to fix the errors, I to Ignore, S to Skip mounting or
M for Manual recovery.
I got interupted and a process started with the initial Ubuntu 'initializing'
screen. The 5 dots were moving but nothing. Let run for about 30 minute then
shut it down.
Attached are picture of some of the screens.
Yesterday I managed to get my stuff onto a USB drive.
Guess my next step will be to try a new install.

---

### Post by JKyleOKC on 2011-03-04
> **Otto-C said:**
> At the end it showed:
Mountall: FSCK / [318] terminated with status 4
Mountall: File system has errors.
Errors were found while checking the disk drive for /
Press F to attempt to fix the errors, I to Ignore, S to Skip mounting or
M for Manual recovery.

 -snipped-

Yesterday I managed to get my stuff onto a USB drive.
Guess my next step will be to try a new install.That first one with "status 4" seems to be a normal termination code but the rest of them at the end do indicate fatal problems on the disk. Hopefully it's simply damaged software rather than a hardware failure.

Glad to know you got your data off to safety. A new install is the best bet. If the install itself fails, though, you might have to replace the drive. Keep us posted!

---

### Post by Otto-C on 2011-03-04
Again thanks for your insight. As a just in case I have a new hdd. Tomorrow in central Florida there will be an install fest (held 1st Sat of month) that I plan to attend. They have been a great help in the past. Will let you know details Sunday PM.
otto-c

---

### Post by Otto-C on 2011-03-06
Well it was a good fest. All did not go as expected.
Did a good install of 10.04. After the install a
restart is automatic. Upon clicking restart it ejected
the cd and promptly displayed a page of i/o error
messages.  Well I decided to install my new hdd and 
went thru the install procedure again.  And surprise,
the same result.  After getting together with some
of the guys, one came up with a Spinrite disk. Well
it took about 4 hours to do the root and swap
partitions we interupted and did a surface scan.
Well it booted normally. Closed it down and booted
again. Ah joy. 
I think next month if possible I'll re-do the original hdd.
Again thanks for your help and interest.

---

### Post by Otto-C on 2011-04-09
Well I guess I took the easy way out. I again
did the Spinrite procedure on the original
problem HDD. Even though it booted when it was
re-installed. The Spinrite reported no errors
and has booted normally since.
Can't thank the guys at the LEAP-CF install fest
enough. 
They have a great fest monthly on the first 
Saturday beginning at 9AM and going to 5PM.
Thanks again.

---

