---
title: "running fsck often"
date: 2010-03-22
forum: General Help
---

### Post by brandon89 on 2010-03-22
hey so this has been a recurring problem for me and i have no idea whats causing it.  ill be using my laptop, just browsing the internet or listening to music, nothing too cpu or hdd intensive when all of a sudden something will freeze.  either it be the browser (chrome) or open office, w/e, it will just freeze.  i will try to close it but then ill get the standard "force quit" dialog but there will be no buttons or text.  if i try to open any program it will not load.  also, if i try to reboot or shutdown i get the dialog box but with no text or buttons or anything.  

so im forced to hardreset (shutdown).  grub will load and ill choose the newest kernel that has been release (this has happened on previous releases as well) and it will attempt to load.  i think i usually get to the white ubuntu logo when all of a sudden that fails and i get some error message that i think says something about a failed mount.  it instructs me to press control-D which i do, but then that fails as well and it then says for me to run fsck manually.  i run that (by just typing fsck) and then it goes through and i have to repair a bunch of inodes, block bitmap differences, free blocks count wrong for group #xx, ect.  

this is getting pretty annoying so i was wondering what would be the cause of this and how might i go about fixing it?  thanks for any help

---

### Post by Chronon on 2010-03-22
Random freezing seems pretty non-specific.  Can you find any info in the system logs?  Running memtest might be a good plan too.

---

### Post by Herman on 2010-03-22
I prefer to run e2fsck rather than just fsck, but that's up to you.

The following command includes my favorite file system check options,
```
e2fsck -C0 -p -f -v /dev/sda1
```Where: "/dev/sda1' is the partition containing trhe file system I want to check.

Most of the time that should fix everything. If it can't it will at least give you a nice informative error message.

If you need to run e2fsck with the -y option very often it could be a sign that your media (hard disk) is failing.
You should take a look at it with the Palimpsest Disk Utility ('System'-->'Administrations'-->'Disk Utility'), and run a badblocks check on it.
```
sudo badblocks -sv /dev/sda1 >> badblocks.report
```If the badblocks command above reveals bad blocks in your hard disk it will print their details in the file called 'badblocks report', an empty file is a pass, one or two badblocks might be forgivable but a long list probably indicates trouble and you should consider replacing the media as soon as possible.
Certainly you should make a backup of all your data, (you should always be doing that anyway).

---

### Post by Herman on 2010-03-22
```
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options). 
```If the e2fsck command in the previous post can't correct your file system problems, you may see this feedback, (above).

It's trying to tell you you need to run a command like the one below, which I olny resort to when things get tough,
```
sudo e2fsck -y -f -v /dev/sda1
```This command can result in files being moved to your lost+found.

There's also this one for dealing with bad blocks, 
```
sudo e2fsck -cc -k -v /dev/sda1
```This command is for telling your file system where the badblocks are so it can avoid them, and may stave off the inevitable for just a little bit longer.

---

### Post by Herman on 2010-03-22
If your hard drive passes the badblocks test you might also want to run some other diagnostic tests such as memtest86+ from your GRUB Menu and watch for voltage fluctuations in your motherboard in case there's a power problem.

[memtest86+]("http://members.iinet.net.au/%7Eherman546/p15.html#Memtest86").

[System Health Check]("http://members.iinet.net.au/%7Eherman546/p1.html#System_Health_Check")[FONT=Arial].


[/FONT]

---

### Post by brandon89 on 2010-03-22
ok so i ran memtest and my laptop passed just fine.  i checked in the bios, but i dont i have a "System Health Check" option, but ill look again.

when i open up Palimpsest Desk Utility, heres what it looks like (btw im dual booting vista and ubuntu)

[[IMG]http://img690.imageshack.us/img690/2752/disk1t.th.png[/IMG]](http://img690.imageshack.us/i/disk1t.png/)

[[IMG]http://img682.imageshack.us/img682/7140/disk2.th.png[/IMG]](http://img682.imageshack.us/i/disk2.png/)

[[IMG]http://img682.imageshack.us/img682/6592/disk3.th.png[/IMG]](http://img682.imageshack.us/i/disk3.png/)

[[IMG]http://img297.imageshack.us/img297/5281/disk4.th.png[/IMG]](http://img297.imageshack.us/i/disk4.png/)

also, how do i determine which sda# im currently using?  i think its sda5 since when i tried doing that it said i was already mounted and it would cause severe damage if i continued...i did not continue :P.  where do i run the e2fsck from?

one more thing, the disk utility wont allow me run a bad sector test on the hdd.  everything at the top is grayed out

---

### Post by Herman on 2010-03-23
Your 'System Health Check' might be there under some different name, most computers have something like it there is the BIOS somewhere.

> also, how do i determine which sda# im currently using? i think its sda5 since when i tried doing that it said i was already mounted and it would cause severe damage if i continued...i did not continue :razz:.  where do i run the e2fsck from?
You should never run a file system check on a file system while it's mounted.
Most people do this from a live CD or a different Linux installation, like from a different partition or disk or from a USB installed Linux or something like that.

The easiest way if you have your Ubuntu 'Desktop' Live/Install CD is to open GParted, right-click on the partition to be checked and click 'check', (from the right-click menu).

The command line way to tell which partition you want to check is with either the 'sudo blkid' command or 'sudo fdisk -lu'.

---

### Post by Herman on 2010-03-23
The Palimsest Disk Utility reads the hard disk's own recorded log files.
The badblocks command tests your hard disk directly and is a better way to tell if your hard drive is going bad or not.

From your screencaps of your Palimpsest output it looks to me like your hard disk may be getting a little hot sometimes, you might want to get your laptop cleaned out.
Often they get blocked with lint, (like you see in the air filter of a clothes dryer), especially when people use them on beds like you see done in trendy advertisements. 
People forget that the laptop's fans and air intake vents are often underneath.
It's a good idea to use your laptop on a hard surface like a table so the air vents will not be blocked or suck up lint, and even have it raised up on something so there's plenty of cooling air space between your laptop and the table top. They also like to suck up spilled liquids, and the habit of raising it up clear of the table top might avert a disaster some day, you never know.

It's not for sure yet that your hard drive is on the way out, but I'd be keeping an eye on it and making extra backups just in case. Try to keep your hard disk drive running cooler and see what happens.

Try a file system check and a badblocks command from a live CD. :D

---

### Post by brandon89 on 2010-03-23
alright so i created a live cd and ran the badblocks test as well as the disk check.  here are the results of the disk check

```
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e

Check and repair file system (ext4) on /dev/sda5  00:00:26    ( SUCCESS )
    	
calibrate /dev/sda5  00:00:00    ( SUCCESS )
    	
path: /dev/sda5
start: 122977638
end: 453386429
size: 330408792 (157.55 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:26    ( SUCCESS )
    	
e2fsck -f -y -v /dev/sda5
    	
Superblock last mount time is in the future.
(by less than a day, probably due to bad system clock last boot) Fix? yes

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****

298326 inodes used (2.89%)
2873 non-contiguous files (1.0%)
229 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 267178/144
6066017 blocks used (14.69%)
0 bad blocks
1 large file

221962 regular files
38086 directories
68 character device files
26 block device files
0 fifos
489 links
38162 symbolic links (30887 fast symbolic links)
13 sockets
--------
298806 files
e2fsck 1.41.9 (22-Aug-2009)
grow file system to fill the partition  00:00:00    ( SUCCESS )
    	
resize2fs /dev/sda5
    	
resize2fs 1.41.9 (22-Aug-2009)
The filesystem is already 41301099 blocks long. Nothing to do!


```

the badblocks test also returned 0 bad blocks.  

i know that my hdd is running a little hot. for some reason when im running ubuntu, the temperatures rise a bit.  im buying a passive laptop cooler that will hopefully help with this.  

so does everything seem to be ok for the time being?

---

### Post by Herman on 2010-03-23
:D Everything looks fine as far as I can see, judging from the information you posted.

I'd say just keep on monitoring the situation and try to keep your laptop as cool as possible, getting a passive laptop cooler is a great idea and maybe that will even cure your problem.

'Bad blocks' are spots on your hard disk where the magnetic properties of the material are starting to get relatively weaker than they should be for reliable data retention. I think I can remember from high school physic something about heat and proximity to other magnets being factors in the deterioration of the properties of magnets, and I imagine the same goes for hard disks too.

---

### Post by brandon89 on 2010-03-23
cool, well thanks a lot!   i really appreciate everything!  i'll be sure to post back here if more problems arise lol

---

