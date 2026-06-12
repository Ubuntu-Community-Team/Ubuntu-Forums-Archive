---
title: "Grub error 17, no bios access"
date: 2009-09-15
forum: General Help
---

### Post by grimstar on 2009-09-15
I hate for this to be my first post on here, however it is...

I bought a netbook roughly a year ago which came with winxp.  I'd say in roughly April I decided to make it dual boot xp/ubuntu remix.  At the time all went smooth minus it not allowing me to make the ubuntu partition very large.  As time went on I ended up with zero space left and couldn't do anything.  I figured I would increase the partition size at a later date and that date happened to be a few days ago.

Being unable to anything in ubuntu I used a program in xp to manage the partitions.  I increased the size of the ubuntu partition and at the end it said something about "...may have affected lilo...,' and of course I didn't think much of it.  Went to reboot and get GRUB error 17.  I searched around and came to the conclusion that a live cd, or in my case a live usb because it's a netbook would be my only solution.  I created a live usb and popped it in with hopes of it catching it and allowing me to do something but alas I am stuck at the error 17 with no way around it.

I have tried any key possible when booting (F1-F12, esc, del, backspace) in hopes of it jumping over to my bios screen but I have not had any luck.  When I originally installed ubuntu I had to do it with a live usb so it should have still been set to load from a usb first anyways... but it just doesn't seem to be happening.

Any help or suggestions would be appreciated.  Right now the only option in the back of my head involves me removing the harddrive and figuring out a way to connect it to another computer.  I don't have the resources for that type of thing readily available so I'm hoping it doesn't come to it.

Thanks in advance.

---

### Post by P4man on 2009-09-16
when you boot from the livecd, can you still access the ubuntu partition and see its files? or is it hosed due to the attempt to change the partition size?

---

### Post by grimstar on 2009-09-16
I can't seem to access anything whatsoever.  It won't let me boot from the live usb.  It goes straight to the grub error with no chance of doing anything beforehand.

---

### Post by dandnsmith on 2009-09-16
If your F12 at boot should allow booting from USB, does it show the device as a possible? If so does it then just not try to boot from it?

I suspect that the process you used to create the liveUSB was flawed in the boot area, and that is why it carries on straight to boot from the HDD.

---

### Post by grimstar on 2009-09-16
I used UNetbootin, selected a disk image which was ubuntu 9.04, selected my USB drive, and let it do the work... is it possible something went wrong with that process?

I could try using it on my desktop to see if it catches it as a bootable usb.

---

### Post by FiggyG on 2009-09-16
That's weird, looks like it isn't finding USB bootloader. I guess I would try an [alternative tool]("http://www.softpedia.com/get/System/Boot-Manager-Disk/Ubuntu-Live-USB-Imager.shtml"). The site is trustworthy, just over-run by advertisements. Be sure to have the tool format the flash drive before you have it copy and setup the image.

---

### Post by grimstar on 2009-09-16
Alright I'll do that right now and let you know the results in a little while.

---

### Post by grimstar on 2009-09-16
Did a format with that tool first, and tapped F12 while booting... still nothing.

I tried all 3 USB ports just to get that possibility out of the way as well and was as unsuccessful as ever.  One thing I will note is that my flash drive is not lighting up when I boot, as in it's not even attempting to access it.  I know my USB ports work so that can't be the reason.

Any other ideas? Or perhaps a way to get in to my bios, or any screen besides the grub error screen for that matter.

---

### Post by danwood76 on 2009-09-16
how did you install the dual boot before?
Was it from a USB?

You should never resize any partitions from windows as the partitioner is about as much use a chocolate tea pot.
Always resize from a live CD or USB and always be careful, I would expect the partitions magic data is screwed due to the move, this can be fixed from a live OS.

When you tap F12 are you presented with a menu?
This should be tapped whilst the BIOS screen is visible (just after power on)

---

### Post by grimstar on 2009-09-16
I set up the dual boot originally with a remix usb.  Between the point where I did that and went to mess with the partitions my dog decided to turn my flash drive into a meal, and that was really the only reason I decided to try and do it through xp.

When I power on I get no screen at all before the grub screen, which is why I'm sure I'm having such a problem.  It leaves me with no opportunity to get in to my bios to do anything.

---

### Post by dandnsmith on 2009-09-16
Without the make/model of netbook, and the BIOS revision, we aren't going to be able to get very far on the boot problem with USB.

My AA1 has a BIOS generated message which says to press F12 to get the boot menu for other devices. Should I not get that, I would think something seriously wrong, as it always appears whether I have an external thing plugged in to USB or not.

Your unetbootin method is one I've used a number of times, always with success (unlike another way I tried).

---

### Post by danwood76 on 2009-09-16
Just a thought you are booting from cold and trying to enter the boot menu?
Some PCs have a quick reboot where you get an extra fast POST and so may not see the BIOS screen.

From a cold boot you should see the BIOS screen!!

---

### Post by grimstar on 2009-09-16
Think I might have done it... got it to load up by holding F2 before I started my netbook.  Went in to gparted and fixed what I thought needed to be fixed... restarted and grub loaded up correctly.

Thanks for the help everyone.

---

### Post by danwood76 on 2009-09-16
Please could you elaberate on what machine and setup you have to help other users?
Also could you mark this as solved?

---

