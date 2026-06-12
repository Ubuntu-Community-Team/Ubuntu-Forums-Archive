---
title: "Restore data from sata hd partition"
date: 2010-09-04
forum: General Help
---

### Post by octohedra on 2010-09-04
Hello,

Ive installed ubuntu for the first time  today, i have a hdd of 500gb, that had 65gb occupied with music, movies and games.

What i did during installation:

it asked me where to install it, so i created a new partition of 100gb ext4 type, to install it there, and i was going to leave the rest for the data, but it wont let me do it, so i went back and selected the "exchange type swap linux 0x82 type" for the 400gb partition.

Then installed it, and now i cant find my data, and i have only 100gb of space in the hd, if i use the "disc utility" i can see the other 400gb, and change partition type, but i dont want to lose my data...

any advice is welcome,

---

### Post by octohedra on 2010-09-04
i was wondering if i could add another exchange type partition of 3gb, and change the partition type of the other 397gb..., but i would like to know what type of partition to chose...

thanks

---

### Post by coffeecat on 2010-09-04
You've rather lost me with what you've done partition-wise. I'm not sure what you mean by an 'exchange-type' but if that's a swap partition you may be misunderstanding what that's for. Linux uses a dedicated swap partition where Windows uses a swap file. You can't use it to store data and it only needs to be about 2GB in size, perhaps less and certainly no more than your available RAM. I really hope you don't have a swap partition of 400GB. :(

So that we can see what is going on, open a terminal (Applications > Accessories) and post the output of the command:

```
sudo fdisk -l
```It will prompt you for your password and nothing appears to happen as you type it in. That is normal. You'll want to copy and paste the output - the keyboard shortcut for a copy in the terminal is not ctrl-C, but ctrl-shift-C. (Or you can use the edit menu in the terminal).

---

### Post by octohedra on 2010-09-04
i've ubuntu in spanish, please excuse me if i dont translate it correctly.

yes i have a swap partition of 400gb lol

output of the fdisk -l

in spanish:

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000772d6

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       12158    97654784   83  Linux
/dev/sda2           12158       60802   390729729    5  Extendida
/dev/sda5           12158       60802   390729728   82  Linux swap / Solaris


translated:

/dev/sda1 start: yes start:1 end: 12158 blocks: 97654784 id: 83 system: linux.
/dev/sda2 start: no start :12158 end. 60802 blocks: 390729729 id: 5 system: extended
/dev/sda5 start: no start :12158 end. 60802 blocks: 390729729 id: 5 system: linux swap / solaris

---

### Post by coffeecat on 2010-09-04
The bad news is that you have reformatted the whole drive and your 65GB of data will no longer be accessible unless you use special recovery software. Even if you do that, the Ubuntu system you installed to the first 100GB partition may have overwritten some of these files, depending on where physically they were written.

Before you installed Ubuntu, what was the partition layout on the drive? Did you have Windows or was it just a storage drive?

Your fdisk output shows:

sda1 = partition 1, formatted with a Linux ext filesystem (probably ext4), 100 GB (93GiB) in size.

sda2 = partition 2, an extended partition with one logical partition (sda5) occupying the whole of it. sda5 is a Linux swap partition of 400.1 GB (373 GiB).

I hope you had your data backed up elsewhere. If not, and you need to recover the data, don't use that hard drive any more, to prevent any further writes to it. If you do need to recover the data, you need to attach that drive to another system, **or** boot up with the live CD and use the Ubuntu app testdisk. But, be warned, it is not easy for a newcomer to Linux.

Post back with what you want to do and I might be able to point you in the right direction, but I won't be able to talk you through testdisk - I have minimal experience of it.

---

### Post by octohedra on 2010-09-04
it was a storage drive, and i would like to restore some of the data, because i dont have it backed up... mostly music, books, photos and movies, and a few games.. but its my first time with linux and i think i wont be able to handle the recovery procedure... i mean, i just made a 400gb swap partition :(
i would like you to advice me of what to do.

Thanks

---

### Post by JedMeister on 2010-09-04
:o Oh no! I hope you didn't have anything important on there!? 

For future reference **ALWAYS** backup anything that you want to keep before you do potentially damaging disk activity (such as formating, partitioning, OS installation etc). You should still be able to recover some (if not all) of your data but the folders and filenames will be gone! I'd advise you to NOT start this PC again except from a live CD until you've recovered your data and if you haven't got one already, go and buy another harddrive (internal or portable - doesn't matter) or USB stick big enough for the files you want to recover. 

Have a look here for recovery info: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Sorry late reply - thats what happens when I'm replying to multiple threads at once. Looks like coffeecat is helping you out. I have used the recovery tools I link to above but as I said above all the folders and file names will be gone so you'll have to go through the files individually to work out what they are.

---

### Post by octohedra on 2010-09-04
yes i had very important stuff, specially books (ill get them somehow), music (and some very rare records, that i might not find again) and some photos... the movies/games are not important,

Maybe its a "signal" to start all over from 0?...  :KS

wish i could recover it without having to remember all those lines to type after booting from the live cd... or at least have a paper-copy...

---

### Post by coffeecat on 2010-09-04
> **JedMeister said:**
> Have a look here for recovery info: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Sorry late reply - thats what happens when I'm replying to multiple threads at once. Looks like coffeecat is helping you out. I have used the recovery tools I link to above but as I said above all the folders and file names will be gone so you'll have to go through the files individually to work out what they are.

@octohedra, I'm not sure I can add much to what JedMeister has said. Read the link and particularly the bit about using testdisk. If you boot from the live CD and can connect to the internet, you can install testdisk. It's installed to RAM in a live session so will be lost as soon as you power down, but at least you can use it while still using the live CD.

I'm sorry I can't be of further help because I only used testdisk/photorec once to recover non-critical data. I remember that photorec is not straightforward. You can use testdisk to restore a lost partition, but now that you've written to sda1 this may not be feasible - I really don't know. The app photorec is part of testdisk and can recover various types of files - not just jpegs. The problem with it is, as JedMeister says, your original file and folder names are gone. You'll get hundreds of files with obscure names which you then have to sort through by hand. Not a pleasant job.

This is the package information for testdisk:

>  TestDisk checks the partition and boot sectors of your disks.
 It is very useful in recovering lost partitions.
 It works with :
 * DOS/Windows FAT12, FAT16 and FAT32
 * NTFS ( Windows NT/2K/XP )
 * Linux Ext2 and Ext3
 * BeFS ( BeOS )
 * BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
 * CramFS (Compressed File System)
 * HFS and HFS+, Hierarchical File System
 * JFS, IBM's Journaled File System
 * Linux Raid
 * Linux Swap (versions 1 and 2)
 * LVM and LVM2, Linux Logical Volume Manager
 * Netware NSS
 * ReiserFS 3.5 and 3.6
 * Sun Solaris i386 disklabel
 * UFS and UFS2 (Sun/BSD/...)
 * XFS, SGI's Journaled File System
 .
 PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for
 * Sun/NeXT audio data (.au)
 * RIFF audio/video (.avi/.wav)
 * BMP bitmap (.bmp)
 * bzip2 compressed data (.bz2)
 * Source code written in C (.c)
 * Canon Raw picture (.crw)
 * Canon catalog (.ctg)
 * FAT subdirectory
 * Microsoft Office Document (.doc)
 * Nikon dsc (.dsc)
 * HTML page (.html)
 * JPEG picture (.jpg)
 * MOV video (.mov)
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
 * Moving Picture Experts Group video (.mpg)
 * Minolta Raw picture (.mrw)
 * Olympus Raw Format picture (.orf)
 * Portable Document Format (.pdf)
 * Perl script (.pl)
 * Portable Network Graphics (.png)
 * Raw Fujifilm picture (.raf)
 * Contax picture (.raw)
 * Rollei picture (.rdc)
 * Rich Text Format (.rtf)
 * Shell script (.sh)
 * Tar archive (.tar )
 * Tag Image File Format (.tiff)
 * Microsoft ASF (.wma)
 * Sigma/Foveon X3 raw picture (.x3f)
 * zip archive (.zip)I'd better say no more because if you need help with testdisk and photorec you need someone who has real experience of it.

---

### Post by octohedra on 2010-09-04
then i think ill start from 0, its too complicated, i dont have time. 
Could you please help me to fix the 400gb swap partition?

Thanks! :D

---

### Post by coffeecat on 2010-09-04
> **octohedra said:**
> Could you please help me to fix the 400gb swap partition?

Boot up with the live CD and open System > Administration > Gparted. You'll see sda5 listed as linux-swap (or whatever the Spanish is). Right-click on it and choose 'swapoff'. The live CD will have mounted the swap partition automatically and you can't resize it until it's unmounted - which is what you do with swapoff.

Now highlight the swap partition again, go to the Partition menu and choose 'Resize/Move'. In 'New size' (the middle box), type in the size you want - the size of your RAM is a good guide, but if you have more than 4GB RAM, the system will probably never use it anyway, so anything more would be wasted. Make sure 'free space preceding' (the first box) still shows zero otherwise you'll move the partition. Click in the third box and the 'free space following will be calculated for you. Now click on the Resize/Move button. The window will close and to write those changes to the HD you need to click on Apply, which is the button in the shape of a green tick.

You'll now have up to 400GB of free space in your extended partition in which you can make as many logical partitions as you want. Had you any ideas what to do with them?

---

### Post by octohedra on 2010-09-04
did what you said, but after resizing the swap partition to 2gb, i cant resize the first one, i can make it smaller, but not bigger, its as if it doesnt see all the unallocated space...

what should i do?

Now it looks like this:

Device start/boot    start      end      blocks  Id  system
/dev/sda1   *           1       12158    97654784   83  Linux
/dev/sda2           12158       60802   390729729    5  Extended
/dev/sda5           12158       12413     2050590+  82  Linux swap / Solaris

---

### Post by coffeecat on 2010-09-04
OK, right, you didn't say you wanted to resize the first partition. The reason you can't add the unallocated space to partition 1 is that they are not contiguous - that mean physically continuous on the drive. What you'll have to do is to move the swap partition to the end, but that means moving the extended partition. Easier and quicker would be to remove the swap partition, resize sda1 and then create a new swap partition.

Here's what you do:

Backup any data you might need onto a separate drive. We're going to resize your Ubuntu root partition. This should work without incident but any manipulation of partitions runs the small risk of data loss.

Boot up the live CD and go into Gparted again. Do the swapoff trick with the swap partition. Now delete firstly sda5 and then sda2. Click on the green tick to write the changes to the disc. Highlight sda1 and choose Resize/Move from the Partition menu. Change the number in the 'new size' box so that it leaves the exact size you want the swap partition to be in the 'free space following' box. Click on the Resize/Move button and now click on the green arrow. You might as well go and do something else now because this might take a long time.

Once sda1 has been resized, click on the unallocated space and create a swap partition. If you only want the two partitions, you might as well make this a primary, rather than make an extended with a logical inside.

One comment though. One huge nearly 500GB root partition with a swap limits your flexibility for the future. Personally I like to set up a number of much smaller partitions so that I can try different distros or versions of Ubuntu in a multiboot and have a larger shared data partition.

Anyway, if you are happy with the simple two partition layout, there is one more job to do. Boot into your hard drive Ubuntu. You may get an error message because it can't find the old swap partition. Post the contents of your /etc/fstab file and the terminal output of:

```
sudo blkid
```A simple edit of /etc/fstab should put things to right - I'll tell you what to do.

**Edit**: thinking about it, there is a simpler alternative. You could make a separate partition for data in the freed space. 100GB is **huge** for a Linux root partition if you have a separate data partition, but it might do for now. Particularly if you are like me and are likely to want to rearrange and reformat the whole drive occasionally. Tell me what you want to do and we'll take it from there.

---

### Post by octohedra on 2010-09-04
I would like to go the easy way first, its my first time with ubuntu, im lovin it and im not thinking on installing windows again, so i would like to follow your advice and create many partitions in that free unallocated  space.

what should i do? Can i do it with the disc utility without booting from the cd? :D

I also want to create another partition for ubuntu, as you said that 100gb its too much for a ubuntu root installation, maybe 30gb ?

Thanks

---

### Post by coffeecat on 2010-09-04
You can use Disk Utility but the partitioning tool is fairly basic. I'm not sure whether it can create logical partitions. It can certainly create primary partitions but unless you resize the extended you won't be able to create any primaries.

You can install Gparted to your hard drive to save booting up from the liveCD.

Since you've got a lot of questions about partitions it might be better if you read this guide first:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Follow all the links and have a think about it before you do anything. Partitioning is a complex subject so it deserves some thinking time. I think you'll find that guide answers most of your questions.

Good luck!

---

### Post by octohedra on 2010-09-04
Thanks coffeecat, now my hdd looks like this:

[IMG]http://img28.imageshack.us/img28/197/pantallazomq.png[/IMG]

looking good?

---

### Post by coffeecat on 2010-09-04
It'll certainly give you some flexibility for the future. And it was a good idea of yours to label the partitions. That's very useful when you come to mount them or search for them in the Places menu. If there's a partition label the system uses it.

Interesting that the Spanish for label in this context is etiqueta. The English word etiquette has quite a different meaning. Or rather the French loan word etiquette has a different meaning in English. We have a lot of French loan words in English - ever since the Norman French invaded us in 1066. We've never forgiven them! :wink:

**Edit:** I've just looked in my French dictionary and the English translation for the French word etiquette is given as 'label'. I never knew that. Seems the word must have changed its meaning as it came across the English channel. Or 'La Manche' as they call it over there. :)

---

### Post by octohedra on 2010-09-04
i assume that your first thought was correct, as etiqueta *literal *translation is label, we dont use it like that in spanish, for example we say "Partition name" instead of "partition label", we use the word "Etiqueta" for things like this:

[IMG]http://www.camisetas-baratas.com/img/concurso-etiquetame/concurso-camisetas-baratas.jpg[/IMG]
the white thing in the middle is the "Etiqueta", provides size and other info...

Personally i like english a lot more than spanish, i even think in english half of the time, its much easier, dynamic, flexible language than spanish, we have tons of dumb rules, and even letters that dont sound and still have to use them for writing, aswell as useless verb forms, useless rules for letter combinations, etc...

---

