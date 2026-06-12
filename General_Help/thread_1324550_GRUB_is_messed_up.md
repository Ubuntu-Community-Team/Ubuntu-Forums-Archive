---
title: "GRUB is messed up"
date: 2009-11-12
forum: General Help
---

### Post by TheHimself on 2009-11-12
My machine was dual boot Ubuntu (UNR) and XP and I installed Moblin (the one available on moblin.org) on a new partition. But now Ubuntu doesn't boot. I get the message  "BOOTMGR missing". XP can be booted. I think if I install Ubuntu Moblin Remix in place of the current Moblin then I might get Ubuntu back to work.

---

### Post by Giblet5 on 2009-11-12
Linux (any distro) is like that movie "The Highlander": there can be only one (that controls grub).

Your second install overwrote the good boot menu and now you'll have to boot a Live CD and fix it.

Please boot a Live image, run the following command and post the output in a CODE block ('#' in the comment editor): ```
sudo fdisk -l
```

Also, please insert notations like <<-- Ubuntu, <<-- Moblin, >>-- XP, etc. That will help us figure out how to sort your installs and create an ideal grub menu.

---

### Post by TheHimself on 2009-11-13
Thank you.

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66666666

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       15540    82879335    5  Extended
/dev/sda3           15541       19203    29423047+  83  Linux
/dev/sda4           19204       19457     2040255   82  Linux swap / Solaris
/dev/sda5            5223       10176    39792973+  83  Linux
/dev/sda6           10177       15170    40114273+   7  HPFS/NTFS
/dev/sda7           15171       15540     2971993+  82  Linux swap / Solaris

Disk /dev/sdc: 1041 MB, 1041629184 bytes
33 heads, 61 sectors/track, 1010 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes
Disk identifier: 0x8ef631df

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     1049447     2022496   979374166   66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(734, 123, 14) logical=(1049446, 20, 47)
Partition 1 has different physical/logical endings:
     phys=(120, 143, 6) logical=(2022495, 32, 9)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?     1713539     3672971  1972168331    7  HPFS/NTFS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(1713538, 15, 31)
Partition 2 has different physical/logical endings:
     phys=(784, 0, 13) logical=(1539355, 11, 19)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     1629317     2599739   976730017   7d  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(252, 59, 46) logical=(1629316, 9, 22)
Partition 3 has different physical/logical endings:
     phys=(139, 118, 4) logical=(466123, 13, 24)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?     2076186     2080321     4161550   6f  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(2076185, 22, 46)
Partition 4 has different physical/logical endings:
     phys=(10, 114, 13) logical=(2080320, 11, 61)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```
 
sda5 is Ubuntu, sda1 is XP and sda3 is Moblin. sda2 contains sda5,6 and 7. Sorry, I don't understand what you mean by your last sentence.

---

### Post by Giblet5 on 2009-11-13
One more question:

Is /dev/sda5 Ubuntu 9.10 or an earlier release?


9.10 uses Grub2, while older releases uses 'legacy' grub. Configuration is different between the two.

---

### Post by TheHimself on 2009-11-13
It's 9.04.

---

### Post by Giblet5 on 2009-11-13
OK!

Open a terminal window and enter the following commands. I recommend selecting, copying, and then pasting (via Shift-Ins) each line to the terminal window, one at a time.

```
sudo bash ## DANGEROUS. ENTER COMMANDS EXACTLY.
mkdir /mnt2
mount /dev/sda5 /mnt -text
mount /dev/sda3 /mnt2 -text
cp /mnt2/boot/grub/menu.lst /mnt/tmp/menu.lst
sync;sync;umount /mnt2
gedit /mnt/tmp/menu.lst
```

Now, scroll down to the first kernel image definition. It will look like ```
title           Moblin
root            (hd0,2)
kernel          /vmlinuz-2.6.XX-XX-generic root=/dev/sda3 ro quiet splash
initrd          /initrd.img-2.6.XX-XX-generic
```

Remove all text *except* that entry, then save it out.

Now run:
```
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
cat /tmp/menu.lst >> /boot/grub/menu.lst
nano /boot/grub/menu.lst
```

Verify that XP, Ubuntu, Moblin, and memtest86 are defined. Save any changes. Run:

```
grub-install /dev/sda
sync;sync;reboot
```

You should boot with a working grub menu, all OSes available, bootable, with singing angels.

You need to uninstall grub in Moblin via.

```
sudo apt-get remove grub --purge
```

New kernels for Moblin will have to be configured by hand over in Ubuntu...

---

### Post by TheHimself on 2009-11-13
I made things much worse by trying to install UMR first. I thought the installer was a friendlt one like that of Ubuntu but the first thing it did was to try to format my hards drive... I had such a problem once before with CentOS. Does it kill them to add a simple warning before starting the format?

So, now nothing can be booted and when I turn on the computer 

```

grub>

```

shows up. I don't know how much of my hard drive has been erased.

---

### Post by TheHimself on 2009-11-13
In grub when I type 
```

root (

```

I get the message 
```

Filesystem type unknown, using whole disk

```

---

### Post by Giblet5 on 2009-11-13
Wow. Aren't you glad you do daily backups now? :)

Aren't you glad that you posted your partitioning info earlier? :)

Boot from the Live CD.

Re-create the partitions (with fdisk) as follows, and don't change *anything* from this layout:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       15540    82879335    5  Extended
/dev/sda3           15541       19203    29423047+  83  Linux
/dev/sda4           19204       19457     2040255   82  Linux swap / Solaris
/dev/sda5            5223       10176    39792973+  83  Linux
/dev/sda6           10177       15170    40114273+   7  HPFS/NTFS
/dev/sda7           15171       15540     2971993+  82  Linux swap / Solaris
```

Make sure you use the Start and End information.

Write out the changes, then try running ```
sudo dosfsck -a /dev/sda1
```

It might recover something.

Then try running ```
sudo fsck -n /dev/sda3
```

There's a chance that is intact.


Back up Linux data with the "tar" command. Example where you're backing up to a gigantic USB stick that mounts at /media/USBstick (substitute the real mount point):

```
sudo mount /dev/sd3 /mnt -text
cd /mnt
sudo tar -cpf /media/USBstick home
cd
sudo umount /mnt
```

Back up Windows data by just copying it somewhere (Windows doesn't have a very sophisticated file security system).

Once your data is saved, you can blow it all away and start over.

---

### Post by TheHimself on 2009-11-15
Yes, I'm so glad for doing so. Quite accidentally I came across

Recovery is Possible Linux

[http://en.wikipedia.org/wiki/Recovery_Is_Possible](http://en.wikipedia.org/wiki/Recovery_Is_Possible)

It's a Linux distribution which is less than 100 MB and contains everything you need to recover your file system.First I recovered the partitions. Everything othar than sda1 was intact. Then I had to edit GRUB (again available in RIPLinux). There was a small problem because the name of the kernel in Ubuntu was not just "vmlinuz". And then rebooted the computer and ... presto! Ubuntu was working.  Also, Windows is gone! I didn't have any data there. I kept it just in case.  

I still can't install UMR. I copied the iso file from Ubuntu website to a flash drive (using usb-creator) but when I boot it, syslinux comes up saying

boot:

---

