---
title: "what is swap and extended?"
date: 2011-06-04
forum: General Help
---

### Post by javajames97 on 2011-06-04
Hmmm... just a query, what exactly are my 'swap 3.1gb' and 'extended 3.1gb' partitions for? are they necessary? what would happen if i deleted them? do they have to be that big (thinking about loading ubuntu to 20gb HDD partition, but at 6gb for the other stuff, #ouch#)? What does ubuntu do about very low space when installing (i.e. in reference to the 20gb part)? why does ubuntu have these but no other Operating Systems do? Would i lose any performance without them?

so many questions!!!!

thanks in advance!

---

### Post by Joe- on 2011-06-04
Swap:[http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)

I think most people recommend that your swap is the same size as the amount of RAM you have. 
And I'm not sure about the extended.

---

### Post by beefheartvliet on 2011-06-04
This thread might Help :-) [http://ubuntuforums.org/showthread.php?t=670083](http://ubuntuforums.org/showthread.php?t=670083)

---

### Post by Hedgehog1 on 2011-06-04
The windows compatible partition map (MBR) allows 4 primary partitions.

When you need more than 4 partitions, we make one of them an 'extended' partition and then we can add more.

This is useful when you have a disk setup like this:

/dev/sda1 NTFS Windows boot partition
/dev/sda2 NTFS Windows data partitions
/dev/sda3 extended partition
__/dev/sda5 EXT4 ubuntu '/' partition
__/dev/sda6 EXT4 Ubuntu '/home' partiton
__/dev/sda7 Swap partition.

However, I have often seen the Ubuntu install do this:

/dev/sda1 EXT4 Ubuntu partition
/dev/sda2 extended partition
__/dev/sda5 Swap partition.

This could have just as easily been:

/dev/sda1 EXT4 Ubuntu partition
/dev/sda2 Swap partition.

The swap partition is a 'MEMORY SWAP SPACE' partition and is used for two things:

(1) If your system has very little RAM (or is running a program that need more RAM than you have, the Linux Kernel will write out sections of memory here to make room, and move this back and forth off the disk as the program needs memory.

(2) If you use suspend or hibernate, this is where Linux writes out your RAM so it can read it up later when you wake the computer.

If you have enough RAM and don't use Hibernate or Suspend, you can remove the swap partition and the reference to it in the /etc/fstab  file.  Folks on systems with limited storage space will sometimes not use swap because disk space is so precious to them.

***The Hedge***

:KS

---

### Post by idoitprone on 2011-06-04
When people made the mbr over 30 years ago. they did not realize that harddrives will go to gb or tb. The orginal creators decided that four primary partitions is all people need, but today this is limiting and extended partition are invented to overcome this problem. Extended partition will take one of the primary partition space, but allow the user to divide the partition to many logical partitions.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by 3xp10r3r|X13 on 2011-06-04
The swap partition jumps into place, when your ram is already taken up by other processes. 

When partitioning your hard drive, you can divide it into four primary partitions. You are able to create several logical partitions in all of those primary partitions.

Extended partition:

As we just clarified that you are able to extend your primary partition into several logical ones, I think it became clear, what an extended partition is :)

In short: A primary partition, which got extended by creating logical partitions within that primary partition. (sry, I'm repeating myself)

To answer your questions:

The Linux OS is just put together by lots of partitions, which is very useful, so you can simply build in another HD when you run out of space or if you've got just a lot of small drives available, you simply put a single partition on each one. 

You wouldn't loose any performance, by installing everything just into one big partition. So you don't have to split the system up, but you are able to :).

I hope this was helpful!

If I didn't answer a specific question, or just missed it out, just ask

---

### Post by JKyleOKC on 2011-06-04
> **3xp10r3r|X13 said:**
> When partitioning your hard drive, you can divide it into four primary partitions. You are able to create several logical partitions in all of those primary partitions.Unfortunately, not quite true. You can create logical partitions only in an extended partition, and can have only one extended partition on a drive.

The whole purpose of the extended partition is to serve as a container for logical partitions, so that you can have more than four partitions total on a drive. When the Linux kernel boots, it assigns device names such as "sda" to the drives it finds, and adds partition numbers to those names for the partitions on each drive. Primary partitions always get numbers 1 through 4; if there's an extended partition it gets the first unused primary partition number, which often is 4. Logical partitions get numbers 5 and up, even if the extended is sda2 and there's only one logical; it will be sda5.

This whole discussion applies only to the "ms-dos" variety of partition table, but it's what is in most common use and until recently was the only type available. With the advent of 1-TB and larger drives, another kind of partitioning was invented and has no such arbitrary limits.

---

### Post by javajames97 on 2011-06-04
thank you all, between you you have successfully answered this question and i am better informed now! one last question, will i be able to install ubuntu to a 20gb disk space?

---

### Post by 3xp10r3r|X13 on 2011-06-04
Sure!

You could even install it to 10gb of space.

---

### Post by 3xp10r3r|X13 on 2011-06-04
> **JKyleOKC said:**
> Unfortunately, not quite true. You can create logical partitions only in an extended partition, and can have only one extended partition on a drive.


I wasn't quite sure on that one to be honest :), but at least I learned something as well.

And now it's me who's posing the questions:

Why are you only able to create logical partitions in just one primary partition?
So why is it that the number of extended partitions possible would be only one?

---

### Post by JKyleOKC on 2011-06-04
When it comes to these two "why" questions the only answer I can give is that they were design decisions. The extended partition differs from the other primaries in that it contains other partitions and so must be treated a bit differently by the access code. I don't know of any logical reason why you could not have several extended partitions so long as they did not overlap, but that's not how the system was designed -- and in fact you never need more than one container so there's no need to allow more. Note that with the newer huge drives, you might need more -- but they've allowed an unlimited number of primaries so have no need for extended partitionss at all.

The original limit of four was set by the amount of space available. The Master Boot Record (MBR) on any hard drive that is partitioned with the original ms-dos scheme is exactly one sector, 512 bytes, in size. That's not a lot of space in which to provide the actual code for starting the boot process and also the partition table. They did manage to fit four partition entries in, but no more.

When it became apparent that more partitions would be needed, the extended partition came into being. It "occupies" all of the disk space needed by the additional logical partitions; it's usually defined to cover all the unused space so that any unallocated space is inside the extended partition. Otherwise, unallocated space outside of the extended partition would not be usable at all if all four primary slots were in use. The extended partition itself cannot be mounted; its only purpose is to allow the logical partitions' data to be stored outside of the MBR, at the start of the extended partition. All of the code that manipulates partition data knows how to get to this data when necessary; the operation is totally invisible to users most of the time.

---

### Post by 3xp10r3r|X13 on 2011-06-05
So, am I getting this right:

In future, we will probably be able (well obviously just if you buy one of the new hard drives) to have as many primaries as we want.

Extended and logical partition...I will miss you :)

That sounds pretty good to me

---

### Post by coffeecat on 2011-06-05
> **3xp10r3r|X13 said:**
> So why is it that the number of extended partitions possible would be only one?

Just to add to JKyleOKC's excellent explanations, I would pose the counter-question: why would you want more than one? In theory there is no  limit to the number of logical partitions you can have in one extended partition. Of course, that's absurd - can I have an infinite number of logical partitions on my 320GB drive, please? :wink: In practice you are unlikely ever to need as many logical partitions as is possible. Your real limiting factor is the size of the hard drive and your patience in creating the partitions.

> **3xp10r3r|X13 said:**
> In future, we will probably be able (well obviously just if you buy one of the new hard drives) to have as many primaries as we want.

Even the [GUID partition table (GPT)]("http://en.wikipedia.org/wiki/GUID_Partition_Table") has a limit of 128 partitions. And you can still use the MBR partition table scheme on new hard drives, although I believe the maximum size of drives that can be used with MBR is in the order of 2TB, but I'm happy to be corrected.

---

### Post by 3xp10r3r|X13 on 2011-06-05
I was just wondering if you could have more than one. So basically to understand, why they designed it this way(only able to have one extended partition). - just out of curiosity 

But you've just answered that question:

Because it is simply not necessary, because you can create ,"even with the GUID partition table", up to 128 logical partitions

---

### Post by coffeecat on 2011-06-05
> **3xp10r3r|X13 said:**
> Because it is simply not necessary, because you can create ,"even with the GUID partition table", up to 128 logical partitions

I don't believe that the primary/logical distinction is relevant to GPT disks. Until someone decides that 128 is too limiting, that is! :)

---

### Post by 3xp10r3r|X13 on 2011-06-05
Edit: Well, you're right. I got confused with all those partitioning :)

---

### Post by srs5694 on 2011-06-05
> **3xp10r3r|X13 said:**
> In future, we will probably be able (well obviously just if you buy one of the new hard drives) to have as many primaries as we want.

Essentially, yes, although technically, in GPT the term "primary partition" is as meaningless as "logical partition" -- they're all just "partitions."

Also, there's nothing "in the future" about it -- you can use GPT *today*. Most of my hard disks right now use GPT. The main limiting factor is Windows, which can't boot from GPT on BIOS-based computers. Windows requires UEFI to boot from a GPT disk, and UEFI systems are still a bit rare, although most of the new Sandy Bridge boards and some new AMD boards ship with UEFI. Also, Windows Vista and 7 can use UEFI on data disks, just not on boot disks, so even if you're using Windows on a non-UEFI computer, you can use GPT on a data disk so long as Windows boots from an MBR disk.

One caveat: If you're using older OSes (Windows XP, DOS, OS/2, BeOS, etc.), you're still stuck with MBR. The same is probably true of some current but obscure OSes.

re: more than one extended partition....

[quote=coffeecat]I would pose the counter-question: why would you want more than one?[/quote]

I can think of a couple of possibilities:


[list]
[*]In the process of partitioning and re-partitioning your disk, you end up with two isolated primary partitions, at least one of which is *not* at the start or end of the disk, so you've got two or even three blocks of free space. You want to create more than one partition in at least two of those blocks. This would require two extended partitions. The usual solution to this problem would be to move one of the primary partitions, but that might not always be practical (maybe the partitions are for obscure OSes whose partitions can't be easily moved and remain bootable), and there are always risks to moving data, so it would be safer to not do so even if it's possible.
[*]There are actually three extended partition type codes, each of which has slightly different capabilities. You might want to use two or even all three of those codes to support the needs of different OSes. This is most likely to be an issue if you're using a very old OS, such as an old version of DOS.
[/list]


Of course, in practice these are both pretty obscure issues.

As to why the one-extended limitation exists, I don't know. I don't know of any theoretical reason why it *should* be limited in this way, but as a practical matter few if any partitioning tools allow you to create multiple extended partitions. I don't know how Linux, Windows, or any other OS would react if it encountered such a disk.

[quote=coffeecat]In theory there is no  limit to the number of logical partitions you can  have in one extended partition. Of course, that's absurd[/quote]

Each logical partition requires one sector to define it, so in theory you could have a disk that consists of interleaved sectors of partition definitions and 1-sector partitions. The MBR needs a sector of its own, too. Thus, the theoretical limit is n/2 - 1, where n is the number of sectors on the disk. Most disks have an even number of sectors, so that'll be rounded down, and in practice it'll become n/2 - 2. Why you'd want to fill a disk with 1-sector partitions is another matter....

[quote=coffeecat]Even the [GUID partition table (GPT)]("http://en.wikipedia.org/wiki/GUID_Partition_Table") has a limit of 128 partitions.[/quote]

By default, yes. The specs allow this limit to be raised, and in practice it can be either raised or lowered. Few partitioning tools support such operations, though. In fact, I know of only one that does: my own [GPT fdisk (gdisk, sgdisk).](http://www.rodsbooks.com/gdisk/) Be aware: The last I checked, libparted contained a bug that caused tools based on it (such as GParted and GNU Parted) to flake out and claim the disk is unpartitioned when it has a GPT with anything other than 128 entries.

[quote=coffeecat]I believe the maximum size of drives that can be used with MBR is in the order of 2TB[/quote]

The limit is for partition start points and sizes of 2^32 sectors (2 TiB precisely, assuming 512-byte sectors). In theory, this means you can have a 4 TiB disk with two 2 TiB partitions (give or take a few sectors). In practice, most OSes that can handle such disks can also handle GPT, so there's no reason to even attempt to use MBR on disks larger than 2 TiB, IMHO. See [here](http://www.rodsbooks.com/gdisk/workarounds.html) for a bit more information on this topic. Thus, I generally just say that MBR is limited to 2 TiB disks. Since disk manufacturers aren't likely to ever release a disk that's precisely that size, but rather to jump from 2 TB (~1.82 TiB) to 3 TB (~2.73 TiB), the precise limit isn't really all that important.

---

### Post by 3xp10r3r|X13 on 2011-06-05
That just was a very detailed explanation. I think I got everything now

 :)

---

### Post by 3xp10r3r|X13 on 2011-06-05
Does Linux (talking about all Linux distributions, while I'm mostly interested in Slackware being able to handle GPT disks) support GPT ?

What OS are you running, when you're able to use GPT - Ubuntu?


edit: Is Linux able to handle them, although it runs on a BIOS based computer ?

---

### Post by srs5694 on 2011-06-06
> **3xp10r3r|X13 said:**
> Does Linux (talking about all Linux distributions, while I'm mostly interested in Slackware being able to handle GPT disks) support GPT ?

What OS are you running, when you're able to use GPT - Ubuntu?


edit: Is Linux able to handle them, although it runs on a BIOS based computer ?

GPT support has been available in the Linux kernel for about a decade, IIRC. Like many Linux kernel features, it's a compile-time option, so it can be present or absent in any given installation, at the discretion of whoever compiled the kernel. In practice, all the major modern distributions support GPT by default, but I can't make promises for most specific distributions. I'm certain that Ubuntu, Fedora, OpenSUSE, and Slackware all support GPT, and I'm pretty sure that Debian and PCLinuxOS do, as well. Gentoo tends to rely on locally-compiled kernels, so its support depends on the user.

The preceding refers to the kernel support, which determines whether or not the OS can provide access to the partitions. You also need boot loader support and support in utility programs to create and edit partition tables. See [this article](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) I wrote on the topic for details.

---

### Post by 3xp10r3r|X13 on 2011-06-06
You really are very informed about this topic. I liked your article a  lot, but unfortunately it showed me, that I probably won't be able to  use GPT... (well, maybe there is a possibility)

1. "LILO is not GPT-aware, so if your                 system uses LILO, you'll have to switch to GRUB&#8212;and the  story with                 GRUB is variable." -> I'm using LILO, which is the  default boot loader for Slackware (luckily you are able to use the GRUB  loader as well. But as you said, you're still at the mercy of your  distribution...

2. "The                 fdisk program and its variants will show you                 the protective MBR data, possibly along with a warning that GPT data has                 been detected."

damn it! Slackware uses fdisk and cdisk to set up partitions...

3. "The GPT creation tools of both GNU Parted and GParted are inherently                 destructive&#8212;if you've got an MBR disk, the only way to turn it                 into a GPT disk with these tools is to destroy your existing MBR                 partitions. If you want to convert an MBR disk in place, you could look                 into GPT fdisk, which is an fdisk-like tool for                 manipulating GPT partitions. GPT fdisk is very new and immature, however,                 so you should use it with caution. "

I wouldn't care to erase my partitions and walk through a fresh install,  but it seems as it's not that stable to turn your mbr disk into a  GPT one.

4. "Large file systems  support" - according to your volume and file size bench marks I've got  nothing to worry about this time :) (finally I found a positive aspect)

5. "This partition is not required if your computer uses BIOS to boot. " Hey, a BIOS has some advantages too.

6. "Linux is flexible enough that it won't be bothered by a disregard for                 these rules" Agreed!

7. "GPT is poised to become the standard for hard disk partitioning because of                 the size limitations of the MBR. Fortunately, Linux is well prepared for                 this transition. Although Linux users may have to give up certain tools                 (LILO and fdisk, for instance)" Come on...why does Slackware have to use those partitioning tools...

8. "You'll need to attend to                 your kernel configuration, your boot loader configuration, and the                 utilities you use to create and manage partitions. " Well I guess 2/3 are not enough...

Is there a possibility to make GNU parted available during the  installation process or is another solution just to configure the  partitions(using another tool), before the actual installation. So directly running "setup",  instead of partitioning first (assuming, you've already done that - on  the other hand, how are you going to tell Slackware, what the mount  points are?)

Suggestions?

PS: again - great article :)

---

### Post by srs5694 on 2011-06-06
> **3xp10r3r|X13 said:**
> 1. "LILO is not GPT-aware, so if your                 system uses LILO, you'll have to switch to GRUB—and the  story with                 GRUB is variable." -> I'm using LILO, which is the  default boot loader for Slackware (luckily you are able to use the GRUB  loader as well. But as you said, you're still at the mercy of your  distribution...

It's not all that hard to use a different boot loader from the one provided by your distribution *if* you plan it carefully and know what you're doing. The basic procedure is to set aside a partition (for GPT I'd use two -- one for the boot loader's files and one for the BIOS Boot Partition), manage it using whatever tools you like, and configure your distribution to ignore that partition except when *you* want to mount it to change its configuration files.

If you're dual-booting two Linux distributions, you could also be careful to set the other distribution's boot loader as the primary one, then not install (or install in some out-of-the-way place) the other boot loader. Then you'd manage the Slackware boot process from Ubuntu/Fedora/OpenSUSE/Mandriva/Debian/Gentoo/whatever.

Also, since writing that article I've run into claims that LILO *can* be made to work with GPT; however, my one attempt at that wasn't fully successful. As I recall, the kernel booted but then ran into problems with my LVM setup. It's unclear to me if this was really a LILO failure or if there was just something incorrect about the way I called my kernel. I haven't used LILO in any serious way for years, so I just dropped my investigation; it's just not important to me personally.

> 2. "The                 fdisk program and its variants will show you                 the protective MBR data, possibly along with a warning that GPT data has                 been detected."

damn it! Slackware uses fdisk and cdisk to set up partitions...

In general, if you prefer fdisk, you can use GPT fdisk (gdisk) in its place. I'm not that familiar with Slackware, but it sounds like there's a variant version that provides gdisk in the installer, as suggested by [this thread on LinuxQuestions.org.](http://www.linuxquestions.org/questions/slackware-installation-40/slackware-13-37-gdisk-choices-mbr-gpt-or-blank-gpt-872281/) There's no close replacement for cfdisk in the GPT fdisk family, though. If the Slackware installer works the way I vaguely recall, that could make adding GPT support to the installer in a seamless way a bit trickier than it could be.

> 3. "The GPT creation tools of both GNU Parted and GParted are inherently                 destructive—if you've got an MBR disk, the only way to turn it                 into a GPT disk with these tools is to destroy your existing MBR                 partitions. If you want to convert an MBR disk in place, you could look                 into GPT fdisk, which is an fdisk-like tool for                 manipulating GPT partitions. GPT fdisk is very new and immature, however,                 so you should use it with caution. "

I wouldn't care to erase my partitions and walk through a fresh install,  but it seems as it's not that stable to turn your mbr disk into a  GPT one.

Note the date of that article -- July, 2009. (I actually wrote it a month or two before that.) In the two years since then, GPT fdisk has matured, and I've seen few or no bug reports about its MBR-to-GPT conversion code. (Note that I'm GPT fdisk's author.) Thus, I wouldn't worry too much about the safety of an in-place conversion; however, I also wouldn't take it for granted that it'll work. At the very least, you should back up your MBR partition table with sfdisk ("sudo sfdisk -d /dev/sda > parts-sda.mbr") and save the backup somewhere safe. Particularly if you want to make other changes (like resizing partitions), backing up everything makes sense.

FWIW, the MBR-to-GPT conversion involves reading one sector of MBR data, plus one more sector for each logical partition, and using that data to fill in the information in the GPT data structures in memory. Those data structures, which occupy a total of 33.5 KiB, are then written to disk, 17 KiB of that at the start and 16.5 KiB of it at the end. Thus, we're not talking about large amounts of data or data locations that are likely to overwrite any important data structures in your filesystem unless you uncover a bug that causes GPT fdisk to write data where it shouldn't be writing it. Assuming that the original partition data structures get mangled in the conversion and are then written to the correct GPT locations, the original filesystem data will remain intact, so you'll be able to recover those partitions using the sfdisk backup.

> 5. "This partition is not required if your computer uses BIOS to boot. " Hey, a BIOS has some advantages too.

An EFI System Partition isn't required for booting a GPT disk on a BIOS-based system; however, if you're using GRUB 2, a BIOS Boot Partition is strongly recommended. (I didn't know much about BIOS Boot Partitions at the time I wrote that article, and I was still using GRUB Legacy on most of my systems then, so there's no mention of BIOS Boot Partitions in the article.)

> 7. "GPT is poised to become the standard for hard disk partitioning because of                 the size limitations of the MBR. Fortunately, Linux is well prepared for                 this transition. Although Linux users may have to give up certain tools                 (LILO and fdisk, for instance)" Come on...why does Slackware have to use those partitioning tools...

You'll have to ask the Slackware developers.

> Is there a possibility to make GNU parted available during the  installation process or is another solution just to configure the  partitions(using another tool), before the actual installation. So directly running "setup",  instead of partitioning first (assuming, you've already done that - on  the other hand, how are you going to tell Slackware, what the mount  points are?)

I'm afraid I can't answer these questions, except to refer to the LinuxQuestions post I found with a Google of "Slackware GPT". Also, the same Google revealed [this article](http://www.ehow.com/how_7769517_install-slackware-gpt-partition.html) that suggests preparing the disk ahead of time will do the trick.

I'm far from a Slackware expert; the last time I used it in earnest was in the mid-1990s. My comment that Slackware supports GPT was based on a VirtualBox installation I happen to have handy; I just booted it with a second virtual GPT disk "attached" to the "computer" and the booted Slackware (on an MBR "disk") could see the GPT partitions. Sorry I can't be of more help on that.

---

### Post by 3xp10r3r|X13 on 2011-06-08
thanks a lot for your detailed and I have to admit excellent explanations (although you didn't provide an answer for all of them, you offered more solutions, than I thought would be possible)

I hope in nearer future I will be able to convert my MBR to GPT and run damn lots of linux OSes :D.
> **srs5694 said:**
> 
"I'm far from a Slackware expert; the last time I used it in earnest was  in the mid-1990s. My comment that Slackware supports GPT was based on a  VirtualBox installation I happen to have handy; I just booted it with a  second virtual GPT disk "attached" to the "computer" and the booted  Slackware (on an MBR "disk") could see the GPT partitions. Sorry I can't  be of more help on that..


Don't be sorry, you really helped me out and keep in mind that this isn't even my thread (I just took it over)

According to your last sentences it seems as Slackware is GPT compatible :)

What distro are you using?

---

