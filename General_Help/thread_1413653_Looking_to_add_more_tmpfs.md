---
title: "Looking to add more tmpfs"
date: 2010-02-22
forum: General Help
---

### Post by JohnnyC35 on 2010-02-22
Hey. I've been playing around with tmpfs for a bit. killed my system a few times and moved on :P  via Google and ubuntuforums I have been able to come up with a list of things I can or *'can...but**'** *and I was wondering if there is anything else I can add to the list of tmpfs.
Here's my fstab as it stands:
 
> 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7b4eb23c-bc71-4282-a492-42150fd701ee /               ext2    noatime,nodiratime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8        0 0
/dev/sda1       /media/Media1   xfs users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
/dev/sdb1       /media/Media2   xfs users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
#/dev/sdc1      /media/Media3   xfs users,auto,sync,noatime,nodiratime,allocsize=384m 0 1

# enable RAM-based temporary file systems
tmpfs  /var/log                                             tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /tmp                                                 tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /var/tmp                                             tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /var/log/apt                                         tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /var/run                                             tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /var/lock                                            tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /var/cache                                           tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /var/cache/apt/archives/                             tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /home/john/.thumbnails                               tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /home/john/.adobe                                    tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /home/john/.cache                                    tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /home/john/.macromedia                          tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /home/john/.claws-mail/gtkhtml2_viewer       tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /home/john/.azureus/tmp                          tmpfs defaults,noatime,nodiratime 0 0
tmpfs  /home/john/.mozilla/firefox/wjtnzhux.default/Cache tmpfs                                                                      defaults,noatime,nodiratime 0 0
and so a few of those directories so yell at me when I mount them on boot I edited rc.local:
> 
mkdir -p /var/log/apt
mkdir -p /var/cache/apt/archives
mkdir -p /var/cache/apt/partial 
mkdir -p /var/cache/apt/archives/partial
sysctl -w vm.swappiness=1           # Strongly discourage the swapping of application data to disk
sysctl -w vm.vfs_cache_pressure=50  # Don't shrink the inode cache so aggressively.
I've had this setup for about a month and no issues yet on my Karmic system ;) I have 2Gb .. well 1.5 after onboard video and at the writing of this my memory is between 325-330mb used. My / + /home is sitting at 2.4Gb of 8Gb. I have it running off a USB stick and have had no issues. my next thing to play with in the future is a RAID 5 USB. I had attempted it before but the previous motherboard's USB was unstable :'(

---

### Post by lloyd_b on 2010-02-23
Sorry, but I think you're overdoing it.  For example, while having "/var/log" as a tmpfs keeps log files from eating your disk, it also means that if the machine crashes for some reason, there's *no* chance of having log file data to tell you what happened.

In addition, "/var/run" and "/var/lock" are, on my system (9.10), *already* virtual file systems, so converting them to tmpfs doesn't save any disk space.

Unless you are on a machine that has tons of memory, but is seriously short of disk space, I don't really see the point...

Lloyd B.

---

### Post by cong06 on 2010-02-23
well, there are arguments that with solid state disks it makes sense to prevent disk writes to protect the disk: [https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)

However, I've decided to only do it with /tmp and /var/tmp
```

tmpfs      /tmp            tmpfs        defaults           0    0
tmpfs      /var/tmp        tmpfs        defaults           0    0

```

I've also given up with the idea of thumbnails (I toyed with it for a bit) because with all the pictures, it makes more sense to keep the thumbnails so that they won't get re-created each time taking up precious cpu/time.

Firefox isn't a bad idea, but you can also re-direct the cache with:
about:config
browser.cache.disk.parent_directory  /tmp

While '~/.cache' is almost a cache, some other programs keep 'important' file there... For example I think banshee keeps cached album covers there.

So It might be better to leave all those messy files there. I'm not a big fan of them either, but I just console myself by resetting them on each re-install.

---

### Post by JohnnyC35 on 2010-02-23
hey,
thanks for the info. I didn't realize "/var/run" and "/var/lock" were in memory already. With 1.5Gb memory I haven't had any issues (yet), at most it's gone to 700Mb after some heavy graphic browsing. 

> 
I've also given up with the idea of thumbnails (I toyed with it for a  bit) because with all the pictures, it makes more sense to keep the  thumbnails so that they won't get re-created each time taking up  precious cpu/time.
I haven't noticed much of a slow down looking thru my movie directories with re-creating thumbnails each time but it's something to keep in mind for the future. As for Firefox I have it in fstab mainly to remind myself that I have put it in memory rather than recheck via config if I did it already :P lol

Thanks for the info tho

---

### Post by mbsullivan on 2010-06-22
I've thought about this before, and I had thought that /usr/src/ would also be prudent. Compilation is one thing that CAN be substantially sped up, and you're not typically interested in the source post-compile, so volatility's less of an issue.

Also, it gives a natural thing to benchmark (disk vs. RAM): kernel compile.

Mike

---

### Post by mbsullivan on 2010-06-22
Also, if you have lots of RAM, it might make the most sense to make a fixed size ramdrive for very often accessed folders. 

tmpfs is variable sized, and can reside in both RAM and swap... This makes it considerably slower than a dedicated (non-compressed) RAM drive. It's still fast (I get 5-600MB/s sequential write speed with my DDR2-667), but it could be faster.

I think [this post]("http://ubuntuforums.org/showpost.php?p=9424927&postcount=13") (from a similar discussion) sums the pros/cons of the different RAM drives nicely.

> 
Unless you are on a machine that has tons of memory, but is seriously short of disk space, I don't really see the point...

This definitely isn't a technique for the memory limited, but since all of these RAM disks are tmpfs, they can technically be swapped out. Therefore, even with a moderate amount of RAM (4 GB), you may be able to combine this with a larger swap disk or file, and get the speedup without having to constantly worry about the size of the data you're storing. See [here]("http://ubuntuforums.org/showpost.php?p=9480616&postcount=47") for a simple experiment I tried with tmpfs and filling up my RAM.

You'd want to increase the vm.swappiness in this case -- otherwise, performance when you DO need to swap will be HORRIBLE. It probably isn't a bad idea anyway... Many files will NOT be reused often if ever, and swapping them out early can only be a good thing.

Mike

---

### Post by JohnnyC35 on 2010-06-23
Going to try the great tmpfs experiment. Put as many directories in  tmpfs and still be able to do my day to day stuff without running swap  or rebooting. Should be doing this after the weekend after I get my SSD :p  and my new RAM (4Gb) :KS
Here's the list I have of directories I have that I think are safe (not  worried if I lose any info in /home atm) and if you know of other safe  ones let me know :)

> 
/home/   
/media
/tmp
/usr/src/
/var/cache  
/var/cache/apt
/var/cache/apt/archives/  
/var/cache/apt/archives/partial
/var/crash
/var/lib/dhcp3
/var/lock
/var/log  
/var/log/apt  
/var/run
/var/spool/cups
/var/tmp  


Thanks ):P

---

### Post by cong06 on 2010-06-24
> **JohnnyC35 said:**
> Going to try the great tmpfs experiment. Put as many directories in  tmpfs and still be able to do my day to day stuff without running swap  or rebooting. Should be doing this after the weekend after I get my SSD :p  and my new RAM (4Gb) :KS
Here's the list I have of directories I have that I think are safe (not  worried if I lose any info in /home atm) and if you know of other safe  ones let me know :)

Have you thought of just using a live disk?

---

### Post by JohnnyC35 on 2010-06-24
> **cong06 said:**
> Have you thought of just using a live disk?

hmm... then it would all load into memory. Would be easy to do. Just run the USB creator on the SSD. Is there a way to automatically have it open or try out Ubuntu and not get stuck at the selection screen?

---

### Post by regnarts on 2010-07-17
> **lloyd_b said:**
> Sorry, but I think you're overdoing it.  For example, while having "/var/log" as a tmpfs keeps log files from eating your disk, it also means that if the machine crashes for some reason, there's *no* chance of having log file data to tell you what happened.

In addition, "/var/run" and "/var/lock" are, on my system (9.10), *already* virtual file systems, so converting them to tmpfs doesn't save any disk space.

Unless you are on a machine that has tons of memory, but is seriously short of disk space, I don't really see the point...

Lloyd B.

Virtual file systems? I'm beginning to think that I'm on a wild goose chase. Though I'm not certain that I haven't missed something, I haven't found any method  for configuring run or lock that would result in having the directories on virtual file systems (as in procfs or sysfs virtual file systems) other than mounting them on tmpfs. Also, though I don't have an Ubuntu installation to confirm it, online sources seem to suggest that one or more releases of Ubuntu mount these directories as tmpfs in an initscript. Did you intend to say that /var/run and /var/lock are already mounted on tmpfs by one the Ubuntu initscripts (/etc/init.d/mountkernfs.sh) in your installation? If not, please explain.

---

### Post by JohnnyC35 on 2010-07-17
> **regnarts said:**
> Virtual file systems? I'm beginning to think that I'm on a wild goose chase. Though I'm not certain that I haven't missed something, I haven't found any method  for configuring run or lock that would result in having the directories on virtual file systems (as in procfs or sysfs virtual file systems) other than mounting them on tmpfs. Also, though I don't have an Ubuntu installation to confirm it, online sources seem to suggest that one or more releases of Ubuntu mount these directories as tmpfs in an initscript. Did you intend to say that /var/run and /var/lock are already mounted on tmpfs by one the Ubuntu initscripts (/etc/init.d/mountkernfs.sh) in your installation? If not, please explain.

Sorry yes, /var/run and /var/lock are temp file systems by default. adding them to my list didn't change anything.

On another note, I tried making a live disk on my SSD and the Startup Disk Creator wouldn't let it go thru.

---

### Post by vadviktor on 2011-05-04
As stated in many documentations putting /var/tmp into disposable ram space is NOT suggested, on the contrary, forbidden.

> /var/tmp: Temporary files that are large or that need to exist for a longer time than what is allowed for /tmp.

---

