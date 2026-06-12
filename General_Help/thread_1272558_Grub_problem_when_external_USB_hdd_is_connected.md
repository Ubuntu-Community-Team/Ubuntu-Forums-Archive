---
title: "Grub problem when external USB hdd is connected"
date: 2009-09-22
forum: General Help
---

### Post by meazz1 on 2009-09-22
I have a dual boot XP and Ubuntu 8.10. When I connect the USB hdd (500 gig) and power up the pc, it gives a Grub 17 error. If I have it unplugged and power up the pc, it boots up ok and than I can connect the usb drive and it works fine.
I already set the boot priority to internal drive and for some reason it goes back to the USB drive as the primary boot drive.

My question is, how can I fix this so the pc does not look to boot from the USB drive.

---

### Post by louieb on 2009-09-22
Grub uses boot order to tell which drive is which. On most PCs built in the last few years there are two places you can change the boot order. The 1st is opened by pressing a key at startup and telling it I want you to boot from this device This time only.

The 2nd is in BIOS setup. Where you specify the boot order if you do nothing at boot time. It may be that it is set to boot a USB device 1st if one is found.  

Also I wonder about the MBR of the external drive - it may be that it has stage1 grub code pointing to a GRUB install that is no longer there.

---

### Post by aikiwolfie on 2009-09-22
When you say you set the boot priority to the internal hard drive, are you talking about in the BIOS or in the Grub menu? Did you change the boot order after you installed Ubuntu or before?

So far as I know (and I could be wrong) Grub by default installs to the boot sector of the primary hard drive or the first writeable boot device. I think error 17 is a panic condition Grub throws up when the hard drives aren't all arranged as it is expecting them to be or if one is missing.

To get round this problem you can install Grub manually from the live CD or do what I did. Setup the boot order you want and dissconnect your internal hard drives before installing Ubuntu to the USB drive. Then reconnect them when you're done with the installation process.

That way the installer can't touch your XP boot drive and grub will go on the USB drive. So when you boot up without the USB drive connected it will boot to Windows as though Ubuntu didn't even exist. When the USB drive is connected it will boot to the grub menu and then your default option.

The Grub menu is pretty simple and easy to edit in a text editor like Gedit. So you can add a Windows XP option without too much trouble.

If Grub has been installed to the boot sector of the first internal hard drive you'll have to fix it. Boot to your XP installer disk and choose to repair the system. At the command line type fixmbr. Now reboot and Windows should boot as normal.

---

### Post by aikiwolfie on 2009-09-22
Ah beat me to it. I need to type faster :p

---

### Post by meazz1 on 2009-09-22
thanks for all the information.
I forgot to mention that the external drive is just for storage purpose. There's no OS on it.
Can I tell the Grub to ignore the external drive and go to the right one even if the boot option in BIOS is set to the usb drive?
Can anyone give some steps?

---

### Post by louieb on 2009-09-22
Did you check your boot order in BIOS? Has there ever been an OS on the external?

Maybe fixable. maybe not. Depends on your computer setup. Need to take a closer look.

With the external plugged in. Boot with a Ubuntu live CD and follow  the [URL="http://ubuntuforums.org/showpost.php?p=6725571&postcount=3"]Boot Info Script Instructions
[/URL] it will give a better picture of what is going on. Please put the results.txt in your next post.

---

### Post by aikiwolfie on 2009-09-23
If the external drive is for storage only there shouldn't be an issue with the external drive. What exactly is on the external drive?

---

