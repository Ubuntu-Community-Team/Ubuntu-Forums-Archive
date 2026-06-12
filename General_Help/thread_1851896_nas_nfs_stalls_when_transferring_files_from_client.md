---
title: "nas nfs stalls when transferring files from client and crashes client"
date: 2011-09-29
forum: General Help
---

### Post by Gatemaze on 2011-09-29
Hi all,

I very recently purchased a new Synology DS211j and it seems like an excellent product so far. I've encountered the following issue over the last couple of days... Whenever I try to copy a file to the NAS it stalls every now and then and in some cases permanently.

In a bit more detail,

My network consists of two ubuntu machines, one running 11.04 (64bit) the other 10.04. An Asus N DSL-N13 router and the Synology DS211j  with two HDD of 2TB each in RAID1, running the latest firmware/software and having NFS enabled. My fstab entry is as follows:
nas_ip:/volume1/shared mounted_folder nfs nouser,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid 0 0

As I said I noticed a stall every now and then, which I suspect it is from the NAS mirroring the data that I am copying across, as this stall occurs even when connected with wire. However, when wired the copy “resumes”/carries on as normal. When connected through wifi the stall can be permanent particularly when trying to copy any file more 200MB. I also noticed that typically there is a stall after transferring a file and moving to the next. The stall is quite bad as it breaks my ubuntu system: unity not responsive, cannot access the mounted folders, trying to unmount says they are busy, shutting down the pc hangs among others. 

Strangely enough a few days back I copied a large amount of data (100GB) over wifi with no issues or copy and system hang ups. More strangely it is only my 11.04 (64bit) machine that seems to crash on the stalls and not the 10.04.

Many thanks if you have any hints and tips that could point me to the right direction.

---

### Post by Gatemaze on 2011-09-29
I found the following post of some relevance although it is under win64bit... mine is ubuntu 11.04 64bit... But still no way to see how I can proceed...

[http://futuremark.yougamers.com/forum/showthread.php?t=142297&page=2](http://futuremark.yougamers.com/forum/showthread.php?t=142297&page=2)

---

