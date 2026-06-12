---
title: "Any reliable partition editor?"
date: 2011-02-26
forum: General Help
---

### Post by rva1945 on 2011-02-26
I need to expand the Linux partition and shrink the W XP partition.

I have Genome Partition Editor, Disk Utility and KDE Partition Manager installed.

Which one do you experts prefer?

BTW KDE Partition Manager tells me that I do not have administrative privileges, so what?


Thanks

---

### Post by 3rdalbum on 2011-02-26
Gparted (Gnome Partition Editor) is best. Just make sure  you have backed everything up before messing with partitions.

You need to run the partition editor as root, not as your ordinary user account - the menu item for Gparted should do this for you.

---

### Post by scouser73 on 2011-02-26
+1 for Gparted.

---

### Post by acrazyplayer on 2011-02-26
I really like "cfdisk" in the terminal

---

### Post by rva1945 on 2011-02-26
> **3rdalbum said:**
> Gparted (Gnome Partition Editor) is best. Just make sure  you have backed everything up before messing with partitions.

You need to run the partition editor as root, not as your ordinary user account - the menu item for Gparted should do this for you.

And do I have to unmount the partiion to be resized? Do I have to create a GParted Live CD to boot with the partitions previously unmounted, or can I use that Live CD to do all the related tasks (unmount, resize, mount)?

Excuse me for machinegunning all of you with my questions.

---

### Post by Mark Phelps on 2011-02-26
You can use the Ubuntu LiveCD to do all the partitioning work -- just be sure that none of the partitions from the drive are mounted.

GParted LiveCD tends to be newer, and it does not mount any partitions by default.  So, in some cases, it may work better.

---

### Post by gerowen on 2011-02-26
+1 for gparted.

---

### Post by rva1945 on 2011-02-28
> **Mark Phelps said:**
> You can use the Ubuntu LiveCD to do all the partitioning work -- just be sure that none of the partitions from the drive are mounted.

GParted LiveCD tends to be newer, and it does not mount any partitions by default.  So, in some cases, it may work better.

And how am I sure then none of the partitions are mounted?

---

### Post by coffeecat on 2011-02-28
> **rva1945 said:**
> And how am I sure then none of the partitions are mounted?

It will tell you with a padlock sign. It will "mount" the swap partition automatically, so you need to right-click on that and choose 'swapoff'. This is especially important if the swap is on a logical partition. While it is active your extended partition will be locked.

---

### Post by srs5694 on 2011-02-28
FWIW, all three of the partitioning tools that rva1945 mentioned are based on the same core: libparted. Thus, they differ mostly in their GUIs, although there are some other differences. AFAIK all GUI Linux partitioning tools are based on libparted, which means they've all got many of the same advantages and disadvantages. The biggest advantage of this family is that so many of them are GUI tools that integrate partition editing with filesystem editing. This makes them easy for newbies to use. I'd only apply the term "reliable" to them in a limited way, though. They tend to create valid partition tables and to be reasonably user-friendly; however, they also tend to flake out whenever there's the tiniest problem with an existing partition table. (Many of my posts to this forum are devoted to helping people work around such bugs.)

For resizing partitions, with *any* tool, a backup is an essential prerequisite. Even if the software is perfect, a power failure mid-resize is likely to wreak havoc. Furthermore, few programs are perfect, which makes a backup even more essential. Windows boot partitions can sometimes be rendered unbootable by libparted-based tools. I'm not positive, but I think this is because they sometimes try to move the start sector of the partition, and Windows is very sensitive about that. Thus, if you want to resize a Windows boot partition, you're best off using the Windows tools for this. You can then use a libparted-based tool for resizing your Linux partitions.

Other partitioning choices for Linux include the fdisk family and the GPT fdisk family. The fdisk family is a series of text-mode tools for managing Master Boot Record (MBR) and some other types of disks. The fdisk program is an interactive tool that writes its operations to the screen in such a way that they scroll by; cfdisk is an interactive tool that uses cursor-positioning commands similar to those of a text-mode text editor to update a single display; and sfdisk is a non-interactive program that you control via options on the command line. All three are less sensitive to partition table problems than is libparted, and so are more reliable, IMO, than any libparted-based tools. None of them is a GUI tool, though, and none of them manipulate filesystems -- for that task, you must use mkfs, resize2fs, and other tools. Resizing a partition with these tools entails resizing the partition and then resizing the filesystem, or vice-versa. Moving a partition with these tools can get tricky. (Note: There's a GNU fdisk that looks a lot like Linux fdisk, but GNU fdisk is based on libparted. IMHO, that's pointless; you get all of libparted's limitations and none of its advantages.)

The GPT fdisk family consists of gdisk and sgdisk, which are similar to fdisk and sfdisk, except that they work on GUID Partition Table (GPT) disks rather than MBR disks. (gdisk uses many of fdisk's commands, but sgdisk doesn't implement sfdisk's commands; sgdisk is thus more conceptually similar to sfdisk than it is modelled after it.) If you prefer the fdisk family to libparted-based tools on MBR disks, you'd probably prefer GPT fdisk to libparted-based tools for GPT disks; but if you prefer libparted-based tools on MBR disks, you'll likely prefer libparted-based tools on GPT disks, too. (One of libparted's strengths is that it handles both MBR and GPT disks, as well as some other formats, like the Apple Partition Map (APM) used on 680x0- and PowerPC-based Macs.) A disclaimer: I'm the author of GPT fdisk, so I'm not exactly unbiased. In fact, one of the reasons I wrote it was that I was fed up with libparted's GPT bugs (most of which have since been fixed).

Overall, I'd say that a GUI libparted-based tool, such as GParted, is a good option for somebody who's uncomfortable with command-line tools. It's also the best option for partition resizing under Linux. (Note the caveat about Windows boot partitions, though.) If you're a more expert user who needs better and more direct control of the partition's real data structures, or if you need to correct problems caused by any of the very many buggy partitioning tools out there, the fdisk or GPT fdisk tools will work better and be more reliable.

---

### Post by Primefalcon on 2011-02-28
I prefer gparted

---

### Post by rva1945 on 2011-02-28
Thanks. Now, if you were to give me a tip:

I have my HD partitioned in two, Windows XP and Ubuntu. A week ago something (I don't know) happened and both systems ceased to boot. By booting in Linux recovery mode, I fixed Ubuntu, but there was nothing I could do to repair the Windows XP boot: the screen with the progress bar vanishes after a couple of secs then the PC reboots.

There's no point in trying to use a MS tool because I can't boot in Windows, although I can access the Windows partition from Ubuntu. Booting with a W XP CD doesn't recognize the C: disk anyway.

Is there something I can do from Ubuntu?

Thanks

---

