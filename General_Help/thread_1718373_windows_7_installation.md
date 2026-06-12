---
title: "windows 7 installation"
date: 2011-03-31
forum: General Help
---

### Post by jmg158 on 2011-03-31
Okay, so I know there have been a post or two about this in the past but searching, I couldn't find what I was doing incorrectly. I suspect is was something basic I was overlooking. Here goes...

Earlier this year I came across an old computer, and taking a look at it, decided it would be a perfect opportunity to learn more about Linux, as I had never used it before. It was initially running Windows XP sp3 but I quickly overwrote that with Ubuntu 10.10 (32 bit).

However, a main function of my computer was to redirect my internet connection so that I could play on xbox live. Upon switching to Ubuntu, my only complaint was lag spikes that were quite frequent and regular. Finding no way to work around them, and in conjunction with what I can only describe as an unhealthy obsession with nhl 11... I have decided to reinstall windows (windows 7 this time) over ubuntu 10.10 and then reinstall ubuntu on the same disk so that both can be run from the same computer. 

Easier said than done I suppose though. I just got the windows 7 32 bit cd yesterday and was excited to throw it in, but apparently my hard drive partition was not formatted to NTFS standard. (I should say now that i'm not sure what this acronym means, but that this is the dialogue box opened when i was unable to install...)

Anyway, I went into ubuntu disk utility tool running from a flash drive and was able to sucessfully format the partition as NTFS... or so I thought. Upon running the cd again, I received the same error message. I've made other partitions with NTFS as well as making other partitions with other file formats and none are cable of receiving the installation. Last night around midnight I got frustrated and ragequit. 

I apologize for the drawn out narrative form, however I wanted to capture as many details as possible, for I do not know what may be causing this problem. If anybody has anything to say please let me know... keeping in mind that I still have plenty to learn about the ubuntu game.

Thanks a bunch guys

John

---

### Post by coffeecat on 2011-03-31
NTFS is the Microsoft filesystem that Windows uses. Or rather, what Windows has used since about 2000, give or take.

Windows 7 will quite happily install to a NTFS partition created in Ubuntu. I've done it myself. Also, you should be able to delete all partitions on the hard drive from the Windows 7 installer and create a partition formatted NTFS. This doesn't seem as though it was possible. So let's do some investigating.

Boot up your live Ubuntu USB drive and choose "try Ubuntu" to get you to the live desktop. Don't open Disk Utility. Work with Gparted, which is more flexible. Open System > Administration > Gparted and post a screenshot (press the PrintScreen/SysReq key) of the Gparted window showing your hard drive layout.

Also, open a terminal (Applications > Accessories) and post the output of this command:

```
sudo fdisk -lu
```
And then we can take it from there. This deserves some advance planning. My preferred way of working is to create one single NTFS partition for Windows (using Gparted) large enough for Windows but leaving unallocated space to be partitioned later for Ubuntu and whatever other partitions you want. Only after installing Windows would I do so.

You might find some useful information about partitioning here:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Be sure you understand the difference between primary, extended and logical partitions. It will save you hours of puzzlement later if you do! :)

---

### Post by Corsain on 2011-03-31
What is the capaacity of the harddrive :guitar:

---

### Post by Anonymous is Incognito on 2011-03-31
If one program doesn't work let's move on to another.

Let's disable swap first. Boot into the live CD or USB and get to a terminal. Now type;

```
swapoff -a
```

To switch off any swap space that is in use.

Now you can proceed to removing the partitions. My program of choice is cfdisk. **Be sure that you have backed up any data that you want to keep on the disk.**

```
cfdisk -z /dev/sda
```

The -z parameter tells cfdisk to skip reading the existing partition table. It will tell you something along the lines that /dev/sda -your 1st disk- is empty.

You can now create new partitions to your liking. Keep in mind that you can only create 4 primary partitions. Generally I put Linux at the start of the disk and Windows at the end. After those my Data partition is there.

---

### Post by jmg158 on 2011-03-31
Thanks guys, good information... I'll have to try that as soon as I can get home. 

First, let me say that I have no aversion to losing all of my data. All of the files I want are backed up properly and if I get to the point where I have to absolutely delete every partition I wouldn't mind it in the least. 

Yes, towards the end of my attempts last night I tried to work with partitions from the windows install cd with no success.

I tried gparted at first but when I ran into difficulty I figured that I should stick to a simpler interface (disk utility.) When I tried to make the partitions an error came up and I figured that there was no use using a program giving errors when I could work with a program that didn't give me any yet haha.  I'll try gparted again tonight. 

And yes, as far as primary extended and logical, i've only been making primary partitions which seems like what I would want but I suppose additional research couldn't possibly hurt.

Also, the hard drive is 120 gigs. Something else that I noticed... when I was on the windows live disk, when selecting a non nfts partition the error said something to the effect of "This is GTP, it should be NFTS" and when it was formatted nfts it said something like "This is GTP." So it looks like windows is recognizing a small difference but not necessarily exactly what i'm looking for. 

I've clearly got a lot of research to do today which I'll enjoy but I appreciate your guys' input. Thanks

---

### Post by coffeecat on 2011-03-31
> **jmg158 said:**
> Also, the hard drive is 120 gigs. Something else that I noticed... when I was on the windows live disk, when selecting a non nfts partition the error said something to the effect of "This is GTP, it should be NFTS" and when it was formatted nfts it said something like "This is GTP." So it looks like windows is recognizing a small difference but not necessarily exactly what i'm looking for. 

That's an interesting observation. Are you sure it said "GTP" and not "GPT"? If your hard drive has a GUID partition table (GPT) Windows 7 will be able to boot from it only if that is an EFi machine, not if it has a conventional BIOS. Perhaps that's why the Windows installer was having problems.

Was this hard drive used with an Apple Mac once? Intel Apple machines use GUID partition tables routinely. But if the HD has only ever been in an old PC it's odd that it should have a GPT rather than the commoner mbr partition table. Whatever, the output of fdisk will complain  if this is a GPT or if there is residual GPT data in the partition table. If so, there's a very easy fix - using Gparted! :)

By the way, you mentioned Windows install CD a couple of times. Windows 7 comes on a DVD. I just wanted to be sure that we're talking about the same thing.

---

### Post by jmg158 on 2011-03-31
@coffeecat

I think you're onto me. I'm not sure whether it was gpt or gtp. I thought it was gtp but i don't know what it would stand for and I can clearly see how the mistake would be made. I think I may have experienced a moment of sydlexia one way or the other. Either way though, this hard drive has definitely never been used with a MAC.

As far as the DVD/CD thing is concerned, I realize that it is a DVD. It was poor form of me to generalize.

---

### Post by srs5694 on 2011-03-31
To clarify and elaborate a bit on what coffeecat has said, GPT and MBR are competing partitioning systems -- they're different methods of carving up the disk into chunks ("partitions") that can be used for different purposes, such as a Windows boot partition, a Linux boot partition, and a Linux swap partition. A disk may use GPT or MBR, but not both (well, except for hybrid MBRs, but they're ugly, dangerous, and violate the GPT specs, so I'll ignore them for now).

The New Technology File System (NTFS) is a data structure that's placed *inside* a partition (defined by GPT, MBR, or other systems) to enable files to be stored. Other filesystems include the File Allocation Table (FAT) used by DOS and Windows 9x/Me, Linux's Second Extended Filesystem (ext2fs), and many others. The filesystem determines things like what filenames are legal and what sort of metadata (file creation times, ownership, permissions, etc.) are stored with files.

Any filesystem may be used with any partitioning system. Thus, NTFS can be used with either MBR or GPT. Some combinations are uncommon or impose limits, though. For instance, as coffeecat says, Windows can't boot from a GPT disk when the computer uses a BIOS, but this combination is fine on an EFI-based system. Thus, you're not likely to use NTFS in GPT with a BIOS-based computer, except possibly on a non-boot data disk.

The upshot of this is that the error message "this is GPT, it should be NTFS" is nonsensical, since the two aren't interchangeable concepts. It'd be like suggesting that sugar and an oven are interchangeable ingredients in a cake recipe. Although you might use both to make a cake, only sugar is an ingredient; the oven is used in a very different way. A more likely error message would be "cannot use NTFS as a boot partition on a GPT disk."

Part of the reason I'm babbling on about this is to illustrate why it's so important that you report error messages *completely* and *accurately*. A garbled error message is worthless. Similarly, in post #2, coffeecat asked for the output of "sudo fdisk -lu". This output (cut-and-pasted between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings or in a screen shot of the Terminal window) will tell us about how your disk is partitioned, which is critical diagnostic information. Without that information, the best anybody can do is guess about what's going on. The fdisk output will tell us more in a few lines than many paragraphs of symptoms reported in prose could possibly do.

---

### Post by jmg158 on 2011-03-31
@srs

Thanks man. That explanation was probably heavily warranted, as  hearing my discussion of these acronyms was probably like nails on a chalkboard to anyone who knew what I was saying. 

And yes, I plan on taking all the advice above (including copying and pasting the returned information) but right now I'm unable to get to my computer *cough cough* at work *cough cough*. I just tried to add all the details I could (incorrectly apparently) remember.

The reason I posted so early was because I honestly didn't expect a helpful response this quickly let alone so many helpful responses this quickly. (brace yourself for some something idealistic and cheesy) Responses like that one are exactly the reason that people take such pride in the Ubuntu community.

so once again haha, Thanks

---

### Post by jmg158 on 2011-03-31
alrighty, so I was able to check this, and you guys seem to have hit it on the head. 

```

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

Disk /dev/sdb: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3915775     1957872    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(956, 128, 32) logical=(948, 75, 32)

```


I think that first line pretty much says it all. So GPT.... how can I go about changing it from this partitioning format to MBR? or is that something out of my control?

also another question, if it was using GPT the entire time, how did it initially run Windows XP?

---

### Post by srs5694 on 2011-03-31
Your /dev/sda certainly looks like a GPT disk, and it seems that /dev/sdb is a small disk (probably a USB flash drive). My suspicion is that you accidentally converted /dev/sda from MBR to GPT form somewhere along the line. If I understand correctly, you don't currently have any data on /dev/sda that you want to preserve. If so, you can convert it back by using GNU Parted from a Linux emergency disc like [PartedMagic](http://partedmagic.com) or [System Rescue CD](http://partedmagic.com) (the Ubuntu installer might also work, but I'm not sure if GNU Parted is installed on it by default):

```

parted /dev/sda mklabel msdos

```

If you use an Ubuntu install CD, you'll probably have to use "sudo" to issue this command.

With this task done, you can create NTFS partition(s) for Windows, if you like, by using parted, the GUI GParted, or some other tool; or you can leave that job for the Windows installer.

If I've misunderstoood and you have data you want to keep on the disk, it may still be possible to convert from GPT to MBR non-destructively; however, that process carries some modest risks, and you'll have to re-install whatever boot loader you're using now. If this is the case, please post the output of the following command:

```

parted /dev/sda unit s print

```

Again, you'll probably have to use "sudo" if you run this from an Ubuntu install disc. In any event, this command will show what your GPT partitions are, which will reveal whether a conversion to MBR form is practical.

---

### Post by jmg158 on 2011-03-31
Alright guys, I really appreciate all your help. I successfully installed win7 on it right now and I'm looking at installing ubuntu back on it tomorrow night. For those of you who dual boot like this, how much would you suggest I leave for each operating system? Should I keep it with a 50/50 distribution?

---

### Post by coffeecat on 2011-04-01
> **jmg158 said:**
> Should I keep it with a 50/50 distribution?

That might mean you would be  keeping personal files on both the Windows and Ubuntu partitions. It's not a good idea to be regularly mounting and reading the Windows C: partition from Ubuntu - a better way  is to have a separate data partition formatted NTFS which can be used by both Windows and Ubuntu.

With a 120GB hard drive I'm guessing the  Windows partition you've created is 60GB, leaving you about 60GB (or approx 56 and 56 gibibytes). I wouldn't be comfortable with a Windows 7 partition of less than that. If you keep your personal files separate, an Ubuntu root partition of 15GB is adequate so once you've also created a swap partition, you could use the remaining as a data partition. 

This would be easily mountable from the Places menu in Ubuntu and Windows will see it as the D: or E: drive (or whatever letter is next in line).

You might also want to think of creating an extended partition in all the space left over from the Windows partition and making the extra partitions logical ones. Windows is booting from a primary partition but will be happy for the data partition to be logical and Ubuntu can boot from a logical partition. Doing it this way avoids having four primary partitions and gives you flexibility in the future if you ever need to change the partition layout.

---

