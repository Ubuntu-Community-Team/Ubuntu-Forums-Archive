---
title: "Dual Boot PC not booting.  Please help !!! :-("
date: 2012-01-20
forum: General Help
---

### Post by farmerjohn73 on 2012-01-20
Hi all !

I have an old desktop pc. Celeron 2.4ghz with 1GB DDr Memory.  No CD Drive is working.  Only USB is functioning.  I installed win XP and then Ubuntu 11.04 with dual boot option.  As far as I remember, it has GRUB LEGACY.  Unfortunately, when I boot the PC, it tries to boot but makes a noise and goes off and turns on itself again and makes noise again.  If - Luckily - it boots, it shows me the first screen, verifies DMI Pool Data and takes me to GRUB Rescue Prompt.  I can't use many commands, but when I use " ls " command, it shows " (hd0), (hd0, msdos1), (hd0, msdos2), (hd0, msdos3), (hd0, msdos4), (hd0, msdos5) etc.

I can't understand how to repair the boot loader.  I tried to set prefix to (hd0,1) but it seems it did not work.

Please help restoring this PC.  My daughter needs it !

Thanks in advance...

farmerjohn

---

### Post by xyzzyman on 2012-01-20
What type of noise? Like a mechanical noise from inside the computer? Or beeping? My gut is telling me you most likely have a hrad drive failing and after a few restarts it stays running long enough for grub to boot and crash.

---

### Post by oldfred on 2012-01-20
Does system let you boot USB flash drives? If so you do need to boot and recover/backup data. I have to agree with xyzzyman on hard drive. From a liveUSB you can also check hard drive's Smart Status with Disk Utility.

If getting Grub Rescue you must have grub2. Grub legacy uses error codes for partition not found or other issues.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by dragonfly41 on 2012-01-20
Since you don't have a working CD drive then using Ubuntu Live CD is not an option.
But you can still create a Live USB.
See unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Get hold of an external USB drive and install Ubuntu on USB.

Here is just one of many tutorials which might help you ..
[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair](http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair)

You can also continue trying to repair the internal configuration.
But it does sound like a failing internal disk drive.   
A utility such as PartedMagic will test the health of the noisy internal disk drive.   
Again you can burn this *.iso onto a USB drive and boot into USB by pressing F12 on booting up.


[EDIT] This was posted just after OldFred suggested same approach.  i.e. Live USB.

---

### Post by farmerjohn73 on 2012-01-20
I created ubuntu usb on my laptop.  I tried super grub disk on usb,  gparted on usb, Boot-repair on usb.  I created these usb drives on my laptop and tried them on my desktop.  But no use.  

the sound is like a mechanical noise from inside the cpu.  The hard disk is a new one about two months old.  160GB IDE hard disk.

Boot-repair disk is not working either.

Kindly suggest me a solution.

Update:  If I leave the computer off for at least half an hour, then I can boot and it takes me to grub rescue.  when I use ls command, it shows me (hd0), (hd0,msdos1), (hd0,msdos2), (fd0).  Does it still mean that its a failed hard disk??  BTW, my bios is set to USB-HDD as the first boot device.

---

### Post by oldfred on 2012-01-20
On my system USB-HDD does not work for flash drives. Flash drives are seen as additional hard drives under the select which hard drive to boot.

Do you know which partition has Ubuntu? That is the one you need to use to boot. Do you have a separate /boot as you have to set root to /boot partition but use install partition to boot if that makes sense.

#Display the contents of the /boot folder. Example: ls (hd0,5)/boot
ls (hdX,Y)/boot/grub    
# or try all of them to see which has your /boot/grub files
#Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,5) or sd5
sh:grub>ls (hd0,5)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,5)/vmlinuz root=/dev/sda5
sh:grub>initrd (hd0,5)/initrd.img
sh:grub>boot

---

### Post by xyzzyman on 2012-01-20
If it's a few months old, was it actually purchased new in a sealed box or is it just new to you?

If you feel comfortable, maybe you could start it up with the side of the case off? If you don't stick your fingers in the fans or touch any circuit board you'll be fine. That way you could identify where the noise is coming from. If you aren't sure if it's the hard drive still, lots of times putting your hand on the drive (on the label side not the circuit side) and you'll feel the vibration that matches the noise.

Now if you think it's a fan, I have been known to stick my finger on the disc portion in the center of teh fan to slow or stop it. I am not saying to do that as if it stopped the fan and you kept the system running it could overheat or damage your CPU. Or you could hurt yourself or break the fan possibly.

Either way, we should identify where that noise is coming from as something is broken. If it's just a CPU fan better to fix it now before the sound goes away and there's more damage, or if it's a HDD and it actually is new than it's got at least a 1 year warranty (I'm suspicious about a 160gb ide being new and not being just 'recertified'. There's no such thing as refurbishing a hard drive. It's either good or bad.)

EDIT: In regards to the USB installs, make sure your laptop can boot off of them, so that way you know they are being made properly and you aren't fighting an impossible battle with the desktop.

---

### Post by farmerjohn73 on 2012-01-22
Thank u very much to you all guys !  Problem solved.  It was a RAM problem.

I had two slots of 512MB and one of them was gone !  I removed one from a slot and booted.  It booted normal and smooth !.

I have one old ram of 256MB.  I added that to it as well.  Now I have 512+256.

I really appreciate the interest of all of you people.  You have responded so fast and so well.

 A noob like me gets a morale boost with help like this.

I am really thankful to you all !

Farmerjohn

---

### Post by dragonfly41 on 2012-01-22
For future reference .. there is a memtest on grub menu.   Or on recovery disks such as PartedMagic.

---

