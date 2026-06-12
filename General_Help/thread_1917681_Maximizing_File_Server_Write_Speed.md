---
title: "Maximizing File Server Write Speed"
date: 2012-01-30
forum: General Help
---

### Post by Kissell on 2012-01-30
This server has 16GB of RAM and is running an XFS formatted partition using a software RAID-6.  The typical file size of a file transfer is 300MB and more files are written than read, however, read speed is more important than write speed.

What happens, is when I copy several GB of files to the XFS partition, it goes amazingly fast for about the first few hundred MB or so...  not exactly sure where that cutoff is...  but it just flies at amazing speed.  Then it comes to a crawl (relatively) at a write speed of about 30MB/sec.  

I suspect that this is because of some sort of memory cache.  Or a buffer of some sort, and then I hit a bottle neck when it gets full.  With 16GB of RAM almost entirely unused, I'd like to significantly increase (or create a) memory cache for disk writes so that I could copy 10GB at a time to the file server and it would go as fast as I could send it.  

Is there a way to adjust do this?  

Also with so much free RAM, is there a way I can put any recently accessed files into RAM to be read?  Read performance is most important and typically someone would not read an entire 300MB file at one time, they're only sent the section they're using, but if they're using it they're very likely to use more than that section, so pre-loading something recently accessed in RAM if possible would be great. 

I don't care if the files are lost due to unexpected power outage, I'd rather prevent that problem than wait for the files to be written to disk every time a file is moved around.

Anyway, I've got some free time to learn something new, so if anyone has ideas for maximizing disk performance or using RAM disk cache please teach me.

---

### Post by Khayyam on 2012-01-31
Kissel ..

There are other factors than system memory and filesystem .. there is also the disk drives themselves (RPM, cache size, etc). Then there is the method used to 'copy' -- if your using the network then the speed of the network, quality of the LAN's switch, the servers network addaptor, network load (LAN and server), and protocol used in the transfer .. all these will play a factor in write speeds. 

With disk-to-disk copies, you have the source disk speed (and cache) to consider. Also, the use of 'rsync' as opposed to 'cp' from disk-to-disk will improve writes, as rsync uses any available free mem.

So there are numerious factors we need to take into account. What does a (sequencial) read from the disk show:
```
hdparm -t /dev/sdX
```Sequencial reads are optimal, random access reads will be less so, as it is dependent on where the file is located on the disk, and how much the 'head' has to move to read/write. Mostly the filesystem will do its best to keep files ordered sequencially, but this is more difficult the larger the filesize, and the extent to which large files are copied and removed from the disk. Whatever the sequencial (optimal) read you are unlikely to improve upon this (though the drives capabilities can be tuned via hdparm). The 'hdparm -t' above, though not a perfect benchmark, will give you some idea of an optimal read/write speed.

The fact your using software RAID might also cause a performace hit, but not using this myself I can't say exactly, its probably minor.   

Next we should consider how the file is written to disk. For good quality SATA BUS/disks over 1GB ethernet, 30MB/s does seem a little slow, but what transport is being used? If your transport uses ssh as a secure wrapper (eg: rsync -e ssh) then this will degrade the speed at which files are transfered. Similarly if your NFS, sshfs, or Samba mounting the server in order to transfer. In my experience rsync (without ssh) has the highest transport speeds, but this depends on your having a network in which security is less of a requirement.

As for caching, well, recently accessed files are in RAM, at least as long as the system doesn't need to free it for some other purpose. This is part and parcel of Linux's memory management. How you might go about doing this in a more targeted way I'm really not sure, you could write them to a ramdisk and have a cronjob move them to the hardisk once a certain time has elapsed. Doing this would mean you'd need to have a seperate directory structure for */new (ramdisk) and */old (hardisk) which is far from straightfoward for client access. Otherwise, I'm fairly sure there is no way to stipulate specific files to be held in RAM, though 'cat $filename > /dev/null' will do it at a pinch .. hehe 

HTH

---

### Post by Kissell on 2012-01-31
```
hdparm -t /dev/md/Data
```
> 
/dev/md/Data:
 Timing buffered disk reads: 2068 MB in  3.01 seconds = 686.86 MB/sec

The array is a RAID-6 made of eleven Seagate Barracuda 2TB SATA-III disks with 64MB disk cache.  Each disk is connected to a PCI-E SATA-III controller card or to a SATA-III port on the motherboard.  No expansion controller holds more than two disks (for load balancing, and so the array will keep running in event of a controller card failure)

That 686MB/sec is 5.7Gb/sec when converting bytes to bits...  which is very close to the 6Gb/sec promised by SATA-III.  However, I think it slows down dramatically during large sustained file transfers, especially writes.

---

### Post by dcstar on 2012-02-01
> **Kissell said:**
> 
............
That 686MB/sec is 5.7Gb/sec when converting bytes to bits...  which is very close to the 6Gb/sec promised by SATA-III.  However, I think it slows down dramatically during large sustained file transfers, especially writes.

People need to understand that the "6Gb/sec promised by SATA-III" is a **wire** speed and has nothing to do with the performance of the actual drives. All you are seeing is how fast the controller and interface can pump cached data out into the system using the SATA cable.

Write performance of anything bigger than data amounts that don't fill the cache are dependant on when **all** the drives in a RAID array have actually written **all** the data to the magnetic surfaces. Until that occurs then the data is not actually written permanently.

RAID-6 has inherent poor write performance:

[https://en.wikipedia.org/wiki/Standard_RAID_levels#Performance_.28speed.29](https://en.wikipedia.org/wiki/Standard_RAID_levels#Performance_.28speed.29)

---

### Post by Kissell on 2012-02-01
> **dcstar said:**
> Write performance of anything bigger than data amounts that don't fill the cache are dependant on when **all** the drives in a RAID array have actually written **all** the data to the magnetic surfaces. Until that occurs then the data is not actually written permanently.


Right, so is there a way we can increase that cache using RAM to improve write speed?  I don't care if it's actually written to the magnetic surface or not, it can do that later.  I just want it to tell me it finished it and let people use it ASAP.

RAID-6 may have theoretical slower right speeds, but at the cost of only one drive it provides dual-disk redundancy, greatly increasing uptime and reducing the likelihood of restoring from a backup.  It's more reliable than RAID-10, and much, much cheaper...  on a budget, I wouldn't run anything else unless the array was small enough to have only a few drives, then RAID-5 would suffice.  These theoretically slower speeds can be compensated for by doing things like upgrading to SATA-III instead of SATA-I or II, or doing other things like taking advantage of unused RAM to increase disk cache.  The 64MB each disk comes with is very small, compared to the cheap price per GB of RAM versus the cost of buying many drives to provide a different raid solution.  Anyway, it's not the best way, but it sure is a cost effective way to maximize results efficiently with the fewest dollars possible.

---

### Post by Khayyam on 2012-02-01
> **Kissell said:**
> [...] so is there a way we can increase that cache using RAM to improve write speed? [...]
I think this is exactly what the kernels memory management does, see the [Linux Memory Management's Wiki]("http://linux-mm.org/Low_On_Memory"). Every I/O will use RAM when it is available or can be freed, as the page states "a page of free RAM is wasted RAM".

In order to 'cache' your files there would need to be a method to speak to MM and set it prefered targets. I know of no way to do this. 

As I said, the only method I know of to specfically target files to be held in RAM is via a [ramdisk]("http://www.vanemery.com/Linux/Ramdisk/ramdisk.html"), but this will not allow you to treat the ramdisk and hardisk as transparent, they would be seperated filesystem wise. You would also need to move the files form the ramdisk, and have them written to disk, via some method (cronjob).

The 'hdparm -t' is an optimal value only, this is hdparm testing the capacity of the hardware, its not reading from the filesystem, or performing actual read/writes to the filesystem. There are benchmarking procedures (involving actual disk read/writes) you could perform to get more realistic numbers, but I mentioned the 'hdparm -t' to show that optimal and real are seperated by any number of factors. I mentioned some of these factors above (network transport, etc), and given your hardware I'm pretty sure the right setup/tools would improve apon 30mb/s (as I remember I've had an scp of about 2GB data to a PII 233mhz 512MB RAM, with a standard ATA drive on 100mb ethernet get about 20mb/s .. as memory serves).

HTH ..

---

### Post by Kissell on 2012-02-01
> **Khayyam said:**
> given your hardware I'm pretty sure the right setup/tools would improve apon 30mb/s 
HTH ..

Well, the 30mb/s was from a source disk that was USB 2.0, so that's likely the bottle neck in that scenario.  

It sounds like the OS is already doing a good job.  The transfers to seem to go very fast in the beginning then slow down considerably, and I was thinking with so much free RAM I could tell the OS to use more RAM for disk caching, but it sounds like the OS is already doing a good job.  I have a long history with windows, so I'm still distrustful of the OS to be doing things the right way on its own.

---

