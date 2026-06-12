---
title: "Odd startup screen about 10% of the time"
date: 2010-09-15
forum: General Help
---

### Post by seattlyte on 2010-09-15
Please take a look at the linked photo and let me know if you've seen a startup screen like this before, or if you have any suggestions on why this happens.  Using Lucid Lynx, btw.[IMG]http://www.flickr.com/photos/68395383@N00/4993248863/sizes/l/[/IMG]

If the photo isn't included (this is my first post) the link is: [http://www.flickr.com/photos/68395383@N00/4993248863/sizes/l/](http://www.flickr.com/photos/68395383@N00/4993248863/sizes/l/)

---

### Post by blueridgedog on 2010-09-15
Looks like your monitor is out of synchronization with the frequency of the graphics card...just a guess.

---

### Post by seattlyte on 2010-09-15
Thanks, [blueridgedog]("http://ubuntuforums.org/member.php?u=459469") - anything I can check through the command prompt (or elsewhere) to see if this is actually the case?

---

### Post by blueridgedog on 2010-09-16
Have you tried turning the monitor off and on or unplugging/plugging in the monitor cable when this happens?

---

### Post by seattlyte on 2010-09-16
No, because it's a laptop, so that's not a possibility (as far as I know!).

---

### Post by blueridgedog on 2010-09-16
Is there another OS on the laptop?  Is there ever an issue with the other OS?  When it fails, what happens?  Do you need to reboot or will things work eventually?  Does the system appear to boot normally and just have a corrupted display (do you hear the start up sound?).

---

### Post by seattlyte on 2010-09-20
This Dell came with Windows XP Media Center.  We switched it over to Ubuntu earlier this year.  We're pretty sure that OS is completely gone.

When this happens, it freezes up and the computer cannot be shut off without holding the power button for a couple seconds.

There is no start up sound because it doesn't get to the screen where the Ubuntu theme is played; it's just before that.

---

### Post by efflandt on 2010-09-20
Looks like the same problem I had with a Dell laptop.  What video chip do you have?  Mine has Radeon Mobility X1300.  That and the X1300 on my desktop do not like kernel mode setting (kms) enabled by default for ATI and some others in 10.04.

Although, on my desktop video was just sluggish and video would not shut off for suspend/hibernate.  On the laptop, it often gave a pattern of red or orange hash marks and froze during boot.  The solution in both cases was **nomodeset** kernel boot parameter (or more specific **radeon.modeset=0** if you have a usb drive that also boots on computers with other video).

I cannot paste the complete link properly with Chromium
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes) and see: "Working around bugs in the new kernel video architecture" under "Other known issues".

---

### Post by seattlyte on 2010-09-22
Thank you for the advice, efflandt - it does sound like a similar problem to what's occurring on this machine. I'm not sure what video chip this has.  If it said on the back at one time, it's rubbed off.

I'm a bit of a noob, so I'm not sure how to get into grub to add nomodeset to GRUB_CMDLINE_LINUX as suggested by your [link]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture") suggested.  I'm able to get into etc/default and see grub, but I"m not sure what to do from there.  I know there are a few editing programs, but I'm blanking on what they are.

In any case, is following the above advise, plus the rest [then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset to the line beginning with # kopt=, then run sudo update-grub)] what you did?  If so, has the problem gone away?

Thanks to you and blueridgedog for your suggestions.

---

### Post by seattlyte on 2010-09-27
What efflandt suggested seems to be correct.  A friend of mine showed me how to use gedit:
sudo gedit grub
And then I ran an update which performed the rest of the tasks.

Thanks!

---

