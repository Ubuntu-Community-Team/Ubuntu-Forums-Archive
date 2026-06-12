---
title: "Removing Windows Vista from Ubuntu 9.04"
date: 2009-10-18
forum: General Help
---

### Post by jarame on 2009-10-18
Okay guys we have a big problem:

I received a Windows Vista Registry error: Oxc000000d corrupt file or missing error and now Vista will not boot at all. Also when I tell the computer to boot from "Removable Devices" Nothing happens it just goes back to the OS options: Windows Vista or Ubuntu. Selecting Vista just gives me that error, selecting Ubuntu just boots into Ubuntu 9.04 from the partition.

My CD Drive is broken so I cannot use that for any types of restoration =[ But I created an Ubuntu USB stick and it doesn't work when I try to boot from it. Is there something I'm doing wrong? Please help, I would like to wipe my computer clean and only leave Linux on it as the Main OS.

I will provide a screenshot of GParted and my Harddrive and  USB stick.

[IMG]http://i607.photobucket.com/albums/tt156/JamesBrad91/Screenshot-1.png[/IMG]

Is there a way I can format /dev/sda1 from Linux? and If that isn't possible what about formatting my usb stick to ext3? Will that format allow linux to boot from the usb stick?

---

### Post by yanceypd on 2009-10-18
Do you have bios pointed to usb drive for boot device?  You may have to activate some other b service in bios.:)

---

### Post by mike555 on 2009-10-18
if you really want just Ubuntu , use the live cd and install to the whole partition , it will make a swap file for you and install grub ..... if you can back up any documents to an external first......

---

### Post by jarame on 2009-10-18
> **yanceypd said:**
> Do you have bios pointed to usb drive for boot device?  You may have to activate some other b service in bios.:)


In the BIOS that I have in the boot options it says "Removable Devices" but whenever I select it nothing happens.

> **mike555 said:**
> if you really want just Ubuntu , use the live cd and install to the whole partition , it will make a swap file for you and install grub ..... if you can back up any documents to an external first...... 

My CD Drive is broken so USB is all I can try to use D:

---

### Post by yanceypd on 2009-10-18
I'm not too sure about laptops but sometimes with desktops you can point the bios to a similar device as boot device and it will grab the usb device and boot.  Maybe you can borrow a friwends bootable usb cd drive?

---

### Post by cybergalvez on 2009-10-18
Reformating the ntfs partision is simple, gparted can do it, but the partition needs to be unmouned first.  The Issue that I see is that it looks like Linux is using the ntfs partition for its boot partition, which means you will need to receat that. 
If you want to wipe the drive and start over, you have two choices, if you biso supports booting from a USB set it, and try the usb, if not, you will have to get a new cdrom

---

### Post by jarame on 2009-10-18
> **yanceypd said:**
> I'm not too sure about laptops but sometimes with desktops you can point the bios to a similar device as boot device and it will grab the usb device and boot.  Maybe you can borrow a friwends bootable usb cd drive?

> **cybergalvez said:**
> Reformating the ntfs partision is simple, gparted can do it, but the partition needs to be unmouned first. The Issue that I see is that it looks like Linux is using the ntfs partition for its boot partition, which means you will need to receat that. 
If you want to wipe the drive and start over, you have two choices, if you biso supports booting from a USB set it, and try the usb, if not, you will have to get a new cdrom


Well I've now run into an even greater issue...-sigh- So I formatted my USB stick to ext3 and put Ubuntu 9.04 on it using Unetbootin (or whatever the program is called) restarted my laptop, hit F12 for boot options, selected "Removable Devices" and got a black screen containing "Missing Operating System." So I thought: well I'm one step closer, it just didn't pick up the OS on the USB stick. WRONG! I'm missing an OS period!!! What am I supposed to do now? I'm using an old *** desktop cmoputer to post this.

Here's a photo of my screen I took with my phone

[IMG]http://i607.photobucket.com/albums/tt156/JamesBrad91/10-18-09_1746.jpg[/IMG]

Now since I do not have any OS to boot from the Harddrive...is there a way to force my BIOS to boot from a usb stick?

---

### Post by mike555 on 2009-10-18
when you install to a USB key make sure you install grub to the key (not MBR) it should be a little button called "advanced" before the install....

another thing make sure your USB key is set bootable.

---

### Post by PrePenguin on 2009-10-18
Removable device is not the same as your CD/DVD player in the bios just so you know..

---

### Post by jarame on 2009-10-18
> **mike555 said:**
> when you install to a USB key make sure you install grub to the key (not MBR) it should be a little button called "advanced" before the install....

another thing make sure your USB key is set bootable.

Well I'm going to have to try from the computer I'm on now, lol. What program do I use to install Grub? Unetbootin?

> **PrePenguin said:**
> Removable device is not the same as your CD/DVD player in the bios just so you know..

I know what a removable device is. And my CD/DVD is broken.

---

### Post by jarame on 2009-10-21
Well I took my laptop to a computer tech the university that I'm attending, and he said he's borrowing someone's external CD drive. He's gotten my laptop to bring up the OS choices (vista and Ubuntu), so later today I'm going to drop by and bring him my restoration CD and an Ubuntu CD that way I can restore & then install ubuntu only. Once all this is done (if it works) this thread will then be solved  :D

Thanks for all help you guys gave me.

---

### Post by cleverusername on 2009-10-29
I know it's probably a bit late, but what it seems you did when you couldn't get the OS choices menu/Grub up was that while in your BIOS you somehow accidentally disabled booting from your HDD.

But I hope all went well after all. :)

---

