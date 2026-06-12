---
title: "Can one boot Ubuntu from memory stick?"
date: 2010-10-27
forum: General Help
---

### Post by germanix on 2010-10-27
I have a Sony Viao laptop that is 5 years old. I use it to run Ubuntu 10.04 and it runs well but is relatively slow. This Sony has a slot for a "MemoryStick pro duo", and I have a 4GB card that fits into this slot. My question is: Is it possible to load a bootable version of Ubuntu 10.04 onto this memory card? The idea would be to install Ubuntu on this card instead of the hard drive and to then boot from the memory stick. I am hoping that this will be much faster than booting from the hard drive, and that applications will start quicker. If this were possible how would I need to proceed to install the OS on this stick and which settings would I need to change (and how) to get the computer to boot from this card. Would doing this give me the advantage I am looking for and I guess I also need to know if the 4GB is big enough for this purpose?
Any help and advice would be greatly appreciated. I am not very technically minded so please explain it in such a fashion that I would enable me to follow your advice.
Thank you

---

### Post by corncob on 2010-10-27
I don't know about faster but you should be able to install Ubuntu on your card.  I think it says 2.7 gig minimum memory on the installation screen but that won't leave much space for added stuff.  On the install, select the card as the drive and use entire drive.  It will, by default, install the grub boot loader on the HD but the grub config files on the memory card so you'll need to have the card always inserted to boot the computer.  If your computer is capable of booting directly from the card there is an option in the advanced part that allows you to select where the boot loader will be installed but I haven't been there myself.

---

### Post by Megaptera on 2010-10-27
Sorry but could you confirm if its a card or a stick? You mention both.
It's easy to boot & run Ubuntu from a USB stick / flashdrive but I've not tried it from a card.

USB  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Hakunka-Matata on 2010-10-27
Wieviel memory you have in your laptop is the biggest factor in how fast it will run.  I would use Gparted partition editor to check to see if your memory stick appears as a hard drive.  It would be a quick, simple method to test that part at least.  If it shows up, and you don't have any important data on it, try to format it and see what happens.

Viel Gluck

---

### Post by germanix on 2010-10-27
Well it is called a memory stick but is in fact a flat square card that slips into a special slot for this card on the computer direct and  not into one of the the USB slots.

---

### Post by Megaptera on 2010-10-27
Thanks, I'll see how this goes. I might give a card a try too ...

---

### Post by oldfred on 2010-10-27
If your computer is 4 years old it is borderline on whether it allows booting USB flash drives. Few even today allow booting from memory cards, but I think if you have a USB card reader the computer may thne see it as a flash drive.

Plop is modifying its boot loader to allow other devices to boot.

[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Since Flash drives or card readers are using the USB ports they are slower than SATA. If you system is older it may still have IDE, not sure of speed comparisons to IDE.

---

### Post by corncob on 2010-10-27
Ist das ein SD Card?
I have a similar thread running myself:
[http://ubuntuforums.org/showthread.php?p=10036245#post10036245](http://ubuntuforums.org/showthread.php?p=10036245#post10036245)
They've given me some good links there.

---

### Post by C.S.Cameron on 2010-10-27
> **germanix said:**
> I have a Sony Viao laptop that is 5 years old. I use it to run Ubuntu 10.04 and it runs well but is relatively slow. This Sony has a slot for a "MemoryStick pro duo", and I have a 4GB card that fits into this slot. My question is: Is it possible to load a bootable version of Ubuntu 10.04 onto this memory card? The idea would be to install Ubuntu on this card instead of the hard drive and to then boot from the memory stick. I am hoping that this will be much faster than booting from the hard drive, and that applications will start quicker. If this were possible how would I need to proceed to install the OS on this stick and which settings would I need to change (and how) to get the computer to boot from this card. Would doing this give me the advantage I am looking for and I guess I also need to know if the 4GB is big enough for this purpose?
Any help and advice would be greatly appreciated. I am not very technically minded so please explain it in such a fashion that I would enable me to follow your advice.
Thank you


Booting from a card works fine on most newer computers but won't work on my top of the line Asus that is only 4 years old. Works great on my daughters 1st gen EEE.
You can use the Startup Disk Creator from the Live CD or Universal USB Installer from Pendrivelinux.com as you probably want persistence.
Or you can just do a Full install to the disk, (use manual partitioning and install grub to the card not the internal HDD).
When booting set the card as first HDD in BIOS or press F10 when booting.
4GB is not to bad as long as you are not installing a whole bunch of stuff or saving movies, etc.

Write speed using USB2 is slower than SATA.

---

### Post by germanix on 2010-10-28
I thank all who contributed to this thread for your support and good advice. I will surely try our your suggestions. I understand that the Sony cards have their own standard (not the same standard as other SD cards) and since recently are lo longer produced by Sony. I did see however on Wikipedia that the reading and writing speeds on these cards are not very fast so it may even be slower than the HDD and may therefore not achieve the results I wanted. Be that as it may, as soon as I find the time I will try it out. Thank you once again for all of your help and have a nice day.

---

### Post by corncob on 2010-10-28
From what I've heard these cards do not have 'data leveling'.  That's a technology used on a hard drive to have it write to different areas rather than always in one place so as to spread out the wear.  SD etc cards are usually made for cameras where the intensity of read and writes is not that great.  I understand that using a card as a hard drive may lead to an unexpectedly premature failure.  Somebody correct me if this is old info.

---

