---
title: "Windows corrupted by Ubuntu installation"
date: 2011-11-13
forum: General Help
---

### Post by 12dan4 on 2011-11-13
It's a bit of a long and sordid story.

So I once had Ubuntu and Windows 7 happily living together on dual-boot when I had to reinstall windows 7 using factory settings (because this computer was from HP so I don't have a disk). When I did that, Ubuntu and GRUB disappeared. However, the partition was still there from my Ubuntu installation, so I just deleted that.

I wanted ubuntu back today so I reinstalled ubuntu using a flash drive.

The installation only gave me the option of erasing the whole disk and installing ubuntu or advanced partitioning because it said "No operating systems are on this computer" or something like that. I did a bit of a dumb move and I selected erasing the whole disk. That operation failed, so I rebooted. This time, I accidentally "Tried Ubuntu" and I got to the GNOME desktop. Here, when I clicked "install Ubuntu," it showed the actual partitioning of my drive with Windows 7 as sda1, but strangely it said it holds the entire 640GB drive. So I tried partitioning again, and Ubuntu installed.

So then I thought "Yay I have Ubuntu again," but when I tried to access my windows files, the Windows partition is not detected in Windows.

So I decided to go into Windows for the first time after this installation and Windows failed to start because of an error. It's recommending me to insert a Windows recovery disk (which I don't have).

So my nice files on my Windows are now inaccessible (if not gone). One of my friends is giving me his OEM install disk for Windows 7 to see if that'll help. Will it? Or should I download a recovery disk ISO and burn it using ubuntu?

Or are my files doomed forever?

Help? Thanks!

---

### Post by Habeouscorpus on 2011-11-13
>  So my nice files on my Windows are now inaccessible (if not gone).  

Maybe not. There is hope. Boot into a live envrionmetnfrom the disk (click Try Ubuntu) and poke around the disk. Open your Places (or whatever it's called) and look for your Windows partition. If it's blank when you open it up, you're, well, screwed. The restore disk will restore the operating system, not the files. If there's stuff there, congrats! Your stuff is safe. Relocate it.

---

### Post by clausrei on 2011-11-13
Well,  I know so much as you can't install Ubuntu first and later Windows. That does not work. The Windows NT Boot Loader is very selfish and does not allow any other operating system parallel installed on the HDD. Therefore, you always have to install Windows first and later Linux, because then the NT Boot loader will be replaced by the Linux GRUP Boot Loader.

I am just not sure if you will find a way around this, because you obviously already have a separate NTFS and ext4 partition. But I doubt it. 

I guess you will install Windows successfully and after that you will have to instal Ubuntu again. How did you get it working the first time ?

---

### Post by 12dan4 on 2011-11-13
Sorry that I wasn't clear.

I'm on ubuntu right now because Windows is dead.
There is no windows drive I can mount because Ubuntu doesn't detect it. (Probably because it is dead.)

I had it working before probably because my partitions weren't screwed up because of a factory restoration.

---

### Post by JC Cheloven on 2011-11-13
> **12dan4 said:**
> I did a bit of a dumb move and I selected erasing the whole disk.
Phew... who knows. Please post the output of ```
sudo fdisk -l
```
to see what lasts there.

---

### Post by 12dan4 on 2011-11-13
I think you meant "fdisk" :)

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8729

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36412   292471289   83  Linux
/dev/sda2           36412       77826   332658689    5  Extended
/dev/sda5           74837       77826    24008704   82  Linux swap / Solaris
/dev/sda6           36412       73276   296109056   83  Linux
/dev/sda7           73276       74836    12536832   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0244b2b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         500     4014048+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(498, 254, 63) logical=(499, 186, 7)
```

---

### Post by Habeouscorpus on 2011-11-13
Based on that output, I'd say you torched it. Sorry! You overwrote it with linux data during the install. To restore your system to where it was (minus all your data), install Windows first, then follow directions for dual booting windows.

---

### Post by 12dan4 on 2011-11-13
Ahh, well I got what I deserved.

Thanks for the help; I was going to have to reinstall windows next week anyway, sucks to lose my stuff though.

Thanks again!

---

### Post by Mark Phelps on 2011-11-14
If you want to recovery your Win7 files (i.e., personal data), and are willing to expend some time and money ... then read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

