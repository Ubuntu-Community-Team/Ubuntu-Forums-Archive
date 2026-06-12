---
title: "Drive Free space confusion"
date: 2010-08-14
forum: General Help
---

### Post by Keskasidvar on 2010-08-14
I currently dual-boot Win7 and Ubuntu 10.04, before I came back on Ubuntu, I uninstall-ed many programs to free up some space. Before I restarted my computer to boot back into Ubuntu my Internal HD had 43.5GB of free space, and when I booted into Ubuntu I checked the free space and it only showed 7.9GB of free space, did I check the wrong thing? Is 'File System' the Ubuntu equivalent to the C:\ drive in Windows?

---

### Post by blazemore on 2010-08-14
> **Keskasidvar said:**
> I currently dual-boot Win7 and Ubuntu 10.04, before I came back on Ubuntu, I uninstall-ed many programs to free up some space. Before I restarted my computer to boot back into Ubuntu my Internal HD had 43.5GB of free space, and when I booted into Ubuntu I checked the free space and it only showed 7.9GB of free space, did I check the wrong thing? Is 'File System' the Ubuntu equivalent to the C:\ drive in Windows?

The free space reported by Windows only refers to the space left available on Windows's own partition.

A partition is like a section of the hard-disk which is fenced off for one operating system to use.

So your actual hard disk is, say 100Gb. When you installed Ubuntu it created a 20Gb partition (for example), resizing the WIndows one (which previously took up the entire space on the disk) to 80Gb.

That means that Ubuntu only ever had 20Gb of space available to it.

I hope I make sense.

---

### Post by Keskasidvar on 2010-08-14
Thanks, I was thinking of getting rid of Win7 anyway, I just gotta get WINE working fine gamewise, if I want Win7 back I can just ask my friend for the disc as he goes to Microsoft conferences and gets free install disc's. If I were to remove Win7 then the rest of the disk is open to Ubuntu leaving more storage space, am I correct?

---

### Post by blazemore on 2010-08-14
You'd have to resize Ubuntu's partition.
Search for "resize ext4 partition ubuntu livecd" to point you in the right direction.

---

### Post by Keskasidvar on 2010-08-14
well, i did notic that you can change the partition size from a livecd easily, but would there be a problem if I'm running 10.04 and i only have a livecd for 9.04?

---

### Post by -kg- on 2010-08-14
There might be.  I don't know if GParted under Jaunty has the ability to deal with partitions formatted to the ext4 file system.  If you elected to install Lucid using ext3, then you're good to go.

If you have a high speed Internet connection, you can download the 10.04 Live CD (I prefer torrents, due to a torrent's error-checking), check the md5 checksum to make sure it's a good download, and burn it to disk.  You'll want to have a Live CD available in case of unsurmountable problems.

That, or you can download the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") (a dedicated Live CD and much smaller download) and burn that to disk.  The Gparted Live CD is an excellent tool to use in partitioning operations.

For more information on basic Partitioning operations, read at the link in my signature block.

One caveat:

I wouldn't completely delete the Windows 7 partition.  It can cause all kinds of problems with booting, making everything unbootable.  When the time comes, I would re-format it and shrink it down to almost nothing (but not quite).  That way it will take little room and the drive letter/number designations (like sda1, sda2, etc.) won't change, rendering your system unbootable until you can correct it.

---

### Post by Keskasidvar on 2010-08-15
well i just found out how to Partition from the Win7, Win7 has a partition thing built in it and i was having trouble with GParted so its a relief.

---

### Post by Keskasidvar on 2010-08-15
Actually, scratch what i just said, apparently Ubuntu is in the same partition as Win7 so i guess my only option IMO is a reformat, theres really not much that i would need, most of my computer actions are done over the internetz. i have the files i used to Crack and Torrent my main programs on my external, and FYI i did get GParted working and it is also showing that there is one labeled partition. if i do reformat I have my flash drive setup as a live Ubuntu 10.04 64 Bit (the one i have installed right now is 32 Bit and i think 64bit would be better as i am a gamer and i was looking to get more RAM. I mould just wait for my friend to get back cuz he's the one who gave me the computer and he did a reformat before i got it, but I would need to wait for him as he is away right now and he has the biOs disc that he used in the machine i am using.

---

### Post by blazemore on 2010-08-16
If Ubuntu is "In the same partition" as Windows 7 when looking at the Windows 7 partitioning tool, then the Windows 7 partitioning tool is wrong.

---

### Post by Keskasidvar on 2010-08-17
But I also mentioned that GParted showed the same thing.

---

### Post by efflandt on 2010-08-17
It looks like you had done a Wubi install within the Windows partition instead of on a separate partition.

But in any case, what Linux would show for free space for its alloted space and what Windows shows as free space for its entire partition would be two different things.

---

### Post by Keskasidvar on 2010-08-17
yeah i was thinking it was wubi installing inside windows, and i did notcie that there was Unallocated Space at about the amount of free space on my Ubuntu side, but Ubuntu is still in the Windows side so idk.

---

### Post by Keskasidvar on 2010-09-02
I recently put this thread to SOLVED but I just wanted to let people know why it is solved. My Friend gave me and extra 320gb HD so im now running Ubuntu on that HD and my other HD(160gb) is just the Win7 setup I had before.

---

### Post by blazemore on 2010-09-04
I'd like to recommend a "true" native dual-boot setup for those who want to use Ubuntu as a dual-boot OS.
If you just want to try it out, run it from the LiveCD.
I personally see no need for an intermediate.

---

