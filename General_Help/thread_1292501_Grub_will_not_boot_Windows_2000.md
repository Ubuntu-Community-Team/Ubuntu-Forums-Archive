---
title: "Grub will not boot Windows 2000"
date: 2009-10-15
forum: General Help
---

### Post by bswanboat on 2009-10-15
When I select Windows 2000, all I get is the Starting up...
and nothing else. I tried the Grub manually but it just drops out when I get to the boot command. Using debug did not expose any errors. Ubuntu 9.04 boot fine. It is on (hd1,5). Windows ntdlr is on (hd0,0) and the Windows OS is on (hd0,2).

Any suggestions?

Bill

---

### Post by lindsay7 on 2009-10-15
Post the results of the following commnads typed in the terminal


sudo fdisk -l  (that is the lower case letter L)

sudo cat /boot/grub/menu.lst  (again the lower case letter L)

---

### Post by bswanboat on 2009-10-16
bill@ubuntu:~$ sudo -i
[sudo] password for bill: 
root@ubuntu:~# fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9c2b9c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          64      514048+   b  W95 FAT32
/dev/sda2              65        7476    59536890    f  W95 Ext'd (LBA)
/dev/sda5              65        2250    17559013+   7  HPFS/NTFS
/dev/sda6            2251        5437    25599546    7  HPFS/NTFS
/dev/sda7            5438        7094    13309821    7  HPFS/NTFS
/dev/sda8            7095        7476     3068383+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x081beb98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3648    29302528+   5  Extended
/dev/sdb2            3831       19457   125523877+   7  HPFS/NTFS
/dev/sdb3            3649        3830     1461915   82  Linux swap / Solaris
/dev/sdb5               1        3648    29302497   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 520 MB, 520093696 bytes
32 heads, 32 sectors/track, 992 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x000e6330

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         992      507887+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(990, 31, 32) logical=(991, 31, 31)
root@ubuntu:~# 

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows NT/2000/XP (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

The prompt shows Starting Up... right after the chainloader +1 and boot command. The boot.ini file is not being used. It is on the C: drive (hd0,0).

Hope this helps.

Bill

---

### Post by lindsay7 on 2009-10-16
I would try to install grub again and then see what the grub.lst file looks like.

. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type “sudo grub”. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Note:  Do not type in the quotation marks in the commands.


After this run the sudo cat /boot/grub/menu.lst again and post the results,

---

### Post by lindsay7 on 2009-10-16
Also you say windows is on hd(0,2). There is no partition hd(0,2).

You have,

sda1 = hd(0,0)
sda2 = hd(0,1)
sda5 = hd(0,4)
sda6 = hd(0,5)
sda7 = hd(0,6)
sda8 = hd(0,7)

So you would need to change

title Windows NT/2000/XP (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

to read hd(0,x) whichever partition windows is really on.

To edit the grub file, type 

sudo gedit /boot/grub/menu.lst into the terminal and change the parition number.  YOu may need to do a trail and error to get to the correct one.


After you reinstall grub and try the change in patition number in the grub menu for windows, you may also need to reinsstall the windows mbr.  Here is a link to doing this

tp://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php

---

### Post by bswanboat on 2009-10-17
I am making progress. Re-installing Grub did not work. I have not been able to run the live cd without getting the busybox prompt. 

Somehow using the Super Grub disk I was able to wipe out the boot loader. The result was simple GRUB. On the Utimate Boot CD, there is a tool that put in a plain MBR. Now Windows 2000 boots from the very start. Super Grub was able to boot Windows 2000 from the Partition menu (hd0,0). Super Grub failed to reinstall Grub. Super Grub could not find the stage1 file. I do believe it is still there on (hd1,4). 

This has been quite a trip. Now to figure out how to re-install Grub. The LiveCd and Alternate both fail to get to the install Grub task.

Your help is much appreciated!

Bill

---

### Post by lindsay7 on 2009-10-17
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:

Code:
sudo bash ~/Desktop/boot_info_script*.sh
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by bswanboat on 2009-10-17
I have not been able to boot the LiveCD. By taking a real close look at the screen, I notice IO error sr0. It turned out to be a malfuncitioning cable to the cd-rom. Grub has been restored. Windows now boots from Grub. Now it looks like my Ubuntu system needs help.

Making progress. 

I will try the boot log proceedure you just mentioned.

---

### Post by lindsay7 on 2009-10-17
I looked at your post again. When the Windows mbr was reinstalled, it most likely over wrote your grub.  You should try to install grub again with

I would try to install grub again and then see what the grub.lst file looks like.

. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type “sudo grub”. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Note: Do not type in the quotation marks in the commands.


After this run the sudo cat /boot/grub/menu.lst again and post the results,

---

### Post by bswanboat on 2009-10-19
Everything is now working. Somehow the Ubuntu installation was wipped out. It might have happened when I did the rescue broken system from the alternate cd. 

Windows and Ubuntu are now working. 

Your help is much appreciated.

Solved

---

### Post by lindsay7 on 2009-10-19
Great! Good luck on your new system.

---

