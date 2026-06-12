---
title: "Partitions have vanished"
date: 2012-04-05
forum: General Help
---

### Post by Carllacan on 2012-04-05
Hi!

Briefly: GParted shows me a drive without any assigned partitions, though I can start Ubuntu and see my data partition. Any idea about why this happens?

Here is my situation: I had 4 partitions on my hd: one for Ubuntu, one for Win7, one for Windows Recovery (set by default) and one for data, the biggest one. They were set up using GParted

I wanted to move the Ubuntu partition so I could make a little bigger the data partition, but I couldn't do it being on Ubuntu, so I started Windows, downloaded Partition Magic and tried to edit them. But Partition Magic said there was a problem with the partition table, did I wanted to fix it? I (perhaps stupidly) accepted and PM fixed whatever it was. Nevertheless, once PM had already fixed the error, still wasn't able to work properly, as it claimed to be unable to find the letter of a drive.

So I gave up with PM and tried GParted instead, making a USB Live. I restarted, configured the computer to boot from USB as first option, restarted... and there wasn't any GParted boot, just the usual GRUB selector. So I thought I would start Windows again and remake the USB installation. But Win7 was unable to start, and I tried using the recovery environment to repair it. As the recovery didn't worked either, I decided to just go to Ubuntu and get rid of the whole Windows stuff (that is, to delete OS partition and the recovery partition).

Now, when I open GParted, it shows a empty drive, without assigned partitions. Weirdly, I still bieng able to start Ubuntu normally and to access to the data partition, while the Win7 partition seems to have vanished.

Now, what could I do now? I just want to have the Ubuntu and Data partitions, but GParted is unable to do anything.

Help please!

---

### Post by Paddy Landau on 2012-04-05
This is a weird one. I cannot tell you what is going on.

In your case, I would repartition the drive from scratch, reinstall Ubuntu, and restore my data. Of course, this presumes you already have a backup, as repartitioning would destroy any data.

---

### Post by satyaminvi on 2012-04-05
Try to format the system and reinstall all the operating systems again. :p

---

### Post by satyaminvi on 2012-04-05
> **Paddy Landau said:**
> This is a weird one. I cannot tell you what is going on.

In your case, I would repartition the drive from scratch, reinstall Ubuntu, and restore my data. Of course, this presumes you already have a backup, as repartitioning would destroy any data.
I guess you r right . 
;)

---

### Post by santosh83 on 2012-04-05
> **Carllacan said:**
> Hi!

Briefly: GParted shows me a drive without any assigned partitions, though I can start Ubuntu and see my data partition. Any idea about why this happens?

Here is my situation: I had 4 partitions on my hd: one for Ubuntu, one for Win7, one for Windows Recovery (set by default) and one for data, the biggest one. They were set up using GParted

What about the swap partition for Ubuntu? Did you allocate one?

> I wanted to move the Ubuntu partition so I could make a little bigger the data partition, but I couldn't do it being on Ubuntu, so I started Windows, downloaded Partition Magic and tried to edit them.

What was the order of the partitions on your disk, before you started having these issues?

Was your HDD using MBR partition format or GPT format?

> But Partition Magic said there was a problem with the partition table, did I wanted to fix it? I (perhaps stupidly) accepted and PM fixed whatever it was. Nevertheless, once PM had already fixed the error, still wasn't able to work properly, as it claimed to be unable to find the letter of a drive.

So I gave up with PM and tried GParted instead, making a USB Live. I restarted, configured the computer to boot from USB as first option, restarted... and there wasn't any GParted boot, just the usual GRUB selector.

Which distribution did you use to make your GParted bootable USB?

 > So I thought I would start Windows again and remake the USB installation. But Win7 was unable to start, and I tried using the recovery environment to repair it. As the recovery didn't worked either,

In each case what if any were the error messages displayed? Did you get to the Grub menu screen without problems?

>  I decided to just go to Ubuntu and get rid of the whole Windows stuff (that is, to delete OS partition and the recovery partition).

Now, when I open GParted, it shows a empty drive, without assigned partitions. Weirdly, I still bieng able to start Ubuntu normally and to access to the data partition, while the Win7 partition seems to have vanished.

Did you try displaying your partitions using other tools like *sfdisk* (try sfdisk -l /dev/sda or /dev/hda to display partitions and sfdisk -V /dev/sda or /dev/hda to make it do a consistency check) or *fdisk*? Do they report the same kind of errors gparted is showing? What does the output of *mount* command display? Also try *cat /proc/partitions*.

> Now, what could I do now? I just want to have the Ubuntu and Data partitions, but GParted is unable to do anything.

Help please!

The last time did you try the GParted from within your Ubuntu system (which will not allow modifications since partitions will be mounted) or from a LiveCD/USB?

Your problem seems to be some sort of strange mess-up caused by a combination of different tools. Your best bet might be to just backup any data and reinstall.

---

### Post by Mark Phelps on 2012-04-05
From first glance, it looks like Linux filesystem utilities can't make any sense of your drive -- which would be true in either of the following cases:
1) Your Windows partitions got converted from Basic Disks to Dynamic Disks -- which would happen AUTOMATICALLY if you had added another partition when you already had four
2) Your Windows filesystems got corrupted big-time, to the degree that the Linux utilities simply can't read them anymore.

Since you can't get into Win7 to see the partitions, and Linux doesn't appear to see them either, my recommendation is to use either of the following MS Windows utilities (after downloading the ISO image and burning that to CD):
1) EASEUS Partition Master
2) Minitool Partition Wizard

These should both be able to see and manage the Windows partitions.  Partition Magic hasn't been out in years, so I don't know if it's any good anymore.

---

### Post by Carllacan on 2012-04-07
Ok, thank you all very much for your answers and your interest. I guess my better option is to format the HD and reinstall everything from scratch. The only problem is that I don't have any place to move my DATA, so I think I will try some other things first, like those ones Mark Phelps talks about (thanks).

I think the whole problem came with Partition Magic trying to fix the info in the partition table. GParted never said anything on that, and everything went fine. Isn't there some way to make GParted "look" at the drive and figure out how partitions were configured? I see it has a "Try to recover data" function, could that help me?

About santosh83 questions:
> What about the swap partition for Ubuntu? Did you allocate one?
I don't remember doing it when I installed Ubuntu. If I configured such a partition, though, GParted never showed it.

> What was the order of the partitions on your disk, before you started having these issues?
If I'm not wrong, it was: 
1) Win7 recovery environment
2) Win 7
3) Empty space
4) Ubuntu
5) Data partition

That empty space came from shrinking Win 7 partition. It was then when I wanted to move Ubuntu in order to increase Data's size. 

> Was your HDD using MBR partition format or GPT format?
I'm sorry for my ignorance, but that sounds to me like if you were talking Japanese :roll:

> Which distribution did you use to make your GParted bootable USB?
I did it in Windows Seven...
> In each case what if any were the error messages displayed? Did you get to the Grub menu screen without problems?
The Grub starts without any problem at all. It even shows me the Windows 7 and the Recovery tool options. When I select any of them, though, I get to a screen telling me that Win 7 is unable to load. When I choose the "Try to repair" option, though, it is unable to do anything.

> Did you try displaying your partitions using other tools like sfdisk (try sfdisk -l /dev/sda or /dev/hda to display partitions and sfdisk -V /dev/sda or /dev/hda to make it do a consistency check) or fdisk? Do they report the same kind of errors gparted is showing? What does the output of mount command display? Also try cat /proc/partitions. 
sfdick -l /dev/sda shows me this 
```
Disc /dev/sda: 77825 cilindres, 255 capçals, 63 sectors/pista
Unitats = cilindres de 8225280 octets, blocs de 1024 octets, contant des de 0

   Disp. Arr.  Inici     Final #cil.    #blocs    Id  Sistema
/dev/sda1          0+   3263    3264-  26217056   1c  W95 FAT32 (LBA) oculta
/dev/sda2   *   3263+   9000    5738-  46085108+   7  HPFS/NTFS/exFAT
/dev/sda3      36682+  77825-  41143- 330480640    7  HPFS/NTFS/exFAT
/dev/sda4      28862+  36682-   7821-  62814208   83  Linux

```
sfdick -l /dev/sda says "Warning: partitions 1 and 2 overlap" (actually I don't know if overlap is the right word, I have Ubuntu in catalan and he says "encavalquen", but I'm pretty sure is the right translation)

With /dev/hda I get an error: such directory doesn't exists, either I try with -l or -V.

> The last time did you try the GParted from within your Ubuntu system (which will not allow modifications since partitions will be mounted) or from a LiveCD/USB? I first made the partitions while installing Ubuntu from a Live CD, and since then I used GParted from within Ubuntu.

PD: Thanks again for the answers. And, by the way, Im sorry if I make any grammar mistakes, English is not my mother language.

---

### Post by oldfred on 2012-04-07
Overlapping partitions is one reason gparted will not show a drive as the corruption creates issues it cannot resolve.

Run this as what you have posted does not necessarily show overlap. This shows more detail by sectors.

```
sudo fdisk -lu
```You should also backup partition table just in case.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Fix overlaping partition error srs5694 post #34
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

But you may just have to use sfdisk. The issue is, if partitions overlap which partition does the overlap belong to and does it contain any data from one, or the other, or both and is corrupted? 
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

---

### Post by Carllacan on 2012-04-25
Ok, I've been researching a bit about everything you told me and I think olfred has it right: I have overlapping partitions. Concretely It is the windows recovery environment the overlapping one. I'll show you:
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb33d55e5

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1            2048    52436159    26217056   1c  W95 FAT32 (LBA) oculta
/dev/sda2   *    52430848   144601064    46085108+   7  HPFS/NTFS/exFAT
/dev/sda3       589301760  1250263039   330480640    7  HPFS/NTFS/exFAT
/dev/sda4       463673344   589301759    62814208   83  Linux

```As I understand it sda1 ends "over" sda2. I think it is almost definetely Partition Magic's fault, it told me there was a problem with a partition and that it was going to "fix" it. 

So, I'm thinking on using sfdisk to copy the table to a .txt, edit it, and load it to disk. Only problem is that I don't know exactly how to edit it. I mean, should I shrink sda2 (modify its starting position) or sda1 (modifying its ending position)?

My guess is sda1, as sda2 is bootable and that could lead to problems, could'nt it?

Thanks everyone.

---

### Post by oldfred on 2012-04-25
The first sector of a partition is like the first sector of a drive in that it has boot info. For NTFS partitions it must match the partition table and have a valid NTFS signature. So moving the start of a NTFS partition will definitely create problems.

But do not know what the end of sda should be. You might try looking in testdisk as it finds old partitions, but it reports the info in the old cylinders, heads, sectors and it is not easy to relate. But if you want to see what it says:

Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

---

### Post by Carllacan on 2012-04-26
> **oldfred said:**
> The first sector of a partition is like the first sector of a drive in that it has boot info. For NTFS partitions it must match the partition table and have a valid NTFS signature. So moving the start of a NTFS partition will definitely create problems.

But do not know what the end of sda should be. You might try looking in testdisk as it finds old partitions, but it reports the info in the old cylinders, heads, sectors and it is not easy to relate. But if you want to see what it says:

Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

I'm sorry, I don't understand what you're talking about. Isn't sda the whole drive? Or do you mean sda1?

If you mean sda1, I think (according to what I have been reading lately) that I can find out what the end position should be by just adding the size of the partition to the start position (that makes sense for me). If I do like this, however, it seems to be a large gap between sda1 and sda2, so I don't know if it is wrong or right.

About testdisk, what for should I use it? To recover the partition table or just to get info?

Thanks.

---

### Post by oldfred on 2012-04-26
Yes, I meant sda1.

I would use testdisk to see if it shows a sda1 that does not overlap sda2.  It it does and looks reasonable then I would see if it would update. But save the current partition info, so you could revert and manually do it if necessary.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by Carllacan on 2012-05-02
I think I'm just gonna use sfdisk to shrink sda1 and the gparted to get rid of windows. ¿Any warning i should keep on mind while doing it?

And, by the way: ¿will it be any problem if, using gParted, I erase a bootable partition? I so, ¿what if I do it from a Pangolin live cd and then I use it to install PP in a new partition? ¿Will it automatically become bootable?

Thanks everyone, you're being really helpful.

---

### Post by Paddy Landau on 2012-05-02
If you delete the bootable partition, that's not a problem, as Ubuntu will fix it when you install.

However, if you are keeping Windows, that may cause a problem particularly if you need to restore Windows -- Windows tends to use hidden partitions to store restoration data.

---

### Post by Carllacan on 2012-05-02
It's not a big deal if I lose Win7, but I'd like to keep it... ¿will it crash even if I just shrink his hidden partition?

---

### Post by Paddy Landau on 2012-05-02
Messing with Windows's partitions is tricky. You do so at the risk of losing Windows.

Windows is terribly fussy.

Here is what I suggest:


[LIST=1]
[*]Reinstall Windows. *Warning:* This will delete all data on your disk, probably including your Ubuntu data, so be sure to **back up all your data first**.
[*]Use Windows tools (from your Administration menu) to shrink the main Windows partition to the size you want. It is safer to shrink your Windows partitions using Windows tools rather than Linux tools. This will leave spare, unused space on your hard drive.
[*]Finally, install Ubuntu in the spare space that is left on your drive.
[/LIST]

You do not have to do it that way. But in any case, please back up all your data first, in case of any problems.

---

### Post by Carllacan on 2012-05-04
Well, I've finally fixed it!

At the end I've just edited the Partition Table to shrink sda1 with sfdisk (I've never been more frightened!) and then I just got rid of my ubuntu partition and I've created a new extended one, where I've installed Pangolin from scratch (it's currently being installed, in fact).

So it seems everything is gonna be ok :-)

I cannot thank you all enough for such a kind and useful help. Thanks everyone!


PD: it seems I've lost sda1, or at least Windows Recovery is no going to work anymore, but I really don't mind, I think I will make it a extended partition and use it to try other OS :-)

---

### Post by Paddy Landau on 2012-05-05
I'm glad you managed to resolve this. It was a bit of a confusing problem.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Carllacan on 2012-05-06
For eveyone coming here with alike problems: Olfred's answer was very very helpful:

> **oldfred said:**
> Overlapping partitions is one reason gparted will not show a drive as the corruption creates issues it cannot resolve.

Run this as what you have posted does not necessarily show overlap. This shows more detail by sectors.

```
sudo fdisk -lu
```You should also backup partition table just in case.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Fix overlaping partition error srs5694 post #34
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

But you may just have to use sfdisk. The issue is, if partitions overlap which partition does the overlap belong to and does it contain any data from one, or the other, or both and is corrupted? 
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

---

