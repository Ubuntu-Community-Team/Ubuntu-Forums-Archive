---
title: "Ubuntu 10.10 (64) hangs on boot with USB Card Reader"
date: 2011-04-18
forum: General Help
---

### Post by roszmoef on 2011-04-18
My PC is an Intel Core-i7-950 with 8GB RAM.  The motherboard is an Intel Extreme, DX580G.  Ubuntu (64) 10.10 is the only OS run on this system, and uses the entire hard-disk.

Today, I purchased an internal USB card reader that connects to the USB socket on the motherboard.  Once I connected it, the PC started hanging on boot.  When it hangs, there is nothing but a non-blinking, still cursor on the top left corner of the screen.

Earlier I had set the Grub2 boot delay to '0', and therefore I guess I do not get to see any messages or the Grub2 menu.

The story is the same with an external USB card-reader.  If I connect the external card-reader and try to boot, the PC hangs in the manner described above.

If I disconnect the internal / external USB card-reader, everything is normal.

The following web-page describes the problem in the manner I can understand.  But it does not provide a permanent solution.

[http://superuser.com/questions/121880/grub-hangs-at-starting-up-when-usb-flash-card-reader-is-plugged-in-on-ubun](http://superuser.com/questions/121880/grub-hangs-at-starting-up-when-usb-flash-card-reader-is-plugged-in-on-ubun)

I would be grateful for any solution to this problem.  Please help!

---

### Post by PRC09 on 2011-04-18
Not sure if this will help but I had the same problem until I went into the bios for the machine and changed the boot order to boot from the hard drive first.You may also have the option to turn off the ability to boot from usb which I did as well.It seems to work fine now but if you wish to boot from usb devices you will have to enable it again....

---

### Post by oldfred on 2011-04-18
I have heard never to set delay to 0 as it then is about impossible to get menu when you need it. If you hold shift key down from BIOS do you get menu. Sometimes even with new grub2 the Escape key will also work when shift key does not.

My portable boots from USB, but if I have two keys plugged in, it will not boot. 

Are your USB ports USB3. Those are known to have issues.

I did a full install from one USB to another and removed the installer. The installed would not boot. It seemed that my flash drives get bumped up in drive numbers and the install was sdf or sdg. My last drive is sdc. Even though UUIDs were correct it seemed like the search for UUID stopped working after a long gap in drive letters. I was able to manually edit grub line and remove search and after several trys to find correct drive number changed set root to correct ( hd6,1) or whatever it was. then it booted.

It is my understanding there are also some video issues with the newest systems like yours. What video are you using?

[http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=1)

---

### Post by roszmoef on 2011-04-19
PRC09 @ #2:

I turned off all but the hard-drive and the optical-drive in the boot sequence from the BIOS.  Still the same problem.  BIOS somehow seems to be wanting to boot from the card-reader.

oldfred @ #3:

Me setting the delay to '0' has been working well till I threw in the card-reader into the system.

The USB socket I connected the car-reader to, was a regular USB 2.0 socket.  The motherboard has USB 3.0 ports on the back, but I did not use them for the purpose of connecting the card-reader, and they seem to be working fine with other devices they are connected to.

I use a basic Zotac Nvidia GeForce 8400-GS (512 MB RAM) video card, as the motherboard has no on-board graphics, and there are no problems with the video till date.

I am pulling my hair as to what is this strange thing about the card-reader, that it starts acting like the hard-disk.

---

### Post by oldfred on 2011-04-19
I have a 9600GT and have to add nomodeset to all liveCD boots either CD or USB and on first boot after an install.

I only realized that with a USB install as my USB kept flashing like it was installing but it had turned my monitor off. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by roszmoef on 2011-04-19
oldfred @ #5:

I reiterate that I have no graphics issue. Therefore, the NOMODESET discussion is not pertinent to my problem.

Well, it occurred to me that perhaps there is no solution to this problem in Ubuntu 10.10 - 64 bit.  I removed the internal card-reader, and am now at peace with myself.

Thanks for all the help.

---

