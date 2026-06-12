---
title: "USB flash drive partitioning question"
date: 2009-12-28
forum: General Help
---

### Post by User0123 on 2009-12-28
I got a shiny new 16gb flash drive for xmas, I decided to install a linux distribution on it, and its quite useful to boot from now and again.

However, Windows wont read the linux filesystem installed on it, so I went ahead and resized a partition to make room for a 6gb FAT32 partition, assuming I could use this as normal for file transfers to and from windows machines, however they don't detect it.

Anyone have any idea what I could do?

Here's a screenshot of the current partitions in Gparted.
[IMG]http://i50.tinypic.com/2visbrb.png[/IMG]

---

### Post by User0123 on 2009-12-28
Is this in the wrong section or something, everyone seems to be ignoring it, no one even viewed my thread yet? ;_;

---

### Post by drdanielfc on 2009-12-28
This is not really a fix, but more of an alternate solution. Would it not be easier to use only 1 partition and then use a tool such as [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) to access your files from windows?

~Dan

---

### Post by User0123 on 2009-12-28
> **drdanielfc said:**
> This is not really a fix, but more of an alternate solution. Would it not be easier to use only 1 partition and then use a tool such as [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) to access your files from windows?

~Dan

Thats interesting and it definitely has some applications where I could make use of it but I need this flash drive for college and such, so I don't think they'd appreciate me installing that.

---

### Post by audiomick on 2009-12-28
Not true, I looked at it about 20 minutes ago, but didn't feel able to help.

However, looking at your picture again, I see that the FAT32  partition is mounted (keys next to it show this).

Is the picture from the gparted live cd, or is Ubuntu booted?

---

### Post by User0123 on 2009-12-28
> **audiomick said:**
> Not true, I looked at it about 20 minutes ago, but didn't feel able to help.

However, looking at your picture again, I see that the FAT32  partition is mounted (keys next to it show this).

Is the picture from the gparted live cd, or is Ubuntu booted?

This is in Ubuntu with gparted installed.

---

### Post by audiomick on 2009-12-28
Then it is mounted in /media
Have you looked there?

---

### Post by drdanielfc on 2009-12-28
Not sure but I believe this is a standalone ([http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)) and just curious can you access the partition from your ubuntu machine?

---

### Post by User0123 on 2009-12-28
> **audiomick said:**
> Then it is mounted in /media
Have you looked there?

I'm sorry I think you have misunderstood me, I have no issues accessing the fat32 partition from linux. And I can boot from the USB drive into the installed distro.

The only other thing I want to do but which I am currently unable to, is to access the fat32 partition from a windows machine.

---

### Post by audiomick on 2009-12-28
> **User0123 said:**
> I'm sorry I think you have misunderstood me, I have no issues accessing the fat32 partition from linux. And I can boot from the USB drive into the installed distro.

The only other thing I want to do but which I am currently unable to, is to access the fat32 partition from a windows machine.

Sorry, didn't read the first post carefully enough.

Are you talking about accessing the partition from a windows install on the same machine (dual boot), or from another machine that is networked to the Ubuntu one?

---

### Post by john newbuntu on 2009-12-28
Did you flip the removable bit on the disk when you created the partitions on USB flash drive on this computer?

---

### Post by User0123 on 2009-12-28
> **drdanielfc said:**
> Not sure but I believe this is a standalone ([http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)) and just curious can you access the partition from your ubuntu machine?

Yes, just to clear things up I have no problems accessing any partition from my Ubuntu or other linux machines.

The problem lies when I plug the flash drive into a windows machine. The flash drive appears as Removeable Disk (E:) in "My Computer". If I double click it I am asked whether I want to format it. And if I right click on it and go to properties, It shows Used Space: 0 bytes, Free Space: 0 bytes, File System: RAW

---

### Post by User0123 on 2009-12-28
> **audiomick said:**
> Sorry, didn't read the first post carefully enough.

Are you talking about accessing the partition from a windows install on the same machine (dual boot), or from another machine that is networked to the Ubuntu one?

Tried on all of my windows machines, Dual boot, Virtual Boxs, and my XP installed netbook.

---

### Post by User0123 on 2009-12-28
> **john newbuntu said:**
> Did you flip the removable bit on the disk when you created the partitions on USB flash drive on this computer?


Can you elaborate on that, please? I'm not sure what you mean.

---

### Post by audiomick on 2009-12-28
Beginning to understand, finally...:)

The windows machines are not dealing with the ext2 partition, obviously.

You could try putting the FAT32 partition at the front of the USB drive, although that is just a guess.

The simplest path would be to just use FAT32 partition(s). Your Linux machines will all be able to read them.

The next thing would be to try one of the Ext2 file reading applications in the links that have been posted. I had one, ext2FS, I think, running on my old laptop. It worked well for the partitions on the HD, but I never tried it on a flash drive.

---

### Post by User0123 on 2009-12-28
> **audiomick said:**
> Beginning to understand, finally...:)

The windows machines are not dealing with the ext2 partition, obviously.

You could try putting the FAT32 partition at the front of the USB drive, although that is just a guess.

The simplest path would be to just use FAT32 partition(s). Your Linux machines will all be able to read them.

The next thing would be to try one of the Ext2 file reading applications in the links that have been posted. I had one, ext2FS, I think, running on my old laptop. It worked well for the partitions on the HD, but I never tried it on a flash drive.

Right I'll try putting the FAT32 partition at the front.

If I did just use FAT32 partitions I know my linux machines can read them with no problems, but I need to boot from this flash drive (it has a linux distro installed to it).

---

### Post by User0123 on 2009-12-28
Tried putting the FAT32 partition at the front but that hasn't changed anything

Its almost as if having the not FAT partitions make the whole drive unusable for windows?

---

### Post by drdanielfc on 2009-12-28
What about using ntfs?

---

### Post by User0123 on 2009-12-28
> **drdanielfc said:**
> What about using ntfs?


Just attempted this, still not recognized by windows. Has anyone ever done this before? Having a bootable system on the flash drive as well as having a partition that can be used by windows for normal flash drive use?

Is what I am attempting even feasible?

---

### Post by drdanielfc on 2009-12-28
> **User0123 said:**
> Just attempted this, still not recognized by windows. Has anyone ever done this before? Having a bootable system on the flash drive as well as having a partition that can be used by windows for normal flash drive use?

Is what I am attempting even feasible?

Never done this as I have never found the need

---

### Post by User0123 on 2009-12-28
> **drdanielfc said:**
> Never done this as I have never found the need

Yeah. It's just that since I have one 16gb flash drive I would like to use it for multiple things, I don't need to carry 16gb of files with me, but carrying a *nix based O/S and then some files too is much more useful.

---

### Post by User0123 on 2009-12-28
Hmm not sure what to do now >_<

Should I forget about having a USB install'd linux distro even though thats working fine.

or should I just format the whole thing and use it as a normal usb stick?

---

### Post by User0123 on 2009-12-28
I still don't understand why this wont work.

---

### Post by drdanielfc on 2009-12-28
Why not format the usb drive as ntfs and then use it for storage but use a live disk when needed?

---

### Post by audiomick on 2009-12-28
> **User0123 said:**
> I still don't understand why this wont work.

I think it goes back to MS refusing to acknowledge that there are other OSs in the world. The "foreign" file system just freaks out the windows and that, said john, is that.

I had hoped that the FAT partition on the front of the drive might have fooled windows into just seeing a smaller drive; pity it didn't work.

---

### Post by User0123 on 2009-12-28
> **drdanielfc said:**
> Why not format the usb drive as ntfs and then use it for storage but use a live disk when needed?

Because I use this USB as a persistant install not a live distro, and furthermore, I use it on my netbook quite a lot, netbooks don't like CDs / DVDs

---

### Post by User0123 on 2009-12-28
> **audiomick said:**
> I think it goes back to MS refusing to acknowledge that there are other OSs in the world. The "foreign" file system just freaks out the windows and that, said john, is that.

I had hoped that the FAT partition on the front of the drive might have fooled windows into just seeing a smaller drive; pity it didn't work.

Yeah thats exactly what I wanted it to do, just see it as a flash drive and ignore the other partitions

---

### Post by User0123 on 2009-12-28
Man this sucks, if I had known that it would have been impossible for me to use this 16gb flash drive like this I would have asked for 4 x 4gb ones!

---

### Post by drdanielfc on 2009-12-28
> **User0123 said:**
> Man this sucks, if I had known that it would have been impossible for me to use this 16gb flash drive like this I would have asked for 4 x 4gb ones!

Did you attempt using the standalone ext3 reader i posted in a link above?

---

### Post by falconindy on 2009-12-28
Do not use ext3 for a flash drive. You're causing unnecessary writes to the drive and shortening the lifespan. Use a journal-less filesystem such as Ext2.

---

### Post by Herman on 2009-12-28
It's a myth that ext3 or ext4 wears out flash memory.

Well, file system journaling might cause a tiny wee amount of extra wear but it's probably almost negligible. Anyway it's probably worth accepting because with journaling, if somebody rips your USB out suddenly or the power goes off, you can just run a file system check and recover your files, whereas without journaling, file recovery might be more difficult. For a most people, files are worth more than the cost of replacing the drive.
 
Another thing a lot of people keep forgetting is that most modern flash memory sticks use wear levelling, so your journal writes are not all occurring in the same physical location in the flash memory, (where the file system journal is), like some scare-mongers like to imply. The wear is spread out evenly around the whole device. 
That depends on the make and model of flash memory you bought though, some are more efficient at spreading wear than others. Some flash memory manufacturers have invested a lot of money on scientific research and engineering to design wear levelling controllers that work well without compromising on the speed of disk writes, others may be slowed down but have a longer life expectancy, and so on.
The purchase price is not always an indication of quality either, it's up to the buyer to try to get information about the hardware before purchasing.
In most cases a modern flash memory device will last a lot longer than a hard disk of the same size.

I don't know why your Windows can't mount your FAT32 partition either though, it should be able to.

---

### Post by john newbuntu on 2009-12-28
Take a look at this.  They do say that it may not work on all flash drives though:
[http://www.pendrivelinux.com/sharing-files-between-windows-and-linux/](http://www.pendrivelinux.com/sharing-files-between-windows-and-linux/)

---

### Post by craftomaniac on 2009-12-29
Hello there.

I've had similar experiences and it seems that it's not that Windows hates ext3 / ext4, it's just that Windows will detect the flash drive as a removable drive, and thus only mount one partition (the first one).

To make it mount both, try [http://www.lancelhoff.com/multi-partition-a-usb-flash-drive-in-windows/](http://www.lancelhoff.com/multi-partition-a-usb-flash-drive-in-windows/) (the Lexar BootIt utility). I don't know if it will work for your USB drive as it's a Lexar product. Might be risky to use it on a non-Lexar product, but I don't know. I'm still trying to find a Linux way of doing that but haven't found one yet. Maybe fdisk or some other low level tool would have that ability.

Take note that making the drive non-removable would make Windows treat it dumbly and non-hot-removable so you have to Safely Remove it every time.

Good luck.

Actually, you can try switching the partitions. Create your 6GB fat32 partition BEFORE the ext3 partition, and make the ext3 partition bootable. I'm not really sure if it will boot that way though. You could always try.

---

### Post by garvinrick4 on 2009-12-29
This below is a 16 gig flash drive  partitioned with gparted in ext3 with sdb1 as /boot and sdb2 as /root and sdb3 as swap. Page 8 in gparted click advanced and put boot in sdb1 same as your boot originally sdb1. No extended partition just as it looks.  Works as complete system with 100% persistence.  Tried a lot of ways and only way it worked with full persistence was using gparted as partition software. Use manual of course and select your USB device and focus on task at hand. Took installation using 64 bit Live CD of 9.10. Choose install Ubuntu and when partitioning started used thid method. Worked and after 20 different tries I was surprised when it booted and worked. It is now a nice 9.10 Karmic Operating System on a 16 Gig Flash drive.

You will notice the flash on bottom of my  fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.7 GB, 16687038464 bytes
64 heads, 32 sectors/track, 15914 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0008849e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         954      976880   83  Linux
/dev/sdb2            3831       15914    12374016   83  Linux
/dev/sdb3             956        3830     2944000   82  Linux swap / Solaris
                                                                                               __________________

---

### Post by Fcon_Vpro on 2009-12-29
Did you just install the ubuntu ISO/live-cd to your flashdrive or did you actually do an install to your flash drive? (Lol I hope that makes sense)

What I would recommend you do is format the drive in windows and create the storage partition there. Then get linux to create the other partition you need for booting. There shouldnt be any problems from there.

---

### Post by garvinrick4 on 2009-12-29
I use a Live CD burned from a 64 bit Ubuntu download. Went through like a normal install to hard disk but choose flash drive device and made a boot/ a root/ and a swap. 
 Would like to use Flash drive to use for Alpha and Beta installs of the next Ubuntu version in future and Let my friends and family to use who are Microsoft users to get them to see what Ubuntu looks and feels like in full bloom and not the Live CD look. Anyway to answer your question a put flash in to USB port then unmounted it when it came up. Put Live CD in tray and then started regular install but choosing Flash drive device in gparted. As you see in fdisk all three partitions say Linux and used ext3. and has /boot in first partition.
 Once it has booted you can see all partitions Windows OS and the 2 other Linux partitions I have. If I reboot it will go to grub and I can pick another OS to boot and I can mount any of the other OS's to exchange files. There is no reason to have it mount for any other reason it is now
a OS not a Flash drive. Designed to be mobile with a Linux OS. Does not write over Windows dos4grub will just make a grub2 if you sudo update-grub. Grub 2 is superior to the Windows grub if you ask me but that is personal opinion. Many articles on how to work with grub2, dual boots and triple boots using all the OS's. I was surprised as anyone when I made one with full persistence of 16 gig to tell you the truth, but what works, works. Use it if you choose, make your USB boot 2nd behind CD and disk drive 3rd.  Always leave CD on first boot for the emergency Live CD repair. And enjoy your Flash drive.

---

### Post by User0123 on 2009-12-29
I managed to get it working finally!

First I created the 6gb FAT32 partition I wanted to use for everyday file transfers, then partitioned the remainder of the space on the flash drive so that it could be booted from.

Now I can both boot from it, and use the 6gb storage across different O/S :D

---

### Post by bemental on 2010-01-23
Still working on my forum skills, accidently posted twice :confused:

---

### Post by bemental on 2010-01-23
> **User0123 said:**
> I managed to get it working finally!

First I created the 6gb FAT32 partition I wanted to use for everyday file transfers, then partitioned the remainder of the space on the flash drive so that it could be booted from.

Now I can both boot from it, and use the 6gb storage across different O/S :D
User0123; I've been having this exact same problem and wouldn't mind a little clarification if you'd be willing?

I assume you started your whole process over and used gparted to create the fat32 partition on your drive. Then booted up a live CD (or similar Ubuntu install) and used the bootable USB tool to crate the ext partition and install Ubuntu to the USB drive, correct?

Currently, my USB thumbdrive (16GB) works perfectly on other Linux installs, partially on my OS X machine, and only as a bootable device on a windows box. I understand the lack of functionality in OS X and am alright for now not being able to access the ext partition being I don't plan to use it for anything other then to backup what's on the fat32 partition. The lack of windows functionality is what is bothering me (since I as you would like access to the fat32 partition on the device too).

My overall plan is like yours, to be able to boot a permanent 9.10 Karmic install (which it currently does fine) when I want as well as being able to plug the drive into a computer running windows and access the fat32 partition as a normal removable media storage device. I keep a few portable apps on it for use on public computers short term when I don't need to boot up 9.10.

Thanks again in advance for the help!
andrew

---

### Post by bemental on 2010-01-27
Managed to get this working & here's how for anyone else who is interested.

Wiped the flash drive completely.  Booted up a computer with a 9.10 live cd.

Partitioned with Gparted.  Two partitions, both primary.  FAT32 at the begining, EXT3 at the end (5GB FAT, 11GB EXT3).  No swap (USB wear&tear)

Installed via the livecd directly to the USB flash drive.  ENSURED GRUB WAS INSTALLED ON THE FLASH DRIVE, and not the computer.

Rebooted.  Perfection.

Resources; both curtosey of a computer science professor from the University of Alabama:

[USB Install Instructions]("http://beastie.cs.ua.edu/cs150/usb-install.html")
[USB Configuration Instructions]("http://beastie.cs.ua.edu/cs150/configuration.html")
-----

Now, all I need to do is figure out how to load the majority of the system into a RAM drive on the host computer to increase speed even more!

---

---

