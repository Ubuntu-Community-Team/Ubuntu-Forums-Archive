---
title: "Usb file transfer slow down my Pc"
date: 2009-09-02
forum: General Help
---

### Post by alex_time on 2009-09-02
I am on Jaunty Jackalope 9.04.

The Usb file transfer rate from an external Western Digital is good (+-27mb/s) but during a file transfer my entire Pc become really slow! Open KDE Menu require 3 seconds, right click 4 seconds and I do not want to speak about open a program....There is somethig I can check? The good transfer rate tells me that usb 2 driver is ok, so what's the problem? 

This is a top command output during the transfer
```
top - 15:00:47 up  1:23,  1 user,  load average: 3.41, 3.43, 3.47
Tasks: 157 total,   3 running, 154 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.6%us, 13.5%sy,  0.0%ni, 23.6%id, 53.6%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   3355424k total,  3336580k used,    18844k free,   679488k buffers
Swap:  7992296k total,      952k used,  7991344k free,  1995364k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4938 root      20   0  4112 1012  420 R   11  0.0   6:01.92 mount.ntfs-3g
 4943 alessio   20   0 36324 3536 1676 D   10  0.1   1:27.86 kio_file
 3736 root      20   0  507m  48m 5716 S    6  1.5   5:33.03 Xorg
 4949 alessio   20   0  356m  37m 6928 S    6  1.1   4:08.03 plasma
 4283 alessio   20   0  132m  29m 8740 S    4  0.9   4:41.74 kwin
   32 root      15  -5     0    0    0 S    3  0.0   1:55.69 kswapd0
 2104 root      15  -5     0    0    0 S    1  0.0   0:19.49 kjournald
 4411 alessio   20   0  518m 164m  10m S    1  5.0   3:29.88 firefox
 7927 alessio   20   0  130m  19m 7440 S    1  0.6   0:01.21 konsole
    7 root      15  -5     0    0    0 R    1  0.0   0:49.17 ksoftirqd/1
 7885 root      20   0     0    0    0 S    1  0.0   0:10.51 pdflush
 7920 root      20   0     0    0    0 S    1  0.0   0:11.39 pdflush
    4 root      15  -5     0    0    0 S    0  0.0   0:44.38 ksoftirqd/0
 6347 alessio   20   0 78276  10m 1468 S    0  0.3   0:01.01 vmware-tray
```I thought it was because of the NTFS Usb disk partition, maybe it require lot of CPU but as you can see cpu is not so busy...

it is also not swapping

```
free -m

             total       used       free     shared    buffers     cached
Mem:          3276       3245         30          0        650       1949
-/+ buffers/cache:        645       2630
Swap:         7804          0       7804
```so...what hell it is doing during usb transfer?!

---

### Post by alex_time on 2009-09-03
The problem occure during a big file transfer, if I copy 20Gb of small file I have no problem, but if I copy some Virtual Machine, with 20/30 Gb each, I have this problem, maybe this can help to understand why this happen?!

---

### Post by Napu5 on 2009-09-04
The NTFS driver in Linux uses a lot of CPU. It says ntfs-3g from version 2009.3.8 is faster, but the version in Ubuntu is older. I don't know if we will get the new and faster ntfs-3g in Jaunty or if we have to wait for Karmic.

---

### Post by alex_time on 2009-09-05
> **Napu5 said:**
> The NTFS driver in Linux uses a lot of CPU. It says ntfs-3g from version 2009.3.8 is faster, but the version in Ubuntu is older. I don't know if we will get the new and faster ntfs-3g in Jaunty or if we have to wait for Karmic.

Thanks for your replay, at least I have a reason...I'll format it on ext3 and I'll solve the problem.

---

### Post by fluffman86 on 2009-09-05
For a bigger speed increase, format as ext4 :)

---

### Post by alex_time on 2009-09-05
> **fluffman86 said:**
> For a bigger speed increase, format as ext4 :)

Thanks...I have already formatted as ext3 all my HD partitions :( when 9.10 will be out I will make ext4 for HD partitions too like my USB Hd

Thanks again

---

### Post by krams915 on 2009-11-19
Did this improve your system response? I mean it's no longer slowing down your PC?

I'm experiencing your same problem. I have an NTFS external drive. Transferring huge files slows down my system.

When I copy files from my DVD somehow it slows down my system as well. I don't think my DVD is in NTFS format.

Thanks.

---

### Post by krams915 on 2009-11-19
I think the problem is related with the kernel. I've done some research and here's an interesting link you might wanna check out:

Bug 12309 -  Large I/O operations result in slow performance and high iowait times   
[http://bugzilla.kernel.org/show_bug.cgi?id=1230](http://bugzilla.kernel.org/show_bug.cgi?id=1230)

(It's quite disappointing though because until now the bug hasn't been fixed, but at least they're working with it).
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8349326") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8349326")

---

