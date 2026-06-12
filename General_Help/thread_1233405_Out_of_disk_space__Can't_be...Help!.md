---
title: "Out of disk space?  Can't be...Help!"
date: 2009-08-06
forum: General Help
---

### Post by markspace on 2009-08-06
Hi all, I have a new Ubuntu install that I'm slowly adding things too.

I'm trying to install NetBeans via the download from their site.  When I execute their .sh file, it tells me I'm out of disk space for temporary files.

```
brenden@ubuntu:~/Desktop$ sudo ./netbeans-6.7.1-ml-linux.sh --tempdir ../temp
[sudo] password for brenden: 
Configuring the installer...
There is not enough free disk space to extract installation data
251 MB of free disk space is required in a temporary folder.
Clean up the disk space and run installer again. You can specify a temporary folder 
with sufficient disk space using --tempdir installer argument
brenden@ubuntu:~/Desktop$ 
```This doesn't make sense to me, as I think I have plenty of space.

```
brenden@ubuntu:~/Desktop$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.6G  3.4G  106M  97% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  104K  993M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M  168K  993M   1% /dev
tmpfs                 994M   76K  993M   1% /dev/shm
/dev/sda2              10G  8.8G  1.3G  88% /host
lrm                   994M  2.5M  991M   1% /lib/modules/2.6.28-14-generic/volatile

```Does anyone have an idea what is going on and how to fix it?

---

### Post by drs305 on 2009-08-06
First, welcome to Ubuntu and the Ubuntu forums.  :-)
Edited: The following is for a normal install, not Wubi. 
3.6GB is not really large enough to support a normal ubuntu installation. I have written a guide that can help you either expand your / partition by taking space from a Windows partition (or other partition) or tell you how to reinstall and make the partition larger (8GB recommended).
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by markspace on 2009-08-06
Hmm, just noticed I was reading that wrong, yeah I see your point.  However I think I may be stuck.

The larger issue of free space can't change.  That's all I have left, there's no partitions left expand into.

---

### Post by drs305 on 2009-08-06
You might try Xubuntu. Although space would still be very tight, the absolute minimum disk space drops from 4GB to 1.5GB. Here is the Ubuntu wiki with the specifications:
[Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by martinbaselier on 2009-08-06
> That's all I have left, there's no partitions left expand into. 
I'm not sure what you mean by that. Do you have no partitions with free space or don't you have an empty partition?

If you have a partition with free space, you can shrink it and add some space to the ubuntu partition. You can easily do that from a live cd with partition editor.

---

### Post by markspace on 2009-08-06
> **martinbaselier said:**
> Do you have no partitions with free space or don't you have an empty partition?  Correct. 
 
   ;) 

 I don't have any empty partitions left to expand into.  Sorry mangled English about my.  

Likely what I really have to do is move some stuff off to an external hard drive and start using that on a regular basis, rather than just for backups.

---

### Post by jerome1232 on 2009-08-06
Well a couple things

Your using Wubi, your install isn't on a real partition. To expand you can make another virtual disk and mount it. /home and /usr will probably be the biggest space eaters on your computer so I would suggest one of those.

There is a guide that shows how to do this. I believe you can resize your existing virtual partition as well.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

