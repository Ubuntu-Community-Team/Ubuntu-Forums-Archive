---
title: "Are there any good disk activity monitors?"
date: 2010-04-17
forum: General Help
---

### Post by xeddog on 2010-04-17
I am looking for a disk activity monitor that can tell me how many bytes/sec (or MB/sec) each of the disks attached to my machine are transferring.  Something like the network monitor where you can see your send/receive rates, but for disks.  System monitor doesn't do it, and it doesn't look like Conky does it.  Any other ideas?

I started looking for this because it seems like either Lucid is having some issues with multiple copies running simultaneously to and from the same disks, or I am having difficulty realizing just how much contention there really is. If I start a single copy operation transferring say 100GB of video files from my internal sata disk to a USB attached disk, the copy will run somewhere around 18MB/sec or a little more.  If I start a second copy from the same internal disk to the same USB disk, the transfer rates start falling until they get down to around 6MB/sec combined.  These numbers are from the "File Operations" dialog.  The internal sata disk is formatted ext4, and the USB is ext3. 

I get more throughput than that when using Filezilla to transfer files from my media server to this same computer over my 100Mb Ethernet.  As a matter of fact, while the file copies are running I can start Filezilla and get about 7.5MB/sec downloading three simultaneous files to the sata drive.  I expect the individual transfers to slow down, and maybe the overall throughput to reduce due to disk contention, but I didn't expect it would fall all the way down to 1/3 or 1/4 the rate of a single copy operation.  So this is why I am looking for a good disk activity monitor.  So I can see what is really happening.

Thanks,

xeddog

---

### Post by dcstar on 2010-04-17
> **xeddog said:**
> I am looking for a disk activity monitor that can tell me how many bytes/sec (or MB/sec) each of the disks attached to my machine are transferring.  Something like the network monitor where you can see your send/receive rates, but for disks.  System monitor doesn't do it, and it doesn't look like Conky does it.  Any other ideas?
.......

gkrellm

---

### Post by oaxacamatt1 on 2010-04-17
Don't forget 'Conky'

---

### Post by xeddog on 2010-04-21
Trying gkrellm.  I don't see where Conky can do this.

Thanks,

xeddog

---

### Post by xeddog on 2010-04-21
Trying gkrellm.  I don't see where Conky can do this.  It looks to me like Conky will tell you your disk utilization as a percentage of spade used, but not actual current transfer rates.  Right??

Thanks,

xeddog

---

### Post by wlourf on 2010-04-21
> **xeddog said:**
> Trying gkrellm.  I don't see where Conky can do this.  It looks to me like Conky will tell you your disk utilization as a percentage of spade used, but not actual current transfer rates.  Right??

Thanks,

xeddog Hi, did you try the "diskio" variable.
From doc : [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
> Displays current disk IO. Device is optional, and         takes the form of sda for /dev/sda. Individual partitions         are allowed. 
There are also : diskio_read, diskio_write, diskiograph
Don't know if they fit tour needs !

---

### Post by robert shearer on 2010-04-21
In the terminal type..
```
sudo apt-get install iotop
```
and once it is installed type 
```
iotop
```

(iotop=input/output version of 'top') shows disc writes and the processes associated with them.

---

