---
title: "Anything I should know about Ubuntu and this set up?"
date: 2011-04-20
forum: General Help
---

### Post by alphaamanitin on 2011-04-20
Hey guys, 

Not new to Ubuntu but have built a new computer, or will tomorrow, anything I should know about amd64 Ubuntu and this set up:

Phenom II x6 3.3ghz 1100T Black Edition Thuban
16 gb (4x4gb) G.Skill Ripjaw series 1333 mhz ram
ASRock 880G Pro3 MOBO AM3+ Socket support
Asus EAH6850 GPU
Crucial 64 gb 2.5" SSD (intend to give Ubuntu half or less for is root and put /home on HD listed below, the rest will go for Windows 7 Ultimate 64-bit)
2TB Seagate Barracuda 7200 RPM SATA III HD


Just to let you know the rest:
Case:
AZZA Solano 1000 Full ATX Case
Koutec IO-RCM621 All-in-one USB 2.0 3.5" card reader
Sony DVD/CD +/- ROM


I might buy another 2 TB HD sometime soon so I have 2TB storage in NTFS for Windows and 2 TB storage for Ubuntu.  Then again, I have never had a problem with Ubuntu messing up NTFS, how common do you guys think it is?  I would put the /home partition of Ubuntu in ext4 though, or just buy a smaller SATA III drive for the /home itself.  


Thoughts guys?  Words of wisdom/warning?

Thanks,

AlphaA

---

### Post by blueridgedog on 2011-04-20
Nothing out of the ordinary from me.  Install 64 bit, put windows on first.

---

### Post by oldfred on 2011-04-21
It looks like your motherboard is UEFI. That works in win7 64 bit. Grub2 is just starting to work with Natty.

Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

Win7 64 bit only works with gpt if UEFI booting.
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

Windows 7 64bit UEFI 2.x boot:
[http://www.insanelymac.com/forum/index.php?showtopic=186440](http://www.insanelymac.com/forum/index.php?showtopic=186440)
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)

MaverickUefiSupport - Cd may not work, need USB 
[https://wiki.ubuntu.com/FoundationsTeam/Specs/MaverickUefiSupport](https://wiki.ubuntu.com/FoundationsTeam/Specs/MaverickUefiSupport)

Not just info on Macs
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
UEFI issues srs5694 post #58
[http://ubuntuforums.org/showthread.php?t=1719851&page=6](http://ubuntuforums.org/showthread.php?t=1719851&page=6)
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
[https://bbs.archlinux.org/viewtopic.php?pid=910369#p910369](https://bbs.archlinux.org/viewtopic.php?pid=910369#p910369)
[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
[https://github.com/skodabenz/Misc_Linux_Shell_scripts/blob/master/grub2/grub2_efi.sh](https://github.com/skodabenz/Misc_Linux_Shell_scripts/blob/master/grub2/grub2_efi.sh)
EFI System Partition Subdirectory Registry
[http://www.uefi.org/specs/esp_registry](http://www.uefi.org/specs/esp_registry)
All linux distro installers (Ubuntu included) assume EFISYS partition to be mounted at /boot/efi.

---

### Post by srs5694 on 2011-04-21
Oldfred has provided you with a lot of useful links. It's worth reading them; but to give you an overview: Because you've got a UEFI board, your system will necessarily boot in an entirely different way than would a BIOS-based system, and Windows *must* use GPT partitions on a UEFI system, so you must use GPT (at least on the Windows boot drive) rather than MBR. These aren't disadvantages, really, over BIOS, but they are different, and the differences can bite you if you go at it in the usual way you'd install on a BIOS-based system. Some specific points:


[list]
[*]Use Ubuntu 11.04, even if you have to install the beta; AFAIK, earlier versions lack the ability to boot the installer on UEFI.
[*]Install the 64-bit version, not the 32-bit version; the 32-bit version's installer might not boot, and even if it does, there are said to be limitations when running a 32-bit kernel on a 64-bit UEFI. (I'm a bit foggy about how important these are, though, so I can't elaborate on this point.) You'll also need to install the 64-bit version of Windows, BTW.
[*]Partition using GParted or gdisk in the Ubuntu installer disc: Create a 100-200 MiB (note MiB, not GiB) EFI System Partition, a 128 MiB Microsoft Reserved partition, and whatever partitions you want for Windows and Linux, as per the [Microsoft document](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx) that oldfred referenced.
[*]Install Linux first (*not* Windows, as is advisable on BIOS-based systems). Install Windows last. The reason for this order is that the Ubuntu installer, at least according to reports from one beta user, wipes the EFI System Partition clean, and with it wipes out the Windows boot loader, when it installs. This renders Windows unable to install. Installing in the other order *should* work better, but few enough people have done this that I can't be positive of that.
[*]Read over the GRUB [Testing on UEFI](http://grub.enbug.org/TestingOnUEFI) page (the name's changed from what oldfred provided). It talks about building GRUB for EFI from scratch, so much of that procedure might not be applicable; but there was a thread here recently started by somebody who installed to a UEFI system, and as I recall, he ended up having to build GRUB from scratch to get things working correctly. (I might be disremembering, though. I think it was [this thread,](http://ubuntuforums.org/showthread.php?t=1719851&highlight=uefi) but I'm not positive. It's a monster 10-page thread and the fact that the system used UEFI didn't emerge until at least halfway through it, so there's a lot of bad BIOS-based advice before [and even after] then.)
[/list]


The special issues you'll encounter are all related to booting and installation, AFAIK; once the system is up and running, you'll have no special problems. I do recommend, though, backing up the contents of the EFI System Partition (mounted at /boot/efi by default) and of the entire /boot directory. That way, if a system update tries to upgrade a modified GRUB configuration and gets it wrong, you'll have something you can restore that should work.

Incidentally, in case you're thinking this  UEFI thing isn't worth the bother, know this: Windows requires an MBR disk to boot from in BIOS mode, and MBR is limited to 2 TiB. Thus, you can't boot Windows from a larger disk if you use BIOS. (There are some workarounds, but they've got their own problems and limitations.) In other words, UEFI "future-proofs" the Windows side of your installation, in terms of hard disk size. At this point, I wouldn't recommend buying a BIOS-based computer if it's to run Windows for this reason.

You also asked about NTFS. Ubuntu's NTFS support seems anecdotally to be pretty good; however, it's slower than Linux-native filesystems, and it's even slower than FAT. I also find it hard to believe that it's as reliable as Microsoft's NTFS support. Thus, I strongly recommend against using Ubuntu's NTFS support to read, or especially to write, your Windows C: partition. Use a separate data-exchange partition. If you expect to need to access most of your files from both OSes, then this might be the bulk of your storage space. If not, though, using a Linux-native filesystem (probably ext4fs) for storing your Linux-only files makes sense. If you don't need to store files larger than 4 GiB, using FAT rather than NTFS makes sense; FAT is faster under Linux and Linux provides decent FAT filesystem maintenance tools, unlike for NTFS. That 4 GiB limit of FAT can be a real pain if you plan to store big audio-visual or backup files, though.

---

### Post by alphaamanitin on 2011-04-21
Thanks for all the great replies guys.  I don't know if I am ready to mess around with beta versions.  Maybe I'll just wait until it comes out in a few days.  Though I hate the new Unity look, I'm sure there will be a gnome version though by some one.  Also, what about using lilo?  I see Archlinux says that GRUB2 officially supports booting from UEFI boards.  

Unfortunately, when I bought this MOBO it didn't say anything about UEFI so I thought it was BIOS.  I should have done more research, but it seemed like a good deal.  I think I'll look around to find a very clear walkthrough for the install.  

Thanks guys,

AlphaA

---

### Post by oldfred on 2011-04-21
I tried Unity for a bit, and may eventually use it on my laptop as it is wide screen. But my desktop has a 4:3 monitor and having the bar on the left makes no sense, top & bottom are where I have extra room. 

With Natty, I changed to gnome, on selection at login screen & it has booted to gnome ever since.

---

### Post by alphaamanitin on 2011-04-21
I should have thought of this earlier but I can do a seamless upgrade from 11.04 beta to 11.04 without having to reinstall can't I?  Is this recommended?  I kind of regret my UEFI purchase now, but I am going to make it work one way or another.

AlphaA

---

### Post by oldfred on 2011-04-21
You should be able to continue to upgrade. I usually do a clean install, just to make sure I have housecleaned out all old stuff, but updating works. With larger drives I create several / (root) partitions of 25GB and test installs and keep older versions, so I know I can boot something.

I wanted to purchase a EFI system when I build this one several years ago. But then they only had server boards for several thousands $. I was a lot ahead of the curve. You are just on the brink of all new systems using UEFI and might regret having BIOS a year or two from now.

---

### Post by blueridgedog on 2011-04-21
Mac users have been dealing with this for a bit.  It sounds more complex than it is in reality (I am multi-booting my macbook pro).  The movement away from mbr is a blessing.

---

### Post by srs5694 on 2011-04-21
> **oldfred said:**
> You are just on the brink of all new systems using UEFI and might regret having BIOS a year or two from now.

I agree. Given Windows' inability to boot on >2TiB drives on BIOS-based systems, and given that Microsoft, by all accounts, seems uninterested in fixing this flaw, I expect there'll be a lot of frustration in a year or two among Windows users with BIOS-based systems. Of course, if you regularly replace your computer every two years or so, this might not matter; but as I wrote above, UEFI at this point is a future-proofing technology. OTOH, you can't boot Windows XP or earlier on these boards, but you can certainly run such OSes in a virtual machine -- they have their own "firmware" that can be of a different type than that on the real computer.

---

### Post by ChrisWells on 2011-04-21
Don't forget to add discard to fstab for auto-trim for the SSD

---

### Post by alphaamanitin on 2011-04-22
> **ChrisWells said:**
> Don't forget to add discard to fstab for auto-trim for the SSD


Uh, what?  I know fstab, but auto-trim?  

I think that buying a UEFI board was a good idea for me in the future.  I do not replace my computer regularly.  This is the first new desktop I have had in 6 years, and my laptop is 3 years old or so.  

I just wanted to get up and running immediately and I knew how to do a dual install of Windows and Ubuntu in BIOS without a problem.  Now I have to relearn things and I don't have lots of free time.  I am a PhD graduate student in a molecular biology lab studying the Fungi group Boletineae, and a couple species in the Sclreodermatineae (both in the Order Boletales).  I want to use this new computer with 16 gigs of ram for MAFTT and RAxML among some custom perl scripts for phylogenetic analysis.  

Thanks guys.  I love this forum, quick, great info, and friendly.

AlphaA

---

### Post by alphaamanitin on 2011-04-23
Okay, have built computer things look great.  So,  I am confused and need help with the install.  I know I should install Ubuntu first, but windows wants things set up a certain way.  So I booted into the livecd of Ubuntu 11.04beta AMD64 opened gparted and did this to my boot drive, which is actually because of the way I installed it, sdb (problem?):

Partition 1-100MB-label EFI, Format FAT32
Partition 2-128MB-label MSR, Format, Unformatted
Partition 3-30000MB-Label Ubuntu, Format ext4
Partition 4-30000MB-Label Windows, Format NTFS

That is exactly how this website says to do it [http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx) thanks for that link btw.

Well, exactly minus the spitting of the rest of the drive.  But, now I am lost.  I go to install from the livecd, select the drive and don't know what do to from there.  I think Partition 4 should be mounted at / right?  What about swap?  What do I do with partitions 1 and 2?  I want to mount my home on a separate regular HD (sda).  BTW I will need to make sda have three partitions.  Currently it is a 2TB drive split into half, 1/2 NTFS 1/2 ext4.  

Hope to hear some feed back soon guys.  I would really like to set this computer up tomorrow and sunday and get everything going.  

Oh, I did use GTP partition table for both sda and sdb.  

Thanks a bunch guys,

AlphaA

---

### Post by oldfred on 2011-04-23
The 100MB for the efi may be a little small. That is windows suggestion for just windows. My notes thought say 100 to 200 is suggested. So it may be ok.

Some say you do not need swap if you have lots of RAM. Others suggest you have some swap anyway like 2GB, others says use a swap file. And if hibernating you need swap = RAM.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Are you keeping /home inside your 30GB root since you will be storing data in all your other partitions? Or are you creating another ext3 or ext4 partition just for Linux data? I also like to have several extra / (root) partitions for testing beta or other systems. And you do not have to fully partition system if you are not sure about how much data your will have. Of course it is a trade off if you have too many small partitions. Very large partitions are hard to backup, run chkdsk/e2fsk, or recover from other issues.

I prefer to keep my entire system files (including /home) on the same drive. That way even if one drive fails the other drives are independant and will boot. If you have essential system files on multiple drives, then any drive failure prevents booting.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by alphaamanitin on 2011-04-23
I plan to split the "linux" half of my 2 tb HD into a smaller partition, say 40 gb for /home and the rest for extra storage in ext4 format.  Do you you think it is worth it to split the ~30 gb Ubuntu partition on sdb (the SSD) into 25 gb for / and 5 for swap?  Or would you do less swap?  

I would prefer to keep /home on the same drive but with just 30 gb to work with on sdb (the SSD) I am not sure I would have space to have a /, /home, and swap.  What do you think?  

Also, guys I have never installed Ubuntu and *then* Windows.  Any words of wisdom?

Thanks

AlphaA

NEW INFO

Can't seem to even figure out if I am even in efi mode in my install.  I boot into 11.04beta AMD64 liveCD, get my wireless working, choose install.  Have no idea what mode I am, and a google search didn't turn up any info on selecting the mode.  Starting to seriously think about install only Windows for a while until UEFI is much more simple with Ubuntu than it is now.

AlphaA

---

### Post by srs5694 on 2011-04-23
Some comments:


[list]
[*]I don't know how a UEFI board will handle booting from the second disk (/dev/sdb). It's hard to imagine the designers would be so brain-dead as to make it impossible, but you might want to swap your cables around so that the board will detect your SSD as /dev/sda, just to be safe. If you don't want to do that or if it doesn't work, be sure to create an EFI System Partition (ESP) on the bigger disk, so that if the EFI wants to look there for the ESP it'll be there.
[*]*Do not* put swap on your SSD! That technology is more limited in terms of the number of writes it can handle, and swap space by its nature tends to collect a lot of writes. Put your swap space on the spinning disk instead. (OTOH, you're not likely to use swap a lot, so this might not be as big a deal as I've heard.)
[*]The traditional advice is to make swap 1-2 times the size of your RAM. This is often overkill on modern systems with lots of RAM, but if you want to use the "suspend to disk" (aka "hibernate") feature, you need at least as much swap as you've got RAM. Thus, you might want to go with something like 1.1x the RAM size.
[*]It's not clear to me that you're setting the partition types correctly. It sounds like you're setting the partition labels to hold the names, but the labels are there just for human use. GNU Parted and GParted set types automatically for most filesystems, but you need to set various "flags," like "boot" for the ESP, or "msftres" for the Microsoft reserved partition. Alternatively, you could use my [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) which more directly maps partition types. You should be able to install it in the Ubuntu installer when it's booted into live CD mode. (It's not installed by default.) Set partition type codes of 0700 on the Linux and Windows boot and data partitions, EF00 on the ESP, 0C01 for the Microsoft reserved partition, and 8200 on the Linux swap partition.
[*]Given your partition numbering, you'd mount partition ***3*** (the Linux partition), not partition 4 (the Windows partition), at root (/). You could specify a mount point for the Windows partition, if you like, but bear in mind that it's always a bit risky to access one OS's boot partition from another OS. If you haven't already planned to do so, you might want to add in a separate FAT or NTFS partition to use for data exchange or data that's to be shared between OSes.
[*]On a primarily Linux system, I'd create a separate /home partition (probably on the spinning disk) in which I'd store most of my data. There's normally no point in creating a separate data partition in a Linux-native format (but see below); but if you expect to need to access lots of files from both Linux and Windows, creating such a partition as FAT or NTFS is probably in order.
[*]Don't worry about keeping related partitions (root and /home, say) on the same drive. The fact that you've got both SSD and spinning-disk technologies in one system has implications that far outweigh the advantages of keeping everything on one drive that oldfred mentioned. In particular, you've got speed, size, and life cycle issues to consider. Depending on what sort of data you'll be storing and how you intend to use the system, these issues might prompt some unusual partitioning decisions. For instance, you might create /home on one disk and a separate Linux data partition on the other, contrary to my previous point, so as to provide quicker data access for some types of data. Precisely what would be optimal depends on your unique needs, though.
[/list]

---

### Post by oldfred on 2011-04-23
It was my understanding that windows will not boot from gpt unless you are UEFI.

I now keep /home inside my / (root) and symlink all the data folder back in. Then the /home only has the mostly hidden files & folders for configuration. I have not moved my .wine with Picasa yet and it is 3/4 of the 1GB my /home is. My root is about 6 to 7GB with /home. One source said keep / at about 25% used.

If you have lots of memory you may not need swap. Some like a swap file, so it is used only if needed. I have not done that so not sure how that works exactly. But you do not want to use swap as it is slower than memory. You can also set swappiness to reduce use.

Herman thinks it boots quicker if it can find a swap, otherwise it seems to get lost for a bit before it knows there is no swap. He uses swap file I believe.
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by srs5694 on 2011-04-23
> **alphaamanitin said:**
> Can't seem to even figure out if I am even in efi mode in my install.  I boot into 11.04beta AMD64 liveCD, get my wireless working, choose install.  Have no idea what mode I am, and a google search didn't turn up any info on selecting the mode.  Starting to seriously think about install only Windows for a while until UEFI is much more simple with Ubuntu than it is now.

In Linux, type this:

```

dmesg | grep EFI

```

A BIOS-based computer will produce no output to this command (unless perhaps some hardware component has "EFI" in its name, like "REFINED ETHERNET" [which is just a made-up example]). An EFI-based computer will produce several lines of output, though, like this:

```

[    0.000000] EFI v2.10 by VBOX 64
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem01: type=2, attr=0xf, range=[0x0000000000100000-0x000000000047e000) (3MB)
[    0.000000] EFI: mem02: type=7, attr=0xf, range=[0x000000000047e000-0x000000000f87e000) (244MB)
[    0.000000] EFI: mem03: type=2, attr=0xf, range=[0x000000000f87e000-0x000000001f000000) (247MB)
[    0.000000] EFI: mem04: type=3, attr=0xf, range=[0x000000001f000000-0x000000001f00e000) (0MB)
[    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x000000001f00e000-0x000000003751c000) (389MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x000000003751c000-0x0000000037a86000) (5MB)
[    0.000000] EFI: mem07: type=7, attr=0xf, range=[0x0000000037a86000-0x000000003ddb6000) (99MB)
[    0.000000] EFI: mem08: type=4, attr=0xf, range=[0x000000003ddb6000-0x000000003e199000) (3MB)
[    0.000000] EFI: mem09: type=7, attr=0xf, range=[0x000000003e199000-0x000000003e1aa000) (0MB)
[    0.000000] EFI: mem10: type=4, attr=0xf, range=[0x000000003e1aa000-0x000000003e1c4000) (0MB)
[    0.000000] EFI: mem11: type=7, attr=0xf, range=[0x000000003e1c4000-0x000000003e1d1000) (0MB)
[    0.000000] EFI: mem12: type=4, attr=0xf, range=[0x000000003e1d1000-0x000000003e1f0000) (0MB)
[    0.000000] EFI: mem13: type=7, attr=0xf, range=[0x000000003e1f0000-0x000000003e2bf000) (0MB)
[    0.000000] EFI: mem14: type=1, attr=0xf, range=[0x000000003e2bf000-0x000000003e334000) (0MB)
[    0.000000] EFI: mem15: type=7, attr=0xf, range=[0x000000003e334000-0x000000003e37e000) (0MB)
[    0.000000] EFI: mem16: type=2, attr=0xf, range=[0x000000003e37e000-0x000000003e384000) (0MB)
[    0.000000] EFI: mem17: type=4, attr=0xf, range=[0x000000003e384000-0x000000003e861000) (4MB)
[    0.000000] EFI: mem18: type=3, attr=0xf, range=[0x000000003e861000-0x000000003ea2c000) (1MB)
[    0.000000] EFI: mem19: type=5, attr=0x800000000000000f, range=[0x000000003ea2c000-0x000000003ea4f000) (0MB)
[    0.000000] EFI: mem20: type=3, attr=0xf, range=[0x000000003ea4f000-0x000000003ea79000) (0MB)
[    0.000000] EFI: mem21: type=5, attr=0x800000000000000f, range=[0x000000003ea79000-0x000000003ea8f000) (0MB)
[    0.000000] EFI: mem22: type=0, attr=0xf, range=[0x000000003ea8f000-0x000000003ea90000) (0MB)
[    0.000000] EFI: mem23: type=4, attr=0xf, range=[0x000000003ea90000-0x000000003ef2c000) (4MB)
[    0.000000] EFI: mem24: type=3, attr=0xf, range=[0x000000003ef2c000-0x000000003ef38000) (0MB)
[    0.000000] EFI: mem25: type=4, attr=0xf, range=[0x000000003ef38000-0x000000003f85b000) (9MB)
[    0.000000] EFI: mem26: type=7, attr=0xf, range=[0x000000003f85b000-0x000000003f85f000) (0MB)
[    0.000000] EFI: mem27: type=3, attr=0xf, range=[0x000000003f85f000-0x000000003f8da000) (0MB)
[    0.000000] EFI: mem28: type=5, attr=0x800000000000000f, range=[0x000000003f8da000-0x000000003f8e8000) (0MB)
[    0.000000] EFI: mem29: type=3, attr=0xf, range=[0x000000003f8e8000-0x000000003f92f000) (0MB)
[    0.000000] EFI: mem30: type=5, attr=0x800000000000000f, range=[0x000000003f92f000-0x000000003f93e000) (0MB)
[    0.000000] EFI: mem31: type=3, attr=0xf, range=[0x000000003f93e000-0x000000003f94b000) (0MB)
[    0.000000] EFI: mem32: type=5, attr=0x800000000000000f, range=[0x000000003f94b000-0x000000003f94f000) (0MB)
[    0.000000] EFI: mem33: type=5, attr=0x800000000000000f, range=[0x000000003f94f000-0x000000003f96b000) (0MB)
[    0.000000] EFI: mem34: type=6, attr=0x800000000000000f, range=[0x000000003f96b000-0x000000003f9a1000) (0MB)
[    0.000000] EFI: mem35: type=6, attr=0x800000000000000f, range=[0x000000003f9a1000-0x000000003f9bb000) (0MB)
[    0.000000] EFI: mem36: type=9, attr=0xf, range=[0x000000003f9bb000-0x000000003f9d1000) (0MB)
[    0.000000] EFI: mem37: type=9, attr=0xf, range=[0x000000003f9d1000-0x000000003f9d7000) (0MB)
[    0.000000] EFI: mem38: type=10, attr=0xf, range=[0x000000003f9d7000-0x000000003f9d8000) (0MB)
[    0.000000] EFI: mem39: type=10, attr=0xf, range=[0x000000003f9d8000-0x000000003f9db000) (0MB)
[    0.000000] EFI: mem40: type=4, attr=0xf, range=[0x000000003f9db000-0x000000003fee0000) (5MB)
[    0.000000] EFI: mem41: type=6, attr=0x800000000000000f, range=[0x000000003fee0000-0x000000003ff00000) (0MB)
[    0.000000]   #2 [003e382000 - 003e3827e0]       EFI memmap ==> [003e382000 - 003e3827e0]
[    0.426216] fbcon: EFI VGA (fb0) is primary device
[    0.436135] fb0: EFI VGA frame buffer device
[    0.556369] EFI Variables Facility v0.08 2004-May-17

```

That's quite a lot of output, and much of it will be system-specific. (This is taken from a Fedora 14 installation in VirtualBox using its EFI mode.) I don't even know what much of it means. The point, though, is that it's identifying the firmware as EFI rather than as BIOS.

Although some computers can switch between (U)EFI and BIOS modes, some can't. My impression is that the latest crop of boards with UEFI are UEFI-only; however, as I don't own one, I'm far from certain of this.

As I've said before, (U)EFI isn't really harder to deal with than BIOS; it's just got its own unique quirks. Partitioning and installation are the worst of it, so if you stick with it, you'll be through the worst of the learning curve quickly enough.

---

### Post by KegHead on 2011-04-23
Wow!

A mips monster?

KegHead

---

### Post by alphaamanitin on 2011-04-23
> **srs5694 said:**
> In Linux, type this:

```

dmesg | grep EFI

```A BIOS-based computer will produce no output to this command (unless perhaps some hardware component has "EFI" in its name, like "REFINED ETHERNET" [which is just a made-up example]). An EFI-based computer will produce several lines of output, though, like this:

[...]


No output, but I definitely have UEFI, I have a GUI for MOBO set up options.  I'll have to do some more reading on my MOBO because I have no idea how to get it into UEFI mode.  Windows 7 x64 also won't let me install because I have a GPT formatted drive, so it also must be booting in legacy BIOS mode.  I get options when I boot, either EFI SONY boot or SATA SONY boot.  It only boots in SATA mode, not EFI mode for my Ubuntu 11.04 AMD64 LiveCD.  Stupid, I noticed this last night but didn't connect the dots, just stupid of me.  

I guess that my LiveCD does not have the things to boot into UEFI mode.  

Also, I have a mild thought here, I know dangerous considering I am a Biologist not a CS person, what about installing windows 7 x64, then install Ubuntu, this then repair the Windows 7 install?  Think that would fix the Ubuntu problem wiping the necessary Windows 7 boot files?  Sorry I don't know all the terms for UEFI stuff, just BIOS things.


@srs5694- Do you know any groups that will help with these issues?  Like a Linux club where you can bring your computer to?  I don't want to say exactly where I live, but the area where you live is in easy driving distance for me.  Only problem is that it is a giant Full ATX tower desktop so hard to take places.  There isn't really anyone that is here that can help me in person.

AlphaA

---

### Post by srs5694 on 2011-04-23
It sounds like your board can boot in either EFI mode ("EFI SONY") or BIOS mode ("SATA SONY"), although the latter name is extremely strange for identifying BIOS mode. Thus, you have three choices:


[list]
[*]Continue trying to install both OSes in EFI mode -- If you can't boot the Ubuntu installer in this mode, you'll obviously have to do some more debugging on that score, but it should be possible to get it working eventually.
[*]Install Windows in EFI mode and Ubuntu in BIOS mode, then switch Ubuntu to boot in EFI mode after you've got it installed -- This will work around whatever issue you've got with booting the installation DVD, but it will require additional post-installation configuration. You'll also have to add a small (~1 MiB) [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) to the disk to help GRUB manage the boot in BIOS mode.
[*]Switch to BIOS mode for both OSes -- You'll need to switch from GPT to MBR partitions for this, and if you want to boot Windows from a >2TiB disk in the future, you'll have to re-install Windows rather than just copy your current installation (or jump through a bunch of weird Windows hoops). This might be the simplest approach in the short term, but you might regret it in a year or two.
[/list]


As far as booting the Ubuntu installer in EFI mode, I suggest you first check the CD/DVD you've burned. It should include a file called efi/boot/bootx64.efi. If it doesn't, that's most likely the problem. Perhaps you burned the disc incorrectly, or maybe the developers erred and the image they've delivered isn't EFI-bootable. In theory, it's correctable, but it could be a pain to do so. If that file *is* present, perhaps your EFI isn't finding it, or you may need to select that file in your EFI's boot loader. (EFI includes its own boot loader, unlike BIOS. There should be an option somewhere to locate a boot file, and you should be able to locate and run the efi/boot/bootx64.efi file on the Ubuntu install disc from that.)

---

### Post by alphaamanitin on 2011-04-23
This is so frustrating.  the efi/boot/bootx64.efi is there, but I cannot  figure out how to get my MOBO to boot from that using its own boot  loader.  In fact I cannot really find anything in the MOBO manual to  point directly to files on a device to use to boot EFI from.  I also  cannot find out whether or not my SSD and HD use NCQ or Hotplug  I am  pretty sure they are not using hot plug, that looks like connecting to a  molex adapter or something, mine are direct SATA III cables to MOBO,  but I cannot find anything out about NCQ for my drives, even on the  respective manufacturers page.  

I am giving up on installing Ubuntu for now.  I will just have to settle  for Windows 7, and we will see if that thing boots using UEFI:SONY.  If  not, I guess I am screwed and will have to go to the bios options,  which I really don't want to do, why have UEFI if you are not using it  you know?

Thanks srs5694.

*****UPDATE******

Cannot get the Windows 7 x64 DVD installation disk to boot in UEFI mode either.  Nothing on this board will boot UEFI.  I have triple check and the board is supposed to be UEFI.  I don't know what to do now.  I guess I am just going to install everything like BIOS.  Thanks for all the help guys.  Unless some one posts a great idea soon I am giving up on the whole UEFI thing and going to BIOS.

AlphaA

---

### Post by the-ridikulus-rat on 2011-04-23
> **alphaamanitin said:**
> This is so frustrating.  the efi/boot/bootx64.efi is there, but I cannot  figure out how to get my MOBO to boot from that using its own boot  loader.  In fact I cannot really find anything in the MOBO manual to  point directly to files on a device to use to boot EFI from.  I also  cannot find out whether or not my SSD and HD use NCQ or Hotplug  I am  pretty sure they are not using hot plug, that looks like connecting to a  molex adapter or something, mine are direct SATA III cables to MOBO,  but I cannot find anything out about NCQ for my drives, even on the  respective manufacturers page.  

I am giving up on installing Ubuntu for now.  I will just have to settle  for Windows 7, and we will see if that thing boots using UEFI:SONY.  If  not, I guess I am screwed and will have to go to the bios options,  which I really don't want to do, why have UEFI if you are not using it  you know?

Thanks srs5694.

*****UPDATE******

Cannot get the Windows 7 x64 DVD installation disk to boot in UEFI mode either.  Nothing on this board will boot UEFI.  I have triple check and the board is supposed to be UEFI.  I don't know what to do now.  I guess I am just going to install everything like BIOS.  Thanks for all the help guys.  Unless some one posts a great idea soon I am giving up on the whole UEFI thing and going to BIOS.

AlphaA

There is always the official manual [ftp://174.142.97.10/manual/880G%20Pro3.pdf](ftp://174.142.97.10/manual/880G%20Pro3.pdf)

---

### Post by alphaamanitin on 2011-04-23
Okay,

I am stubborn so I still have not given up yet.  So, I have updated the  "BIOS" from 1.1 to 1.2 using the instant flash built in utility provided  by ASRock.  I tried to boot my CD in EUFI and I get this message  immediately,

```
Error: "prefix" is not set
```

Then it boots to the menu, you know try ubuntu, install ubuntu, check  disk for errors (which I am doing).  I try ubuntu, it boots into ubuntu  and all I can see is just the very top part of the screen which is  flashing back and forth to black, the rest of the screen is black.  It  is just barely enough to see about 3/5 of the shut down logo.  Graphical  error is the same when checking the disk for errors as well.  

I put in the Windows 7 install disk and it boots UEFI fine, and the  graphics on the installer are fine as well.  I downloaded the most up to  date 11, 11.04.2 beta2 AMD64 and it has the exact same graphical errors  as the 11.04 beta AMD64 I have downloaded.  It must be just something  to do with my computer, I guess I am going to have to just install  windows 7 alone for now and not get Ubuntu.  

Marking thread as solved I guess.

AlphaA

---

### Post by alphaamanitin on 2011-04-23
> **skodabenz said:**
> There is always the official manual [ftp://174.142.97.10/manual/880G%20Pro3.pdf](ftp://174.142.97.10/manual/880G%20Pro3.pdf)


yeah, that is what I was reading.  It only mentions booting by device, cannot point directly to a file to boot from.

AlphaA

---

### Post by the-ridikulus-rat on 2011-04-23
@alphaamanitin: Read the last page of the manual on how to install windows in uefi mode. For ubuntu do the same way like windows x64 dvd.

If that does not work copy [http://tianocore.git.sourceforge.net/git/gitweb.cgi?p=tianocore/edk2;a=blob_plain;f=ShellBinPkg/UefiShell/X64/Shell.efi;hb=HEAD](http://tianocore.git.sourceforge.net/git/gitweb.cgi?p=tianocore/edk2;a=blob_plain;f=ShellBinPkg/UefiShell/X64/Shell.efi;hb=HEAD) to <Partition 1-100MB-label EFI, Format FAT32>/Shell64.efi or <Partition 1-100MB-label EFI, Format FAT32>/shellx64.efi . Launch the shell from the 'EXIT' page of the UEFI menu and launch efi from ubuntu using

```

fs0:
cd efi\boot
bootx64.efi

```

---

### Post by the-ridikulus-rat on 2011-04-23
> **alphaamanitin said:**
> yeah, that is what I was reading.  It only mentions booting by device, cannot point directly to a file to boot from.

AlphaA

For launching an efi app directly, use uefi shell. Can you come online in #ubuntu irc?

---

### Post by alphaamanitin on 2011-04-23
sure, what is the info, but fyi it wouldn't load the shell.  Anyway, that isn't the issue anymore.  Now the graphics are the hold up.

---

### Post by the-ridikulus-rat on 2011-04-23
> **alphaamanitin said:**
> sure, what is the info, but fyi it wouldn't load the shell.  Anyway, that isn't the issue anymore.  Now the graphics are the hold up.

[http://webchat.freenode.net/](http://webchat.freenode.net/)

Nickname: alphaamanitin
Channels: #ubuntu
<enter captcha>
<connect>

---

### Post by alphaamanitin on 2011-04-23
There.

AlphaA

---

### Post by srs5694 on 2011-04-23
Concerning the graphics, there are ways to install Ubuntu in text mode. I don't recall offhand how to do this using the desktop installer, or if it's even possible, but IIRC, a text-mode install is the default for the "alternate" installer. You might give that a try. You could also try some other Linux distribution, like Fedora, which I know supports (U)EFI booting.

More generally, from your description it sounds as if ASRock may have rushed that board out the door with a poorly-debugged UEFI implementation!

---

### Post by alphaamanitin on 2011-04-23
Think you are right, they rushed the UEFI booting.  I did get it working though, just the graphics are to the point where I can't install.  I went ahead and just installed Windows 7 to see if I could get UEFI booting working, and it did.  WOW Windows 7+UEFI+SSD incredibly fast booting.  

Skodabenz had a good idea I think.  So GRUB2 is the only thing that is different right?  So boot the liveCD in BIOS mode, install, then stay in the livecd mount the new install, install GRUB2 and set it up for EFI booting.  So I was wondering.  Could I install something like teamviewer and have some one with more skill in chroot and the like to set up the GRUB2.

Thanks Guys,

AlphaA

---

### Post by the-ridikulus-rat on 2011-04-24
> **srs5694 said:**
> Some comments:

[list]
[*]I don't know how a UEFI board will handle booting from the second disk (/dev/sdb). It's hard to imagine the designers would be so brain-dead as to make it impossible, but you might want to swap your cables around so that the board will detect your SSD as /dev/sda, just to be safe. If you don't want to do that or if it doesn't work, be sure to create an EFI System Partition (ESP) on the bigger disk, so that if the EFI wants to look there for the ESP it'll be there.
[/list]


AFAIK UEFI uses unique disk GUID and unique partition GUID to identify partitions in its boot manager (after all they defined GPT partitioning). So i don't think there should be any problem in booting from second HDD/SSD, although i have not checked such config (using 2 or more disks).

---

### Post by the-ridikulus-rat on 2011-04-24
> **srs5694 said:**
> 
As far as booting the Ubuntu installer in EFI mode, I suggest you first check the CD/DVD you've burned. It should include a file called efi/boot/bootx64.efi. If it doesn't, that's most likely the problem. Perhaps you burned the disc incorrectly, or maybe the developers erred and the image they've delivered isn't EFI-bootable. In theory, it's correctable, but it could be a pain to do so. If that file *is* present, perhaps your EFI isn't finding it, or you may need to select that file in your EFI's boot loader. (EFI includes its own boot loader, unlike BIOS. There should be an option somewhere to locate a boot file, and you should be able to locate and run the efi/boot/bootx64.efi file on the Ubuntu install disc from that.)

UEFI spec (including 2.3.1 as of April 2011) does not require having efi/boot/bootx64.efi in the iso to make it uefi boot. It works slightly different from what you think. I suggest you read through this script [http://projects.archlinux.org/archboot.git/tree/usr/bin/archboot-allinone.sh](http://projects.archlinux.org/archboot.git/tree/usr/bin/archboot-allinone.sh) to understand how a bios+uefi iso (bios=syslinux, uefi=grub2) is created and this script [http://projects.archlinux.org/archboot.git/tree/usr/bin/archboot-usbimage-helper.sh](http://projects.archlinux.org/archboot.git/tree/usr/bin/archboot-usbimage-helper.sh) on how to use the iso to create a bios+uefi bootable usb (isohybrid will not work for uefi systems - usb should be FAT32 formatted).

---

### Post by alphaamanitin on 2011-04-24
I like to have every thing nice and orderly.  I really want to have both Windows 7 and Ubuntu booting from UEFI methods.  I have also read that due to a issue with Windows 7 if you are going to dual boot either both need to be in UEFI or in BIOS, can't be mixed.  Though I may be confused on this and not understanding things correctly.  I am going to email a local Linux guru I know and see if he can provide more help, he could actually look at the computer you know so that would be helpful I think.  

Would any of you be willing to help via teamviewer with the chroot and install of efi grub like skodabenz was tying to help me with, thanks again for that.  If you are let me know a time and I can clear my schedule to meet yours.  

Also, what do you guys think about just waiting until 11 is fully released and see if these "graphic" anomalies disappear?

Thanks for all the help guys.  If I ever get this dual boot working I will post all the steps here.  I think I might need to make a new thread as we have gone a little past the intent of this thread.  

Thanks guys.

AlphaA

---

### Post by srs5694 on 2011-04-24
> **skodabenz said:**
> UEFI spec (including 2.3.1 as of April 2011) does not require having efi/boot/bootx64.efi in the iso to make it uefi boot. It works slightly different from what you think.

No, I understand fine; you misunderstood my comment. I was reporting the actual files on my Ubuntu 11.04 alpha 2 disc, not the files that UEFI requires. My thought was that the disc might have been burned improperly (say, as an .iso file stored on the disc -- a common error) or that the developers might have changed things or accidentally omitted a file for the beta (which I haven't downloaded).

---

### Post by srs5694 on 2011-04-24
> **alphaamanitin said:**
> I like to have every thing nice and orderly.  I really want to have both Windows 7 and Ubuntu booting from UEFI methods.  I have also read that due to a issue with Windows 7 if you are going to dual boot either both need to be in UEFI or in BIOS, can't be mixed.  Though I may be confused on this and not understanding things correctly.

You must be misunderstanding; I can't imagine how Windows could determine what mode (EFI or BIOS) you use to boot another OS. I'd want to use the same mode, myself, just because it's awkward to go around changing such things from one boot to the next.

> Also, what do you guys think about just waiting until 11 is fully released and see if these "graphic" anomalies disappear?

Don't count on a problem just disappearing. File a bug report!

---

### Post by alphaamanitin on 2011-04-24
I am sorry I should have been more clear, what I really meant is that you have to install Ubuntu in GPT or Windows cannot boot in UEFI mode.  Since, I cannot see the GUI to install during livecd session in UEFI boots of my 11.04.2 beta2 liveCD I cannot install it in UEFI mode, will Ubuntu install with GPT without UEFI booting?  

I'll look into reporting the bug.  

Thanks guys,

alphaa

---

### Post by srs5694 on 2011-04-25
Yes, Linux installs fine on GPT in BIOS mode. You should, however, have a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) for best results. (It's more reliable that way, and some people have problems getting GRUB installed at all without one.)

---

### Post by alphaamanitin on 2011-04-25
I'm stupid and should have thought of this ages ago.  When I got the choices to try Ubuntu, install Ubuntu, or check disk for errors, I hit E.  I changed the boot location to be ```
/cdrom/efi/boot/bootx64.efi
```I then booted into the liveCD and ran ```
dmesg | grep EFI
``` Here is the output:```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x000000000007f000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x000000000007f000-0x0000000000080000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000080000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000064d000) (5MB)
[    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x000000000064d000-0x0000000001000000) (9MB)
[    0.000000] EFI: mem06: type=4, attr=0xf, range=[0x0000000001000000-0x0000000001565000) (5MB)
[    0.000000] EFI: mem07: type=3, attr=0xf, range=[0x0000000001565000-0x0000000001569000) (0MB)
[    0.000000] EFI: mem08: type=4, attr=0xf, range=[0x0000000001569000-0x0000000001596000) (0MB)
[    0.000000] EFI: mem09: type=3, attr=0xf, range=[0x0000000001596000-0x000000000159c000) (0MB)
[    0.000000] EFI: mem10: type=4, attr=0xf, range=[0x000000000159c000-0x000000000159f000) (0MB)
[    0.000000] EFI: mem11: type=3, attr=0xf, range=[0x000000000159f000-0x00000000015a2000) (0MB)
[    0.000000] EFI: mem12: type=4, attr=0xf, range=[0x00000000015a2000-0x00000000015a5000) (0MB)
[    0.000000] EFI: mem13: type=3, attr=0xf, range=[0x00000000015a5000-0x00000000015a8000) (0MB)
[    0.000000] EFI: mem14: type=4, attr=0xf, range=[0x00000000015a8000-0x00000000015aa000) (0MB)
[    0.000000] EFI: mem15: type=3, attr=0xf, range=[0x00000000015aa000-0x00000000015ac000) (0MB)
[    0.000000] EFI: mem16: type=4, attr=0xf, range=[0x00000000015ac000-0x00000000015ad000) (0MB)
[    0.000000] EFI: mem17: type=3, attr=0xf, range=[0x00000000015ad000-0x00000000015af000) (0MB)
[    0.000000] EFI: mem18: type=4, attr=0xf, range=[0x00000000015af000-0x00000000015b3000) (0MB)
[    0.000000] EFI: mem19: type=3, attr=0xf, range=[0x00000000015b3000-0x00000000015b5000) (0MB)
[    0.000000] EFI: mem20: type=4, attr=0xf, range=[0x00000000015b5000-0x00000000015b6000) (0MB)
[    0.000000] EFI: mem21: type=3, attr=0xf, range=[0x00000000015b6000-0x00000000015b7000) (0MB)
[    0.000000] EFI: mem22: type=4, attr=0xf, range=[0x00000000015b7000-0x00000000015bf000) (0MB)
[    0.000000] EFI: mem23: type=3, attr=0xf, range=[0x00000000015bf000-0x00000000015c2000) (0MB)
[    0.000000] EFI: mem24: type=4, attr=0xf, range=[0x00000000015c2000-0x00000000015d3000) (0MB)
[    0.000000] EFI: mem25: type=3, attr=0xf, range=[0x00000000015d3000-0x00000000015de000) (0MB)
[    0.000000] EFI: mem26: type=4, attr=0xf, range=[0x00000000015de000-0x00000000015e8000) (0MB)
[    0.000000] EFI: mem27: type=3, attr=0xf, range=[0x00000000015e8000-0x00000000015ef000) (0MB)
[    0.000000] EFI: mem28: type=4, attr=0xf, range=[0x00000000015ef000-0x00000000015f4000) (0MB)
[    0.000000] EFI: mem29: type=3, attr=0xf, range=[0x00000000015f4000-0x00000000015f5000) (0MB)
[    0.000000] EFI: mem30: type=4, attr=0xf, range=[0x00000000015f5000-0x00000000015fc000) (0MB)
[    0.000000] EFI: mem31: type=3, attr=0xf, range=[0x00000000015fc000-0x00000000015fd000) (0MB)
[    0.000000] EFI: mem32: type=4, attr=0xf, range=[0x00000000015fd000-0x0000000001628000) (0MB)
[    0.000000] EFI: mem33: type=3, attr=0xf, range=[0x0000000001628000-0x000000000162a000) (0MB)
[    0.000000] EFI: mem34: type=4, attr=0xf, range=[0x000000000162a000-0x000000000162f000) (0MB)
[    0.000000] EFI: mem35: type=3, attr=0xf, range=[0x000000000162f000-0x0000000001631000) (0MB)
[    0.000000] EFI: mem36: type=4, attr=0xf, range=[0x0000000001631000-0x0000000001633000) (0MB)
[    0.000000] EFI: mem37: type=3, attr=0xf, range=[0x0000000001633000-0x000000000165a000) (0MB)
[    0.000000] EFI: mem38: type=4, attr=0xf, range=[0x000000000165a000-0x000000000165b000) (0MB)
[    0.000000] EFI: mem39: type=3, attr=0xf, range=[0x000000000165b000-0x000000000165c000) (0MB)
[    0.000000] EFI: mem40: type=4, attr=0xf, range=[0x000000000165c000-0x000000000165e000) (0MB)
[    0.000000] EFI: mem41: type=3, attr=0xf, range=[0x000000000165e000-0x000000000166e000) (0MB)
[    0.000000] EFI: mem42: type=4, attr=0xf, range=[0x000000000166e000-0x000000000167f000) (0MB)
[    0.000000] EFI: mem43: type=3, attr=0xf, range=[0x000000000167f000-0x0000000001683000) (0MB)
[    0.000000] EFI: mem44: type=4, attr=0xf, range=[0x0000000001683000-0x0000000001684000) (0MB)
[    0.000000] EFI: mem45: type=3, attr=0xf, range=[0x0000000001684000-0x0000000001689000) (0MB)
[    0.000000] EFI: mem46: type=4, attr=0xf, range=[0x0000000001689000-0x0000000001691000) (0MB)
[    0.000000] EFI: mem47: type=3, attr=0xf, range=[0x0000000001691000-0x0000000001693000) (0MB)
[    0.000000] EFI: mem48: type=4, attr=0xf, range=[0x0000000001693000-0x0000000001695000) (0MB)
[    0.000000] EFI: mem49: type=3, attr=0xf, range=[0x0000000001695000-0x0000000001698000) (0MB)
[    0.000000] EFI: mem50: type=4, attr=0xf, range=[0x0000000001698000-0x000000000169a000) (0MB)
[    0.000000] EFI: mem51: type=3, attr=0xf, range=[0x000000000169a000-0x000000000169e000) (0MB)
[    0.000000] EFI: mem52: type=4, attr=0xf, range=[0x000000000169e000-0x00000000016a3000) (0MB)
[    0.000000] EFI: mem53: type=3, attr=0xf, range=[0x00000000016a3000-0x00000000016a4000) (0MB)
[    0.000000] EFI: mem54: type=4, attr=0xf, range=[0x00000000016a4000-0x00000000016b0000) (0MB)
[    0.000000] EFI: mem55: type=3, attr=0xf, range=[0x00000000016b0000-0x00000000016b9000) (0MB)
[    0.000000] EFI: mem56: type=4, attr=0xf, range=[0x00000000016b9000-0x00000000016bb000) (0MB)
[    0.000000] EFI: mem57: type=3, attr=0xf, range=[0x00000000016bb000-0x00000000016c6000) (0MB)
[    0.000000] EFI: mem58: type=4, attr=0xf, range=[0x00000000016c6000-0x00000000016c8000) (0MB)
[    0.000000] EFI: mem59: type=3, attr=0xf, range=[0x00000000016c8000-0x00000000016d0000) (0MB)
[    0.000000] EFI: mem60: type=4, attr=0xf, range=[0x00000000016d0000-0x00000000016d2000) (0MB)
[    0.000000] EFI: mem61: type=3, attr=0xf, range=[0x00000000016d2000-0x00000000016d4000) (0MB)
[    0.000000] EFI: mem62: type=4, attr=0xf, range=[0x00000000016d4000-0x00000000016d5000) (0MB)
[    0.000000] EFI: mem63: type=3, attr=0xf, range=[0x00000000016d5000-0x00000000016d8000) (0MB)
[    0.000000] EFI: mem64: type=4, attr=0xf, range=[0x00000000016d8000-0x00000000016df000) (0MB)
[    0.000000] EFI: mem65: type=3, attr=0xf, range=[0x00000000016df000-0x00000000016e6000) (0MB)
[    0.000000] EFI: mem66: type=4, attr=0xf, range=[0x00000000016e6000-0x00000000016fb000) (0MB)
[    0.000000] EFI: mem67: type=3, attr=0xf, range=[0x00000000016fb000-0x000000000170a000) (0MB)
[    0.000000] EFI: mem68: type=4, attr=0xf, range=[0x000000000170a000-0x000000000170b000) (0MB)
[    0.000000] EFI: mem69: type=3, attr=0xf, range=[0x000000000170b000-0x000000000170e000) (0MB)
[    0.000000] EFI: mem70: type=4, attr=0xf, range=[0x000000000170e000-0x000000000171e000) (0MB)
[    0.000000] EFI: mem71: type=3, attr=0xf, range=[0x000000000171e000-0x0000000001729000) (0MB)
[    0.000000] EFI: mem72: type=4, attr=0xf, range=[0x0000000001729000-0x0000000001735000) (0MB)
[    0.000000] EFI: mem73: type=3, attr=0xf, range=[0x0000000001735000-0x0000000001739000) (0MB)
[    0.000000] EFI: mem74: type=4, attr=0xf, range=[0x0000000001739000-0x000000000173d000) (0MB)
[    0.000000] EFI: mem75: type=3, attr=0xf, range=[0x000000000173d000-0x000000000173e000) (0MB)
[    0.000000] EFI: mem76: type=4, attr=0xf, range=[0x000000000173e000-0x000000000173f000) (0MB)
[    0.000000] EFI: mem77: type=3, attr=0xf, range=[0x000000000173f000-0x0000000001742000) (0MB)
[    0.000000] EFI: mem78: type=4, attr=0xf, range=[0x0000000001742000-0x0000000001748000) (0MB)
[    0.000000] EFI: mem79: type=3, attr=0xf, range=[0x0000000001748000-0x000000000178a000) (0MB)
[    0.000000] EFI: mem80: type=4, attr=0xf, range=[0x000000000178a000-0x0000000001794000) (0MB)
[    0.000000] EFI: mem81: type=3, attr=0xf, range=[0x0000000001794000-0x0000000001799000) (0MB)
[    0.000000] EFI: mem82: type=4, attr=0xf, range=[0x0000000001799000-0x00000000017a1000) (0MB)
[    0.000000] EFI: mem83: type=3, attr=0xf, range=[0x00000000017a1000-0x00000000017a7000) (0MB)
[    0.000000] EFI: mem84: type=4, attr=0xf, range=[0x00000000017a7000-0x00000000017a9000) (0MB)
[    0.000000] EFI: mem85: type=3, attr=0xf, range=[0x00000000017a9000-0x00000000017ab000) (0MB)
[    0.000000] EFI: mem86: type=4, attr=0xf, range=[0x00000000017ab000-0x00000000017ad000) (0MB)
[    0.000000] EFI: mem87: type=3, attr=0xf, range=[0x00000000017ad000-0x00000000017af000) (0MB)
[    0.000000] EFI: mem88: type=4, attr=0xf, range=[0x00000000017af000-0x00000000017b3000) (0MB)
[    0.000000] EFI: mem89: type=3, attr=0xf, range=[0x00000000017b3000-0x00000000017b5000) (0MB)
[    0.000000] EFI: mem90: type=4, attr=0xf, range=[0x00000000017b5000-0x00000000017b9000) (0MB)
[    0.000000] EFI: mem91: type=3, attr=0xf, range=[0x00000000017b9000-0x00000000017bb000) (0MB)
[    0.000000] EFI: mem92: type=4, attr=0xf, range=[0x00000000017bb000-0x00000000017bc000) (0MB)
[    0.000000] EFI: mem93: type=3, attr=0xf, range=[0x00000000017bc000-0x00000000017be000) (0MB)
[    0.000000] EFI: mem94: type=4, attr=0xf, range=[0x00000000017be000-0x0000000001c97000) (4MB)
[    0.000000] EFI: mem95: type=3, attr=0xf, range=[0x0000000001c97000-0x0000000001c99000) (0MB)
[    0.000000] EFI: mem96: type=4, attr=0xf, range=[0x0000000001c99000-0x0000000001cad000) (0MB)
[    0.000000] EFI: mem97: type=3, attr=0xf, range=[0x0000000001cad000-0x0000000001caf000) (0MB)
[    0.000000] EFI: mem98: type=4, attr=0xf, range=[0x0000000001caf000-0x0000000001cb1000) (0MB)
[    0.000000] EFI: mem99: type=3, attr=0xf, range=[0x0000000001cb1000-0x0000000001cb3000) (0MB)
[    0.000000] EFI: mem100: type=4, attr=0xf, range=[0x0000000001cb3000-0x0000000001cb5000) (0MB)
[    0.000000] EFI: mem101: type=3, attr=0xf, range=[0x0000000001cb5000-0x0000000001cbf000) (0MB)
[    0.000000] EFI: mem102: type=4, attr=0xf, range=[0x0000000001cbf000-0x0000000001cc1000) (0MB)
[    0.000000] EFI: mem103: type=3, attr=0xf, range=[0x0000000001cc1000-0x0000000001cc3000) (0MB)
[    0.000000] EFI: mem104: type=4, attr=0xf, range=[0x0000000001cc3000-0x0000000001cc5000) (0MB)
[    0.000000] EFI: mem105: type=3, attr=0xf, range=[0x0000000001cc5000-0x0000000001cc7000) (0MB)
[    0.000000] EFI: mem106: type=4, attr=0xf, range=[0x0000000001cc7000-0x0000000001cc8000) (0MB)
[    0.000000] EFI: mem107: type=3, attr=0xf, range=[0x0000000001cc8000-0x0000000001ccc000) (0MB)
[    0.000000] EFI: mem108: type=4, attr=0xf, range=[0x0000000001ccc000-0x0000000001cd3000) (0MB)
[    0.000000] EFI: mem109: type=3, attr=0xf, range=[0x0000000001cd3000-0x0000000001cd5000) (0MB)
[    0.000000] EFI: mem110: type=4, attr=0xf, range=[0x0000000001cd5000-0x0000000001ce3000) (0MB)
[    0.000000] EFI: mem111: type=3, attr=0xf, range=[0x0000000001ce3000-0x0000000001ce5000) (0MB)
[    0.000000] EFI: mem112: type=4, attr=0xf, range=[0x0000000001ce5000-0x0000000001ce6000) (0MB)
[    0.000000] EFI: mem113: type=3, attr=0xf, range=[0x0000000001ce6000-0x0000000001ced000) (0MB)
[    0.000000] EFI: mem114: type=4, attr=0xf, range=[0x0000000001ced000-0x0000000001cf3000) (0MB)
[    0.000000] EFI: mem115: type=3, attr=0xf, range=[0x0000000001cf3000-0x0000000001cf6000) (0MB)
[    0.000000] EFI: mem116: type=4, attr=0xf, range=[0x0000000001cf6000-0x0000000001d16000) (0MB)
[    0.000000] EFI: mem117: type=3, attr=0xf, range=[0x0000000001d16000-0x0000000001d26000) (0MB)
[    0.000000] EFI: mem118: type=4, attr=0xf, range=[0x0000000001d26000-0x000000000213d000) (4MB)
[    0.000000] EFI: mem119: type=3, attr=0xf, range=[0x000000000213d000-0x000000000213e000) (0MB)
[    0.000000] EFI: mem120: type=4, attr=0xf, range=[0x000000000213e000-0x0000000002140000) (0MB)
[    0.000000] EFI: mem121: type=3, attr=0xf, range=[0x0000000002140000-0x0000000002141000) (0MB)
[    0.000000] EFI: mem122: type=4, attr=0xf, range=[0x0000000002141000-0x0000000002147000) (0MB)
[    0.000000] EFI: mem123: type=3, attr=0xf, range=[0x0000000002147000-0x0000000002153000) (0MB)
[    0.000000] EFI: mem124: type=4, attr=0xf, range=[0x0000000002153000-0x0000000002258000) (1MB)
[    0.000000] EFI: mem125: type=7, attr=0xf, range=[0x0000000002258000-0x0000000002271000) (0MB)
[    0.000000] EFI: mem126: type=4, attr=0xf, range=[0x0000000002271000-0x000000000237b000) (1MB)
[    0.000000] EFI: mem127: type=7, attr=0xf, range=[0x000000000237b000-0x0000000002387000) (0MB)
[    0.000000] EFI: mem128: type=4, attr=0xf, range=[0x0000000002387000-0x0000000002388000) (0MB)
[    0.000000] EFI: mem129: type=7, attr=0xf, range=[0x0000000002388000-0x0000000002389000) (0MB)
[    0.000000] EFI: mem130: type=4, attr=0xf, range=[0x0000000002389000-0x000000000238a000) (0MB)
[    0.000000] EFI: mem131: type=7, attr=0xf, range=[0x000000000238a000-0x000000000238c000) (0MB)
[    0.000000] EFI: mem132: type=4, attr=0xf, range=[0x000000000238c000-0x0000000002466000) (0MB)
[    0.000000] EFI: mem133: type=7, attr=0xf, range=[0x0000000002466000-0x000000000249e000) (0MB)
[    0.000000] EFI: mem134: type=4, attr=0xf, range=[0x000000000249e000-0x000000000249f000) (0MB)
[    0.000000] EFI: mem135: type=7, attr=0xf, range=[0x000000000249f000-0x00000000024ab000) (0MB)
[    0.000000] EFI: mem136: type=4, attr=0xf, range=[0x00000000024ab000-0x00000000024ac000) (0MB)
[    0.000000] EFI: mem137: type=7, attr=0xf, range=[0x00000000024ac000-0x00000000024c6000) (0MB)
[    0.000000] EFI: mem138: type=4, attr=0xf, range=[0x00000000024c6000-0x00000000024e8000) (0MB)
[    0.000000] EFI: mem139: type=7, attr=0xf, range=[0x00000000024e8000-0x00000000024ea000) (0MB)
[    0.000000] EFI: mem140: type=4, attr=0xf, range=[0x00000000024ea000-0x00000000024eb000) (0MB)
[    0.000000] EFI: mem141: type=7, attr=0xf, range=[0x00000000024eb000-0x00000000024ec000) (0MB)
[    0.000000] EFI: mem142: type=4, attr=0xf, range=[0x00000000024ec000-0x00000000024ed000) (0MB)
[    0.000000] EFI: mem143: type=7, attr=0xf, range=[0x00000000024ed000-0x00000000024ef000) (0MB)
[    0.000000] EFI: mem144: type=4, attr=0xf, range=[0x00000000024ef000-0x00000000024f0000) (0MB)
[    0.000000] EFI: mem145: type=7, attr=0xf, range=[0x00000000024f0000-0x00000000024f1000) (0MB)

```Solved my own problem with a VERY important piece from srs5694!  Now I need to set up the partitions, intsall Ubuntu, and then Install Windows 7 x64.

Thanks Guys, you have all been great.

Well, scratch that.  It will not go past the install step where it install the boot loader (GRUB2).  It failes every time, whether I use a CD, USB, download updates or third party things or not, on the internet not on the internet.  I just cannot get it to work.  /target is created though.  Also, where can I find the /var/log/syslog and /var/log/partman?  Those are the logs it tells me to report with the buy but I didn't know where to look, the CD or the /target area.  

AlphaA

---

