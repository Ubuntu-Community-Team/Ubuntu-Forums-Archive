---
title: "accessing music from windows"
date: 2010-08-28
forum: General Help
---

### Post by tux01 on 2010-08-28
Hi everyone I recently built a desktop computer with 2 hard drives and I have windows7 installed on a 160g one and Ubuntu 10.04 on a 500g one. I store all of my music on my linux hdd and i was curious if there is a way to access my music folder in linux via windows 7? If I am in the wrong forum please excuse me for I am new to posting on forums.

---

### Post by Woody1987 on 2010-08-28
It depends on what filesystem you are using for linux. I am assuming you are using ext3 or 4 and thus it would be hard if not impossible to access it from windows. I am in a similar position and what I do is partition my linux disk into two partitions. First partition holds my linux installation and is formatted as ext4 and the second holds just my music and is formatted as NTFS which is readable and writable from both windows and linux. My music partition is then mounted to /home/USERNAME/Music in linux and is read in windows as a separate drive. You can use gparted to partition your drive. You will need to shrink your existing Linux partition, this won't destory anything but you should back up before you do it, and then format the freed space as NTFS and move your music to it.

---

### Post by Lars Noodén on 2010-08-28
Windows is very poor at supporting filesystems, so you might want to rely on a third-party client (music player) and stream the music from your computer.  ffmpeg, vlc, and icecast2 can provide music streams.

---

### Post by Mark Phelps on 2010-08-29
Ubuntu 10.04 installs by default using the Ext4 filesystem -- which, unless they very recently updated the Ext-filesystem driver, MS Windows can NOT read.

If you want to share files, a much better way is to create a data-only NTFS partition, move the shared files there, and mount that in Ubuntu.

---

### Post by papibe on 2010-08-29
Check this article: [Three Ways To Access Linux Partitions (ext2/ext3) From Windows On Dual-Boot System]("http://www.howtoforge.com/access-linux-partitions-from-windows")s.

I've never tried neither of them, so I would advice you to get more info for each tool (specially check for malware and so).

Regards.

---

### Post by Vaphell on 2010-08-29
shared ntfs partition for the cross-platform usage is the best option. Support for native linux partitions in windows is half-assed at best while the opposite is not true.

---

### Post by Lars Noodén on 2010-08-30
> **Vaphell said:**
> shared ntfs partition for the cross-platform usage is the best option. Support for native linux partitions in windows is half-assed at best while the opposite is not true.

So is support for NTFS in Windows.  Data on NTFS will get lost eventually.  

If you are going for a data share via the file system with quirks to help along users still on Windows, then [samba](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html) can do it.  The partition exported can be EXT that way.

However, it'd be less work to set up a streaming server.  A further advantage of the streaming server is that there is less access to the system from the Windows clients.  Thus decreasing the risk for security problems.

---

