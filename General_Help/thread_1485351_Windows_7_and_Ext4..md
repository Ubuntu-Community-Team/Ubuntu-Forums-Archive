---
title: "Windows 7 and Ext4."
date: 2010-05-16
forum: General Help
---

### Post by chrispche on 2010-05-16
How do you make Windows 7 see my Linux partition in it. I want to run some mp3s and avi's from Windows 7.

Thanks.

---

### Post by jerome1232 on 2010-05-16
You don't.

There is a driver that will allow Windows to work with ext2 partitions (ext3 can be mounted as ext2 so you can access ext3 partitions too).

Ext4 CAN be used as ext3 (which should allow the ext2 drivers to work with it) but you had to have certain features turned off from the start if I remember correctly.

Here is the link to one of the tools that allow access to ext2/3.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

There are a few others as well.

---

### Post by WorMzy on 2010-05-16
If you have files that you would like to be accessible from both Windows and Linux, you generally store them on an NTFS or FAT partition.

---

### Post by nebulon5 on 2010-05-19
I've been fighting this one for a while now... finally found something that works.

[http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html](http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html)

Right click executable, compatibility, select always run as administrator. Read only access, allows you to right click a directory and save as on a windows partition.

> **jerome1232 said:**
> You don't.
Here is the link to one of the tools that allow access to ext2/3.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

fs-driver will ask you to format the partition because it's incompatible with ext4.

---

### Post by ryan858 on 2010-05-19
I would just transfer the files you need to the Windows partition from Linux.

---

### Post by nebulon5 on 2010-05-19
> **ryan858 said:**
> I would just transfer the files you need to the Windows partition from Linux.

Unless you're serving up streaming video to your wife's computer who will yell at you, should your PC go offline for 5 minutes.

Honestly, I didn't mind the challenge of making it work through Windows, because it's irritating to just do it the way all the Linuxians want me to do it. If I want to access ext4 data from Windows 7 64-bit, then that's what is going to happen.

Wish I was a developer, this ext4 driver would be a done deal. Wish I was a little bit taller, wish I was a baller, I wish I had a girl who looked good I would call her, wish I had a rabbit in a hat with a bat and a six fo Impala.

---

### Post by pirateghost on 2010-05-19
> **nebulon5 said:**
> Unless you're serving up streaming video to your wife's computer who will yell at you, should your PC go offline for 5 minutes.

file systems are irrelevant over the network.  at that point, it is all about network protocols.

---

### Post by jmate24 on 2010-05-19
beware of malicious software you get from certain sites, they could be trojans or malware designed to provide a direct link from your computer to theirs so that they may steal your sensitive data without you knowing it.

only install software from reputable sites! this is true for any OS.

---

### Post by nebulon5 on 2010-05-19
> **pirateghost said:**
> file systems are irrelevant over the network.  at that point, it is all about network protocols.

puh puh puh pirateghost. Missed the point. Not sharing data from drive partitioned to ext4, just sharing data over local network in general. Rebooting would interrupt file transfer/streaming.

> **jmate24 said:**
> only install software from reputable sites! this is true for any OS.

I'm good man, believe ext2explore is legit. And edit your sig man, "SEREOUS" ???

---

### Post by pirateghost on 2010-05-19
> **nebulon5 said:**
> puh puh puh pirateghost. Missed the point. Not sharing data from drive partitioned to ext4, just sharing data over local network in general. Rebooting would interrupt file transfer/streaming.
why would you want to reboot though?

---

### Post by nebulon5 on 2010-05-19
> **pirateghost said:**
> why would you want to reboot though?

To boot into Ubuntu for access to files on ext4, personally, as in this action only affects the network because someone is pulling data (in an unrelated action). I haven't had any luck mounting my ext4 filesystem through VirtualBox.

---

### Post by Serpher on 2010-05-19
What I do is I have one small NTFS partition for Windows 7, a small EXT4 partition for Ubuntu, and a large NTFS partition to store all my data like that including Windows applications. See if you can resize your partitions and go about it all that way. You just simply can't mount EXT4 partitions in Windows. It's not Linux's fault, Linux is awesome for being able to mount NTFS.

---

### Post by nebulon5 on 2010-05-19
> **Serpher said:**
> What I do is I have one small NTFS partition for Windows 7, a small EXT4 partition for Ubuntu, and a large NTFS partition to store all my data like that including Windows applications. See if you can resize your partitions and go about it all that way. You just simply can't mount EXT4 partitions in Windows. It's not Linux's fault, Linux is awesome for being able to mount NTFS.

I agree it is most certainly not "Linux's" fault for Windows 7 inability to accept ext4 filesystems. Microsoft is the big meanie as usual. You can simply mount for read-only access with the program I mentioned before, which got the job done... but for overall sustainability, yes NTFS is the way to go for sharing.

---

### Post by east375 on 2010-05-24
> **nebulon5 said:**
> I'm good man, believe ext2explore is legit. And edit your sig man, "SEREOUS" ???
Well ext2explore appeared to be the only windows tool that can access my ext4 partition but finally it became useless in my case because it can't copy large files from ext4 and produces only 10-20MB limited output.
But time is going and now linux can work with NTFS as native file system. So relax with it and go on share NTFS or FAT volume with your linux.

---

### Post by Shrav on 2010-05-24
> **nebulon5 said:**
> I've been fighting this one for a while now... finally found something that works.

[http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html](http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html)

Right click executable, compatibility, select always run as administrator. Read only access, allows you to right click a directory and save as on a windows partition.

Been looking for a solution like this for a few days now. Works great.
Thanks!!!!

ps works fine under 64bit Windows 7!!!!!!!!!!

---

### Post by babygenius55 on 2012-07-17
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

do it. do it now.

---

### Post by oldos2er on 2012-07-17
Please don't bump old threads.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

