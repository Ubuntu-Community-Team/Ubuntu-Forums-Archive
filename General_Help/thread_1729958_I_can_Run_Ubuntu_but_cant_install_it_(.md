---
title: "I can Run Ubuntu but cant install it :("
date: 2011-04-15
forum: General Help
---

### Post by tunechi on 2011-04-15
i download ubuntu netbook 10.10 and used the usb installation thing , then i booted my laptop with the usb and it all worked fine. I runed ubuntu and it worked its amazing and fast. now when i click to install i used a partial drive on my harddrive which is D; drive it empty then  i fill out everything out and wait for the installation to finish , eventually at the end of i think it was " copying system file " or something like that , with "system" it crashes  and say please report this bug and attach the file var/.... anyways how can i get it to work ???

thanks

---

### Post by Rubi1200 on 2011-04-15
Hi and welcome to the forums :-)

On the LiveUSB, go to Applications > Accessories > Terminal and run this command:

```
sudo fdisk -l
```(lowercase L not 1)

Copy/paste the output back here in a new post.

Also, post the full specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by tunechi on 2011-04-16
this is my computer 
"
[B]Toshiba  Satellite L305-S5902 15.4-Inch Laptop (2.0 GHz Intel Pentium Dual Core  T3200 Processor, 2 GB RAM, 160 GB Hard Drive, DVD Drive, Vista Premium)" 
[/B]

[http://www.amazon.com/Toshiba-Satellite-L305-S5902-15-4-Inch-Processor/dp/B001HAO4OU](http://www.amazon.com/Toshiba-Satellite-L305-S5902-15-4-Inch-Processor/dp/B001HAO4OU)

**Product Features and Technical Details**

           **Product Features**

 
[LIST]
[*]15.4-inch (Diagonal) Widescreen TruBrite TFT LCD Display, 1280x800 Resolution
[*]2.0 GHz Intel Pentium Dual Core Processor with 1MB L2 Cache
[*]2048MB DDR2 System Memory, 160GB (5400 RPM) Hard Drive, Mobile Intel Graphics Media Accelerator 4500M
[*]DVD SuperMulti with Labelflash, Atheros 802.11 b/g wireless-LAN
[*]Windows Vista Home Premium, dims in inches: 10.6 (W) x 14.3 (D) x 1.3 (H) approx., 5.49 lbs.
[/LIST]
                **                 Processor, Memory, and Motherboard               **
                            
[LIST]
[*]**Hardware Platform:** PC
[*]**Number of Processors:** 2
[*]**RAM:** 2000 MB
[*]**RAM Type:** DDR2 SDRAM
[/LIST]
                            **                 Hard Drive               **
                            
[LIST]
[*]**Size:** 160 GB
[*]**Type:** Serial ATA
[/LIST]
                            [B]

FOR THE LOG here it is :
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c8e27df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              14        6486    51992577    f  W95 Ext'd (LBA)
/dev/sda3            6486       12972    52094976    7  HPFS/NTFS
/dev/sda4           12972       19458    52096000    7  HPFS/NTFS
/dev/sda5              14        6486    51992576    7  HPFS/NTFS

Disk /dev/sdc: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders
Units = cylinders of 735 * 512 = 376320 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       21270     7816688    b  W95 FAT32


THANK YOU VERY MUCH
[/B]

---

### Post by Rubi1200 on 2011-04-16
Thanks for the info. Did you happen to find/save the information from the log that you mentioned in your first post?

The specifications look good, so I don't believe that is the problem.

I would check the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by tunechi on 2011-04-17
> **Rubi1200 said:**
> Thanks for the info. Did you happen to find/save the information from the log that you mentioned in your first post?

The specifications look good, so I don't believe that is the problem.

I would check the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


ok the result is "MD5 Check Sums are the same."  , btw when i install it on my hard drive , i select a portion and change it to extr3 or something like that right ?

do i format then reinstall ubuntu or what do i do , i rly need it ](*,)

thanks

---

### Post by Rubi1200 on 2011-04-17
This guide should get you going:
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

Please read it carefully and if you have any questions ask before starting.

3 tips before you start:

1. make backups

2. create a Windows recovery disk if you don't already have one

3. use manual partitioning and the default file-system which is ext4

---

### Post by tunechi on 2011-04-19
> **Rubi1200 said:**
> This guide should get you going:
[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")

Please read it carefully and if you have any questions ask before starting.

3 tips before you start:

1. make backups

2. create a Windows recovery disk if you don't already have one

3. use manual partitioning and the default file-system which is ext4

hi , FINALLY IT WORKED , AND INSTALLED correctly:P , NOW i still have a problem](*,)when i boot , i get a black screen with "-" blinking , thats it :( , i tried to boot to recovery mood and it worked . How can i fix that ?

---

### Post by tunechi on 2011-04-19
> **Rubi1200 said:**
> This guide should get you going:
[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")

Please read it carefully and if you have any questions ask before starting.

3 tips before you start:

1. make backups

2. create a Windows recovery disk if you don't already have one

3. use manual partitioning and the default file-system which is ext4

lol , i just got it to work , now it is kinda slow at the beginning but now its better , how can i configurate it , and let it not ask for the username and password ?

thank you very much

---

