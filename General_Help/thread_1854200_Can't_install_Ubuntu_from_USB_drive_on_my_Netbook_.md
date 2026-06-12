---
title: "Can't install Ubuntu from USB drive on my Netbook (can't access Windows 7 BIOS)"
date: 2011-10-03
forum: General Help
---

### Post by Ulysses1994XF04 on 2011-10-03
So I bought an Asus Eee PC 1001PXD yesterday that came with Windows 7. I want to replace it with Ubuntu. I downloaded the .iso file to a 2GB USB stick, but when I turn of my computer and restart it, I can't access the Windows 7 BIOS. 

I remember XP had a "press F#" or "press Esc to access BIOS" text when you started up the computer, but with Windows 7, it doesn't display that; it just says "Microsoft Windows" with the yellow loading bar beneath, a black screen, and goes straight to the desktop. I tried pressing Esc, F1, F2, F10 and Del but it didn't do anything.

How do I install Ubuntu from my USB drive on a Windows 7 Netbook?

---

### Post by jocko on 2011-10-03
There is no such thing as a "Windows 7 bios". The bios is part of the motherboard of your computer, and starts before any operating system. To get into the bios you need to press F2 BEFORE windows even starts loading.

---

### Post by Ulysses1994XF04 on 2011-10-03
Okay, so I accessed the BIOS.

I tried to follow the instructions of this video ([http://www.youtube.com/watch?v=xEUlczV2ggI](http://www.youtube.com/watch?v=xEUlczV2ggI)) but it didn't work.

I disabled "Quiet Boot" and "Boot Booster," went to "Boot Device Priority" selected my USB drive with the Ubuntu .iso file, pressed F10, "OK," then Esc.

The screen came up that said "Please select boot device." I selected my USB stick, but it said.

"Invalid system disk. Replace the disk, and then press any key." I removed it, and it went straight back to the Windows 7 desktop.

I'm starting to feel like Window 7 is like herpes; once you're computer gets it, it has it for life :confused:

---

### Post by hyper2hottie on 2011-10-03
If you want to install from a USB stick you can not just put the iso on it.
You need to use a program such as [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to create a bootable usb stick.  Download the windows one and use it to set up the usb stick.

---

### Post by Mr.Enigma on 2011-10-03
your problem is that your USB stick doesn't have a boot sector.  try using the universal boot disk creator here: [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)

Or you can follow the instructions here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Edit-- just to elaborate.  .iso files are images of CD or DVD disks, you can use them to burn cd/dvd's directly or you can mount them as a 'virtual' disk drive.  The boot-disk creator I linked you to above will take that disk image and create a bootable USB drive for you.

The usb will also become a 'live' boot disk, allowing you to play around with ubuntu and give it a 'test drive' without actually making any changes to your computer.  I highly recommend backing up all of your data before you install Ubuntu, do some research on imaging your computer.  That way you can 
1. restore your computer to windows 7 with minimal effort if you want to.
2. Write the windows 7 image to a virtual machine so that you can run windows applications from within ubuntu with minimal effort. (you already own the license, might as well capitalize on it)

---

### Post by Ulysses1994XF04 on 2011-10-04
Holy crap it works! Thank you, much appreciated:popcorn:

---

### Post by spumvis on 2011-11-10
May I ask how you accessed the BIOS?

I tried Wubi for a couple of days on my netbook and decided that I'll switch over to Ubuntu for good.

I uninstalled Wubi but now I can't seem to access the BIOS.


Also, I made a USB key with startup disk creator in Wubi, following the instructions on the main page. Is that good enough to boot from?

---

