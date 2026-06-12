---
title: "Problems on an Acer Netbook"
date: 2012-06-14
forum: General Help
---

### Post by little muddy on 2012-06-14
I am a Linux newby, but an old vintage computer collector. I recently acquired an Acer Aspire one netbook with an Atom N450 processor. 1G mem, 160G HD. No cd rom, but 3 USB sockets. It came with Win 7 on CDs but the previous owner installed Ubuntu 11.10.
 When it starts up it displays error: hd0 out of disk Press enter to continue. It does start up tho if left alone to a Nautilus 3.2.1- Home desktop. and gives me an error message could not display "x-nautilus-desktop:///". referring to an absent service file. There are other minor problems including "Grub" terminal which won't start up when I attempt to access it at start-up. In attempting to change or get rid of the admin password I lost it and my replacement doesn't work altho it doesn't now require one for log-in, but does to install an app. A re-install would seem in order from a USB boot which the BIOS is set up for if I can find the 11.10 boot on the Ubunto site. Version 12.xx is featured with no list of earlier versions. I would prefer a dual boot with Win 7 but repair of 11.10 would seem a better starting place, tho there's no data I wish to retain. Sorry for the length of this.

---

### Post by black veils on 2012-06-15
why does is have to be 11.10 ?

maybe you should try a lighter distribution based on Ubuntu, like Xubuntu, Lubuntu or Bodhi Linux ?

what is the harddrive size?  is Windows already installed?

---

### Post by chocklet on 2012-06-16
You can find Ubuntu 11.10 here...

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

<>

I don't understand the hard drive error message.  Perhaps the first thing to do is determine whether the hard drive is sound.  Put Ubuntu 11.10 live image on a USB flash device and test the Aspire One hard drive.  

If the hard drive is sound... Install Windows first, then install Ubuntu from the USB device.  Aspire One will not boot from an internal SD card slot (at least mine will not).

Just a suggestion... besides Windows, create four partitions for
- Ubuntu 11.10 (ext4)
- swap
- data (FAT32)
- a second Linux distro (ext4)

If you put all your data files (pictures, music, documents, etc) on the data partition, then the two Linux partitions can each be 15GB or so.  15GB is enough for lots of software, assuming that you won't be running graphics-heavy games on the oldish atom-based Aspire One.

The second Linux distro would preferably be one that uses Grub 2 (also called grub 1.99). You might try 12.04 Unity, which also offers a classic menu option.

<>

If your hard drive is not sound, then you can continue to use your Aspire One by booting Knoppix (DVD version) from a USB device.

Good Luck!

---

### Post by little muddy on 2012-06-25
My apologies for not responding sooner, but LIFE does get in the way. I attempted to reply earlier today but the reply I was writing using the ACER wound up disappearing (Yes I can use the I-net on it.) Arrrghhh ! The gods like to toy with your mind when they know your stressed.
 So this reply is being crafted on Win$ Notepad so I have a back-up to paste.
 I used the Universal USB Installer to download to a USB and attempt to reinstall Ubuntu 10.11 The Acer just ignored it. I then used Uni-USB Inst. to install Ubuntu Vers. 12.04 on my USB. After 2 frames it stalled on Intel "Pineview" VGA accelerator and sat displaying a flashing "-", as if waiting for another command. I have 4 Acer MS$ cds for Win7 starter; Recovery disk 1, Recovery Disk 2, Language Disk, and System Disk, which I transferred to a 16G USB, placing each of them except the Sytem disk in folders, since it was the only one with an autorun file.  Acer replied with a "no OS installed". What now ?
 I have an IBM USB FDD I acquired through my own paranoia about FDD-less devices some time ago. I am on the "trailing edge" of technology after all, and am 76 years of age, with a long IT history. I'm wondering if I could perhaps use it without installing the drivers which came from China. Surely if the BIOS boot choices, which includes USB FDD floppies it would recognize an IBM. If so I could perhaps using DOS pull out all my old arsenal of MBR, Boot Managers, HDD test, etc. utilities to eventually install a "modern" OS.

---

### Post by little muddy on 2012-06-25
I should mention that Ubuntu was only using about 3G of the 160G hdd. I also noticed many of the system folders were empty. The HD disk utility test also mention a few of the sectors were damaged and also displayed a READ failure. Since it works for many apps, I can't believe the hdd is toast. A new installation would have tested the hdd and marked as bad those  sectors which were unusable. I tend to think the original Ubunto installation was flawed perhaps with the size of partitions. It's a question of how I can get past the limitations and correct it. In the old days reformat and reinstall the OS. Perhaps the USB floppy is the key, if the Acer Bios will accept it. An FD with SBM and Ranish Boot manager could be the key.

---

