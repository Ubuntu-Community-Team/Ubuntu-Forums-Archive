---
title: "USB issue during start up"
date: 2011-04-13
forum: General Help
---

### Post by smelliothook on 2011-04-13
I have a Zotac ZboxHD-ND02 running Ubuntu 10.04 that I primarily use to run XBMC in my lounge.  I have noticed that after the system boots into either Ubuntu or XBMC, the USB IR receiver is not recognised until I unplug and replug it.  Before I do this, in Ubuntu lsusb hangs indefinitely, or in XBMC no commands from the remote are recognised (even though the receiver flashes a red LED with every key press).

I also suffer from the 'nForce2_smbus 0000:00:03.2: Error probing SMB2' error that is widely reported on fora. [One post]("http://www.ubun2.com/question/545/error_probing_smb2_while_booting_ubuntu_desktop_1004") seemed to think that the two could be linked, however, I've applied [this fix]("http://ubuntuforums.org/showthread.php?p=9311538") and the error message has gone during boot, yet the USB behaviour remains.

So, I thought I would try booting from a USB stick (initially with a bootable Ubuntu stick, made by following [these instructions for Mac]("http://www.ubuntu.com/desktop/get-ubuntu/download")).  When in the BIOS, the system recognises the USB stick and i can set it as primary boot device.  Then the system starts up and, after the Zotac splash screen, it is as if the USB stick is not there.  Also, on boot up, i can press F11 and select the USB stick, but again the boot up process behaves as if no usb stick is present.

I am quite a linux newbie, so not sure how to diagnose the problem further, but it seems as if during start up, the USB ports are not recognised by my linux installation.  Can this be fixed with drivers?  I can't even boot from a USB stick to remove my Ubuntu installation or try another distro.

Any help would be gratefully received

---

### Post by Hippytaff on 2011-04-13
You can find some more info if once booted you open a terminal and do```
dmesg | less
``` it will be a long message so the tail bit of the commad means you can scroll through it by pressing enter. The usb bits will probably be towards the end. this will show you what the kernel is doing at boot, so any problems with usb devices being recognised at boot will be logged here.

---

### Post by smelliothook on 2011-04-14
> **Hippytaff said:**
> You can find some more info if once booted you open a terminal and do```
dmesg | less
``` it will be a long message so the tail bit of the commad means you can scroll through it by pressing enter. The usb bits will probably be towards the end. this will show you what the kernel is doing at boot, so any problems with usb devices being recognised at boot will be logged here.

Thanks for you response, any help is appreciated.

The output from dmesg is here: [http://pastebin.com/pQBfNkCL](http://pastebin.com/pQBfNkCL)

I don't know where to begin diagnosing from that text.  I've can see references to the USB ports, but do not know what to make of them.  Does it tell you anything?

---

### Post by smelliothook on 2011-04-15
I have resovled the issue.

The USB stick (made using the instructions on the Ubuntu download page) wasn't bootable.  I made one using UNetbooin and I could boot from it fine,

I've now installed '[openelec]("http://www.openelec.tv/")', a lightweight linux distro to run XBMC from, and the issues with USB behaviour for my IR receiver are np longer observed.

---

### Post by Hippytaff on 2011-04-15
Excellent...glad you got it sorted.
 
Remember to mark the htread as solved in the thread tools at the top of the page :-)

---

