---
title: "Shared NTFS Data-Partition: Lost files after Win7-CHKDSK"
date: 2010-05-21
forum: General Help
---

### Post by swiss-chris on 2010-05-21
Hello Everybody,

I have been happily getting used to using my 9.10 Ubuntu in stead of Win7 (dual-boot), until I recently noticed a serious problem for which I cannot seem to find a solution myself. Repeatedly, I have been downloading files via FileZilla (sFTP) onto my shared NTFS Data-Partition. When I restart Win7, CHKDSK (or something like it - still have to verify that it really is the good old CHKDSK I used to know) asks me to run a disk check, and after completion (where some indexes were removed and then supposedly restored), when rebooting under Ubuntu 9.10, all the previously downloaded files are gone. Also - I had (luckily) configured SVN to commit the most important code-files I was working on. Now, when I go into the svn workspace of those files, it tells me " '.' is not a working copy". In other words, not only the files I downloaded via FileZilla have disappeared, but also the .svn folders and files! As well, it seems all the files I created and worked on these last days have disappeared from my file system as well.

I hope you can understand my frustration. This is lots of hours of paid work that's disappearing regularly. 

Now, here's my actual question and the reason why I come to this forum for help: Does any one have an idea:

[LIST=1]
[*]What the problem is that CHKDSK is identifying?
[*]Why after running CHKDSK, the files are gone (where are they?)
[*]What's the solution for a shared data-partition for a dual-boot (Win7 - Ubuntu) computer?
[/LIST]

If you can help me with any of these questions or with the problem above, I would be very grateful.

Thanks in advance for any help you can give me with these questions or with the problem above,

Chris

p.s. it seems that files previously created via Win7 and only edited under Karmic are o.k.
p.p.s. I should maybe note as well that my Win7 is usually in hibernation while I use Karmic (for which hibernation has never worked - when I turn on my computer it gives me a fresh boot into Karmic in stead of restoring the previous state). The data-loss problem seems to happen only when I actually restart/reboot Win7. Win7 has 2 primary partitions to itself. My other partitions (including the NTFS data partitions) are logical partitions all on the same extended 3rd primary partition. I'm using Grub2 as a boot manager which is on it's own (logical) partition.

---

### Post by heyneman on 2010-12-11
I'm having this same issue.  I assumed it may have something to do with Win7 hibernating while I modify data on my shared partition in Ubuntu.  I've been very careful about fully shutting Win7 down lately, and it has still happened.

So...bump :)

---

### Post by swiss-chris on 2010-12-11
Hi,
If I remember correctly, the solution was installing something called ntfs tools or ntfsprogs. 
Let me know if it helps !
Good luck !

---

### Post by Bitrate on 2010-12-11
> **swiss-chris said:**
> Hello Everybody,


Now, here's my actual question and the reason why I come to this forum for help: Does any one have an idea:

[LIST=1]
[*]What the problem is that CHKDSK is identifying?
[*]Why after running CHKDSK, the files are gone (where are they?)
[*]What's the solution for a shared data-partition for a dual-boot (Win7 - Ubuntu) computer?
[/LIST]

I had the same problem trying to share an NTFS partition between Ubuntu and Windows 7. Corruption of the NTFS partition would arise when switching from one OS to another and no amount of repairing would fix it. I'd suggest you backup as much data as you can from your NTFS partition and also try using TestDisk to recover any lost data. Keep your Windows 7 NTFS partition separate from your Ubuntu installation (if possible). 

I decided to dump Windows 7 in any case as ext4 works much better and Ubuntu runs every application I need. If I want to run any Windows apps I just use either Wine or VirtualBox.

---

### Post by JesperSP on 2011-02-11
I had the exact same problems with corrupted NTFS after writing files from ubuntu 10.10:

[http://ubuntuforums.org/showthread.php?t=1665687](http://ubuntuforums.org/showthread.php?t=1665687)

but unfortunately I went with the wrong solution: I decided to install win 7 on my machine (in triple boot XP, 7-64bit, ubuntu 64bit) and now my ubuntu partition is listed as "unallocated" and is not even detected in testdisk. And I miss ubuntu! My WIFI-network card and HP printer do not work under win7 ! ](*,) :cry:

Cheers,
Jesper

---

### Post by ursoouindio on 2011-03-18
I've been experiencing this very same problem stated in the first post, for a couple of years now. File corruption and lost work :(

I have Windows XP + Ubuntu and a mutual partition with the files I commonly access, independently of which system I'm using. It makes sense to have different partitions to different systems, but no sense to have different partitions to my personal data.

I will get a new pc and I would like to know any measures to take (as I will take the time to format it and set up Ubuntu and Windows 7) to avoid this kind of problem...

---

### Post by akakingess on 2011-03-18
Do any of ya'll (yes I am Texan) have ntfs-3g and ntfs-config (I think that's what it's called), cuz I have yet to have that problem?

---

### Post by ursoouindio on 2011-03-18
> **akakingess said:**
> Do any of ya'll (yes I am Texan) have ntfs-3g and ntfs-config (I think that's what it's called), cuz I have yet to have that problem?

yeah, I have both!

---

### Post by swiss-chris on 2011-03-18
Have you tried ntfsprogs?

---

### Post by ursoouindio on 2011-03-18
I have it too.

---

### Post by gesti on 2011-06-30
have the same issue. Any one got a solution? I'm thinking to just change to Ext2 and install a driver for that on Win7... unless some one knows a better solution?!

---

