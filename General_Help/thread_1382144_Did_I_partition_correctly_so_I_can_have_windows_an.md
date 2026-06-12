---
title: "Did I partition correctly so I can have windows and ubuntu?"
date: 2010-01-15
forum: General Help
---

### Post by cscott5288 on 2010-01-15
OK, so I just bought a new hard drive and I wanted to create two partitions. One for windows and one for ubuntu. I created a 200GB ext3 file system for ubuntu and a 110GB FAT32 for windows. I also created a 2GB swap partition (my ram is 2GB). 

For the mount point, I selected "/" for the ubuntu partition and "/windows" for the windows partition. I now see (inside of my installed ubuntu) that I have a folder in Computer --> Filesystem named "windows" that is 110GB in size ... but why would it be a folder if it is a seperate partition? Shouldn't it be recognized as an entirely seperate drive altogether and show up under "Places"? 

I guess my main question is -- did I do this right? I can in fact install windows in that folder I created and boot it right? 

Thanks ahead! And please dumb things down a bit for me because I know how technical some of the answers can get on this forum.

---

### Post by howefield on 2010-01-15
Can you open a terminal (Applications > Accessories > Terminal) and type

```
sudo fdisk -l
```

Enter your password when prompted and post the output back here ?

(Although it might look like a number ONE, that command ends with a lower case L)

---

### Post by audiomick on 2010-01-15
Hi.
The windows folder you are seeing is probably the partition you think it is. When you mount a partition within your file system somewhere, it shows up as a folder. Do what howefield asked for, and post the output of that command here.

---

### Post by louieb on 2010-01-15
:D [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm") - Partitions are accessed via whatever folder/directory they are mounted on.  (Even if the partition is really on another hdd). 
> I can in fact install windows in that folder I created and boot it right? 

Depends what version of Windows? For XP and later NTFS would have been a better choice. 

Once you install windows its boot-loader will overwrite the MBR  and you will have to reinstall GRUB in order to dual boot.

---

### Post by Ugluk on 2010-01-15
You should convert Windows partition to NTFS filesystem, because it's security depends on it.
Also note, that your first partition should have FAT or NTFS filesystem if you intend to install Vista on it.

---

### Post by cscott5288 on 2010-01-15
> **howefield said:**
> Can you open a terminal (Applications > Accessories > Terminal) and type

```
sudo fdisk -l
```Enter your password when prompted and post the output back here ?

(Although it might look like a number ONE, that command ends with a lower case L)
OK, here is what is says:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078a5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24315   195310206   83  Linux
/dev/sda2           24316       24558     1951897+  82  Linux swap / Solaris
/dev/sda3           24559       38913   115306537+   b  W95 FAT32

I chose FAT32 for windows because there was no option for NTFS (I am using a 9.04 ubuntu install disc). I am surprised there is not an option in the ubuntu partitioner. Is it difficult/risky to convert FAT32 to NTFS? Because I will be using windows XP or higher.

---

### Post by howefield on 2010-01-15
Looks fine, your windows partition is on a primary partition which is what it needs to be, but as others have said, NTFS would be a better choice, however you can choose to change the file system and format to ntfs during the windows install.

The downside to installing Ubuntu first and then Windows is that grub is a goner, you will need to rectify that after the Windows installation.

---

### Post by cscott5288 on 2010-01-15
> **howefield said:**
> Looks fine, your windows partition is on a primary partition which is what it needs to be, but as others have said, NTFS would be a better choice, however you can choose to change the file system and format to ntfs during the windows install.

The downside to installing Ubuntu first and then Windows is that grub is a goner, you will need to rectify that after the Windows installation.
Well, i don't have a windows disc now, I was just thinking in the future. 

So what does GRUB do exactly and why can't I have it? lol 

When I do install windows, will I be able to chose, on start-up, which partition I want to boot from? If not, how will I get into my windows installation? lol, forgive me if these are very newbish sounding questions.

---

### Post by audiomick on 2010-01-15
Grub is the boot loader. It administers the various OSs on the machine at boot time, i.e. allows you to choose which system to boot into. If you only have one OS installed, you hardly notice it.

The problem with installing windows after a linux system is that windows aims for world domination in that it assumes that it will be the only system on the computer and overwrites the master boot record. A linux installation generally has a look to see if there is another OS on the machine already, and tries to include it in the boot loader.

When you install windows, it will not remove the Ubuntu installation unless you tell it to overwrite that partition during the installation, but you will only be able to boot windows afterwards.

To regain access to your Ubuntu, you will have to re-install Grub. It is no big deal. If you are using 9.10, it will be grub2. There are instructions for re-installing here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If it is an older Ubuntu, it will have grub legacy. Instructions here
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by howefield on 2010-01-15
> **cscott5288 said:**
> Well, i don't have a windows disc now, I was just thinking in the future.

OK, well, you're good to go when you do :) 

> So what does GRUB do exactly and why can't I have it?

It is a boot manager and if you have more than one operating system on your computer, it allows you to select which one to boot. You do have it currently but the problem is that windows doesn't play nice with other operating systems and tends to think it should be all by itself on your computer so it deletes grub and installs it's own bootloader, from which you will only be able to select windows.

Grub however, does play nice with other operating systems, detecting them and giving you the choice of which you want to boot, this is why it is easier to install windows first, and then Ubuntu. 

> When I do install windows, will I be able to chose, on start-up, which partition I want to boot from? If not, how will I get into my windows installation?

If the sentences above make any sense, you will now realise that you will get into your windows system, just not Ubuntu. (until you reinstall Grub, at that point you have the choice of both).

---

### Post by cscott5288 on 2010-01-15
> **audiomick said:**
> Grub is the boot loader. It administers the various OSs on the machine at boot time, i.e. allows you to choose which system to boot into. If you only have one OS installed, you hardly notice it.

The problem with installing windows after a linux system is that windows aims for world domination in that it assumes that it will be the only system on the computer and overwrites the master boot record. A linux installation generally has a look to see if there is another OS on the machine already, and tries to include it in the boot loader.

When you install windows, it will not remove the Ubuntu installation unless you tell it to overwrite that partition during the installation, but you will only be able to boot windows afterwards.

To regain access to your Ubuntu, you will have to re-install Grub. It is no big deal. If you are using 9.10, it will be grub2. There are instructions for re-installing here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If it is an older Ubuntu, it will have grub legacy. Instructions here
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

> **howefield said:**
> OK, well, you're good to go when you do :) 



It is a boot manager and if you have more than one operating system on your computer, it allows you to select which one to boot. You do have it currently but the problem is that windows doesn't play nice with other operating systems and tends to think it should be all by itself on your computer so it deletes grub and installs it's own bootloader, from which you will only be able to select windows.

Grub however, does play nice with other operating systems, detecting them and giving you the choice of which you want to boot, this is why it is easier to install windows first, and then Ubuntu. 



If the sentences above make any sense, you will now realise that you will get into your windows system, just not Ubuntu. (until you reinstall Grub, at that point you have the choice of both).

Ah, ok, thanks for explaining it sesame street style. I understand now. I have ubuntu 9.10. I guess I will have to re-install grub after installing windows. 

One more question however - the partition I want windows on is a FAT32. If I format it to NTFS for XP, is there a possibility I could ruin my hard drive by creating bad sectors? My last hard drive got bad sectors after I re-formated it -- that's why I ask. 

Thanks again.

---

### Post by louieb on 2010-01-15
> **cscott5288 said:**
> ... If I format it to NTFS for XP, is there a possibility I could ruin my hard drive by creating bad sectors? 

Not a problem - All the format program does is write stuff to the drive.  Much the same way installing a program or copying a music CD writes stuff to the hdd.

---

### Post by miegiel on 2010-01-15
> **cscott5288 said:**
> Ah, ok, thanks for explaining it sesame street style. I understand now. I have ubuntu 9.10. I guess I will have to re-install grub after installing windows. 

One more question however - the partition I want windows on is a FAT32. If I format it to NTFS for XP, is there a possibility I could ruin my hard drive by creating bad sectors? My last hard drive got bad sectors after I re-formated it -- that's why I ask. 

Thanks again.

Your last hard drive probably already had bad sectors. Bad sectors are normally caused by bumping the drive while it's reading/writing, reckless transport or old age. But the bad sectors are often only discovered when the drive is checked, even a format can gloss over them.

---

