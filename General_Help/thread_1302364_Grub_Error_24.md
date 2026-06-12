---
title: "Grub Error 24"
date: 2009-10-27
forum: General Help
---

### Post by PyramidOfMars on 2009-10-27
Hello, 
I recently installed Ubuntu 9.04 along side my windows xp. From the windows environment i resized my Linux partition with Paragon Software. Now when I reboot, grub gets stuck at stage1.5 with grub error 24. I'm typing this message from a different laptop so I can't copy and paste the messages I get by trying some of suggested solutions. I will type what I see. Here is what I have tried: 

sudo fdisk -l returns /dev/sda1 through /sda7. Linux is on sda5 and there is a star by sda2. System for sda2 is HPFS/NTFS. 

sudo /mkdir/root
sudo mount /dev/sda5 /media/root 

for the above line I get the following message: "mout: wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or helper program, or other error."

I then tried:
dmesg | tail
SQUASHFS error. (there are three of these)
sda5: rw=0, wnat=55316504, limit=26571447
JBD: IO error reading journal superblock
EXT3- fs: error loading journal.

then I tried: sudo gedit /boot/grub/menu.lst
I get the following message: "sudo: unable to execute /usr/bin/gedit: Input/output error"

I am trying the above with LiveCD. 

Can anyone please help? How can I go back to using windows without loosing my files.

---

### Post by shaon3343 on 2009-10-27
[B]This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB .
Boot up the live cd and post me the contents of  menu.lst file.

You can also try these command to restore your grub:
          Bootup with a live cd
          open terminal
          then type :[/B]*sudo grub*[B]
           then type : [/B]*find /boot/grub/stage1*[B] 
            then type :[/B]* setup (hd0, X*[B])      here X means partition no
           then type : [/B]*root (hd0)*[B]  
                then quit and reboot pc
I hope these will work to restore your grub.

[/B]

---

### Post by PyramidOfMars on 2009-10-27
Shaon, thanks for your reply. I am able to get into grub directory. Following command gives an error message: 

grub>find /boot/grub/stage1

the above line of code gives the following error: "Error 15: File not found".

What else can I try.

---

### Post by shaon3343 on 2009-10-27
hi , You can try with this link: [http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)

---

### Post by shaon3343 on 2009-10-27
**[COLOR=Black]hi there, I've found another solution for your GRUB 24 error. Here it is: [https://bugs.launchpad.net/ubuntu/+bug/353071](https://bugs.launchpad.net/ubuntu/+bug/353071)[/COLOR]**

---

### Post by PyramidOfMars on 2009-10-27
I am very new to Linux so I apologize if sound like I don't know what I'm talking about. 
I can now post the results of commands i use. Let me start by some of the common ones: 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbac32136

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785        5034    34138125    7  HPFS/NTFS
/dev/sda3            5035       12161    57247627+   5  Extended
/dev/sda5            5035        6688    13285723+  83  Linux
/dev/sda6            6689       11979    42499926    7  HPFS/NTFS
/dev/sda7           11980       12161     1461883+  82  Linux swap / Solaris

what can you see from the above? partition4 seems to be missing and the start and end blocks for sda3 and sda5 seems to be overlapping. Does it mean anything.

---

### Post by shaon3343 on 2009-10-29
[B]> **PyramidOfMars said:**
>  From the windows environment i resized my Linux partition with Paragon Software. 

hi, probably your GRUB had lost permanantly for the resizing. For this it is showing the GRUB 15 and GRUB 24 error . So , you have to reinstall your Ubuntu which would retrive your GRUB and you can work with both windows and linux.[/B]

---

