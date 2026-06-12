---
title: "WUBI installation gives &quot;no root file system is defined&quot; error upon rebooting."
date: 2011-02-25
forum: General Help
---

### Post by Timos798 on 2011-02-25
Hey everybody,
I recently wanted to install Ubuntu ony my Windows 7 computer so I could dual-boot both Windows 7 and Ubuntu. I tried to use Wubi to install Ubuntu because I didn't want to be faffing about with all the different settings and such, everything seemed to be going fine until I restarted the computer and chose to boot Ubuntu. After it booted into Ubuntu it gave me the error "No root filesystem is defined. Please correct this from the partitioning menu." And I couldn't even press anything apart from shut down. Does anybody know why this is happening and how I can fix it? 
Thanks in advance.

---

### Post by MirkoRK on 2011-02-25
When I was learning Ubuntu,on one partition I was have Windows 7,on the other one (second) I was have Ubuntu 10.10. I was use program called Unebotin.It's very easy process to install Linux from USB stick.Try if you want.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Rubi1200 on 2011-02-25
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

The information from the script should help us figure out what is going on and will make offering solutions easier.

Thanks.

---

### Post by Timos798 on 2011-02-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 3,697,309,695 3,697,102,848   7 HPFS/NTFS
/dev/sda3       3,697,309,696 3,907,024,895   209,715,200   7 HPFS/NTFS


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        50AC2687AC266824                       ntfs       System Reserved               
/dev/sda2        3C12287212283376                       ntfs                                     
/dev/sda3        FC764E07764DC2DE                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

```

This is everything found in the RESULTS.txt file
Thanks for the quick answer and detailed instructions Rubi1200

---

### Post by Rubi1200 on 2011-02-25
Hi and thanks for posting the results of the boot script.

I notice the results mention a GPT layout; this has been known to cause problems for Wubi installs.

I will consult with forum member bcbc, a Wubi expert, and we will try and have an answer for you as soon as possible.

Thanks.

---

### Post by Timos798 on 2011-02-25
Thank you Rubi1200, you're a lifesaver. Does it matter if I have some data on my hard drive though? Because I have some important data and I don't want to delete it, but I don't have anywhere I could back it up to. :confused:

---

### Post by Rubi1200 on 2011-02-25
Don't do anything yet please. Wait for either bcbc or myself to respond with possible solutions.

---

### Post by bcbc on 2011-02-25
I'm going to refer you to [this unhappy thread]("http://ubuntuforums.org/showthread.php?t=1687840"). The poster didn't quite make it through, but forum user **srs5694** seems to be an expert on GUID Partition Tables (and the poster didn't follow the instructions given).

I too have seen reports that having a mix of MBR and GPT partition tables will prevent Ubiquity from installing (both in that thread as well as for Wubi). The solution is apparently to remove the leftover GPT information. But I can't advise on that other than to say that [one user reported that "testdisk"]("https://bugs.launchpad.net/ubuntu/+bug/259540/comments/25") solved the problem, but **srs5694** strongly advised against testdisk in that first thread I linked to.

So... bottom line - it won't install in your current state. You can try some of the solutions mentioned, but make sure you back up first.

---

### Post by Rubi1200 on 2011-02-25
Whatever you decide to do, make sure you have full backups before proceeding.

If all this seems too scary, you could always consider installing Ubuntu in VirtualBox:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by srs5694 on 2011-02-25
Concerning the GPT thing, it appears that the disk has leftover GPT data that haven't been completely removed. [This page of mine](http://www.rodsbooks.com/gdisk/wipegpt.html) describes why this can be a problem and how to fix it. The short "how to fix it" answer is to download and install [GPT fdisk (gdisk and sgdisk)]("http://sourceforge.net/projects/gptfdisk/files/") for Linux (use the latest version, *not* the version in the Ubuntu repositories, which is old and has bugs that will cause problems with this procedure) and then type the following commands:

```

sudo sfdisk -d /dev/sda > parts.txt
sudo sgdisk --zap /dev/sda

```Copy the parts.txt file to a removable disk (USB flash drive, CD-R, or whatever), preferably before you run sgdisk; you can use parts.txt to recover if some horrible problem occurs. If you prefer to work from Windows, you can use gdisk for Windows, as described on my Web page, although I don't know of an easy way to back up your partition table in Windows.

All this said, I'm not sure that the stray GPT data issue is the cause of the problem reported by Timos798. The Linux kernel normally ignores stray GPT data; the usual problem that this situation causes is with partitioning software based on libparted, which sometimes either uses the GPT data inappropriately or gets confused and claims that no partitions exist on the disk. It's conceivable that the combination of a WUBI install and the stray GPT data is causing the problem, though. In any event, the stray GPT data do confuse some utilities and so are best removed, IMO.

---

### Post by bcbc on 2011-02-25
> **srs5694 said:**
> All this said, I'm not sure that the stray GPT data issue is the cause of the problem reported by Timos798. The Linux kernel normally ignores stray GPT data; the usual problem that this situation causes is with partitioning software based on libparted, which sometimes either uses the GPT data inappropriately or gets confused and claims that no partitions exist on the disk. It's conceivable that the combination of a WUBI install and the stray GPT data is causing the problem, though. In any event, the stray GPT data do confuse some utilities and so are best removed, IMO.
Wubi also uses ubiquity to install so it's probably affected in the same way as a normal install when it checks the partitions.

---

### Post by Timos798 on 2011-02-25
Thank you to everyone who replied and tried to help! I will come back tomorrow morning and update you on what has happened with Ubuntu, hopefully you're suggestions will work. 
Thanks alot!

---

### Post by Timos798 on 2011-02-25
Oh one more thing before I forget. If I buy a second hard drive, could I install Linux on the second one and keep Windows 7 on the first one? Would that allow me to dual-boot?

---

### Post by bcbc on 2011-02-25
> **Timos798 said:**
> Oh one more thing before I forget. If I buy a second hard drive, could I install Linux on the second one and keep Windows 7 on the first one? Would that allow me to dual-boot?
Yes, absolutely. 

The only thing to consider is where to put the grub2 bootloader. If you can select which drive to boot from the BIOS then you can completely separate Ubuntu and Windows. Otherwise, you can install grub2 on the windows drive's MBR (ubiquity default I believe). This works fine if the drive is permanently installed, but not so well if it's an external USB drive that's not always present.

---

### Post by Timos798 on 2011-02-27
> **srs5694 said:**
> Concerning the GPT thing, it appears that the disk has leftover GPT data that haven't been completely removed. [This page of mine]("http://www.rodsbooks.com/gdisk/wipegpt.html") describes why this can be a problem and how to fix it. The short "how to fix it" answer is to download and install [GPT fdisk (gdisk and sgdisk)]("http://sourceforge.net/projects/gptfdisk/files/") for Linux (use the latest version, *not* the version in the Ubuntu repositories, which is old and has bugs that will cause problems with this procedure) and then type the following commands:

```

sudo sfdisk -d /dev/sda > parts.txt
sudo sgdisk --zap /dev/sda

```Copy the parts.txt file to a removable disk (USB flash drive, CD-R, or whatever), preferably before you run sgdisk; you can use parts.txt to recover if some horrible problem occurs. If you prefer to work from Windows, you can use gdisk for Windows, as described on my Web page, although I don't know of an easy way to back up your partition table in Windows.

All this said, I'm not sure that the stray GPT data issue is the cause of the problem reported by Timos798. The Linux kernel normally ignores stray GPT data; the usual problem that this situation causes is with partitioning software based on libparted, which sometimes either uses the GPT data inappropriately or gets confused and claims that no partitions exist on the disk. It's conceivable that the combination of a WUBI install and the stray GPT data is causing the problem, though. In any event, the stray GPT data do confuse some utilities and so are best removed, IMO.

I'm sorry if this sounds retarded, but how do I run GPT fdisk on linux? I typed in the two terminal commands and it said that the GPT data has been destroyed. Is this good or bad, and is that how the program is run, because I'm used to Windows where you double click and it opens up a window with the program. Does it just run it inside the terminal or what? Thanks.

---

### Post by Rubi1200 on 2011-02-27
Did you download the file from the link srs5694 provided?

If yes, just click on it to open in Software Center. It will ask you if you want to install this newer version or the older version. Agree to install the new version.

That should be it.

---

### Post by Timos798 on 2011-02-27
Yeah I downloaded it from the link, and then I installed it in Ubuntu Software Center, do I not have to do anything after that except write in those two commands? And once I do that I can install Ubuntu into a new partition? 
Thanks

---

### Post by Rubi1200 on 2011-02-27
If you ran those commands after installing that should be it.

But, just to make sure, post the output of ```
sudo fdisk -lu
```

---

### Post by Timos798 on 2011-02-27
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d7e06ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848  3697313791  1848553472    7  HPFS/NTFS
/dev/sda3      3697313792  3907028991   104857600   83  Linux

Disk /dev/sdb: 2006 MB, 2006974464 bytes
16 heads, 32 sectors/track, 7656 cylinders, total 3919872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8bc4d4c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8064     3919871     1955904    6  FAT16
ubuntu@ubuntu:~$ 


```
That's the output when I typed in sudo fdisk -lu Hopefully all should be well :S

---

### Post by Rubi1200 on 2011-02-27
Unless the output is incorrect, it appears the GPT data is gone.

Do you want to try installing Wubi again?

It might be worth starting there just to make sure the problem really is resolved. If all is good and you like Ubuntu you can always do a proper dual-boot later.

What do you think?

---

### Post by Timos798 on 2011-02-27
I don't really want to try Wubi again, because I have to use my Xbox 360 hard drive as a storage space for backup (I know I'm a broke **** XD) but it's too small to hold all my data and I don't want Wubi to delete all my stuff again.

---

### Post by Timos798 on 2011-02-27
One last thing, now when I try to install Ubuntu 10.10 to my newly created partition, it just says straight away that no root filesystem is defined. How would I remedy this? The partition I am trying to install to is an ext4 partition. If anyone could give me detailed instructions on how to do the dual-boot install properly, it would be greatly appreciated.

---

### Post by Rubi1200 on 2011-02-27
Please tell me you made backups before starting!

To answer the question:

Choose manual partitioning and select the partition you prepared. Then choose change and select the mount point as / (for the root partition) and file-system as ext4 (but you don't have to format if you don't want to since you appear to have already created it as ext4). You also need a swap partition of 1.5-2x the amount of RAM. For example, if you have 2GB of RAM, you would make a swap partition of 4GB.

How much space did you devote for the Ubuntu partition? According to fdisk, sda3 is the partition you created? This makes 3 primary partitions already. If you have enough RAM and can live without hibernation, then I suppose you could skip out on creating a swap partition.

---

### Post by Timos798 on 2011-02-27
Don't worry Rubi1200, I'm good enough with computers to know when to make backups, it's just that I had to backup my most important stuff, but I really can't be bothered to re-install all the less important files and such. Also thank you very much for the instructions, sorry to have taken so much of your time :S 
Thank you to everyone who helped me with my predicament, you saved me from going back to Windows :D

---

### Post by Timos798 on 2011-02-27
And I made a 100GB partition for Ubuntu, I think that should be enough, that's just for programs specific to Ubuntu, everything else like .txt files etc I'm putting into my primary partition which is 1.8TB.

---

### Post by Timos798 on 2011-02-27
How do i make a swap partition?!

---

### Post by Rubi1200 on 2011-02-27
If your current setup is what fdisk reported, then I would use GParted from the LiveCD to shrink the Linux partition to then create an extended partition. You could create a swap partition inside the extended partition using GParted. The advantage of doing so before installing is that the installer will use the swap during the install, thus speeding up the process (thanks to Herman for the tip). The rest of the partition will be for Ubuntu and I think 100GB is more than enough for your needs.

In other words, it would look like this:

sda1 Windows primary

sda2 Windows primary

sda3 Linux primary 100GB minus the amount you choose for the extended/swap partition

sda4 extended

sda5 swap

Does this make sense?

If not, don't do anything until you are sure.

I actually have to go now (time zone differences) but here is a great guide to dual-booting:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Timos798 on 2011-02-27
OMG...thanks sooo much guys, I finally installed Ubuntu properly. I think everything is working properly, and thanks again for helping me out guys!

---

### Post by Rubi1200 on 2011-02-28
> **Timos798 said:**
> OMG...thanks sooo much guys, I finally installed Ubuntu properly. I think everything is working properly, and thanks again for helping me out guys!
Excellent! You are more than welcome too :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy, and if you ever need help with anything, feel free to ask.

---

