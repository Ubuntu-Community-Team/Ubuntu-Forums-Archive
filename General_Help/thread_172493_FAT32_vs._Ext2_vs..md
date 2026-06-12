---
title: "FAT32 vs. Ext2 vs. ???"
date: 2006-05-08
forum: General Help
---

### Post by benuski on 2006-05-08
Just a random newbie-esque question:

If I want to be able to write with both linux and Windows XP to an external hard drive that I'm going to load breezy badger on, should I use FAT32 or Ext2?  Or is there some other file system that works better.  Or should I just not bother and just format the external drive into one file system that works best with linux, like XFS or something, and just copy things over from my windows drive?

---

### Post by jazzmuzik on 2006-05-08
Either will work. Linux reads fat32 out of the box. For Windows you can download ext2 drivers to mount any ext2 partitions. One problem with fat32 is it doesn't store permissions and ownership info when being used from the Linux side. ext2 would be my choice because of that. However, you might consider which OS you use the most. If Windows, perhaps fat32 would be more convenient. Or vice versa if you mainly use Linux.

---

### Post by Omnios on 2006-05-08
Personaly I use a Vfat 32 drive which seems to fake permitions fairly well. I formated my vfat using linux terminal.

---

### Post by Gomez Akita on 2006-05-08
The easiest way I have found is to use FAT32 so booth operating systems can see the drive (not the most secure but it works well).

There are other options like installing the EXT2 driver for windows so it can see the Linux partitions, or fuselib for Ubuntu so it can see NTFS etc.

The choice is yours it can be done its just a matter of what suits you best.

---

### Post by Hoffmann on 2006-05-08
[QUOTE=benuski]Just a random newbie-esque question:

If I want to be able to write with both linux and Windows XP to an external hard drive that I'm going to load breezy badger on, should I use FAT32 or Ext2?  Or is there some other file system that works better.  Or should I just not bother and just format the external drive into one file system that works best with linux, like XFS or something, and just copy things over from my windows drive?[/QUOTE]

I formated my external HD as a FAT32 one, and I have successfully used it in both my Windows XP and Ubuntu partitions.

---

### Post by Forgotten on 2006-05-08
What I have done is basically partition my drive. one is FAT32 (for windows) and EXT3 (for linux)

From what I was told, thanks to everyone at the ubuntu irc channel, thats the way to go.

---

### Post by Hoffmann on 2006-05-08
In my case, I have the following partitions:

(1) NTFS (for Windows partition)
(2) EXT3 (for Linux partition)
(3) FAT32 (for  the External HD, which I use in both Windows and Linux partitions)

---

### Post by cvmostert on 2006-05-09
[QUOTE=Hoffmann]In my case, I have the following partitions:

(1) NTFS (for Windows partition)
(2) EXT3 (for Linux partition)
(3) FAT32 (for  the External HD, which I use in both Windows and Linux partitions)[/QUOTE]


I have it like this aswell, but how do i see the ext3 hdd in windows?

that is the problem...

any help would be greatly appreciated... i can view ext2 (with help of a program) but nut ext3

---

### Post by Hoffmann on 2006-05-09
[QUOTE=cvmostert]I have it like this aswell, but how do i see the ext3 hdd in windows?

that is the problem...

any help would be greatly appreciated... i can view ext2 (with help of a program) but nut ext3[/QUOTE]

Well, since a Windows partition is not so reliable (security problems, virus, etc.) I don't think you should access your linux partition from there. Why don't you do the oposite? I mean, to see your Windows partition from linux?

---

### Post by cvmostert on 2006-05-10
[QUOTE=Hoffmann]Well, since a Windows partition is not so reliable (security problems, virus, etc.) I don't think you should access your linux partition from there. Why don't you do the oposite? I mean, to see your Windows partition from linux?[/QUOTE]

a daly update of dapper broke something with my screen drivers and i could not fix it right away, i dont have my breezy cd anymore... iso on ext3 hdd. so i am working with windows until i can download the full dapper.

meanwhile i would like to access my music on the ext3 storage hdd. from win.

i have been using linux as primary os for quite a while... since hoary. 

i guess there is no way to get my music playd until june eh?

I cant even write from the ubuntu live cd.. dapper beta. 

permission problems... or the writer moans that theres not enough space on a empty disc?

all sorts of exitement....

thanx for trying to help.

ciao

---

### Post by Cirrocco on 2006-05-10
the driver found on this page: [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm")
allows windows xp to read/write to and ext2fs or ext3fs partition as if it were native.

---

### Post by cmanfu on 2007-10-14
Just be warned, the max file size supported by FAT32 is 4GB, as i learned the hard way.

---

### Post by LowSky on 2007-10-14
dude this post was from over a year ago...lol

---

### Post by cmanfu on 2007-10-21
haha true, but it may live on forever through search :)

---

