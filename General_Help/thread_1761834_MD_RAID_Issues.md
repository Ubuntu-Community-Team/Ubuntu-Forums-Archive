---
title: "MD RAID Issues"
date: 2011-05-18
forum: General Help
---

### Post by jmg999 on 2011-05-18
Ok, so here’s the deal…I have an Ubuntu fileserver:
   
  ```
jeffe@USC:/disk$ cat /etc/issue
  Ubuntu 10.04.1 LTS \n \l
   
  jeffe@USC:/disk$ uname -a
  Linux USC 2.6.32-24-generic-pae #43-Ubuntu SMP Thu Sep 16 15:30:27 UTC 2010 i686 GNU/Linux
   
  jeffe@USC:/disk$ mdadm --version
  mdadm - v2.6.7.1 - 15th October 2008
```  Attached to this server is a 8x1TB MD RAID 5 array housed in a Rosewill enclosure and connected via dual-plane eSATA connections. This array has been sort of a mystery for a while now, and I had a feeling that one of the drives was going bad, b/c for quite some time, when I’d attempt to write to the array via Samba, even something as small as creating a new directory, the array would freeze up anywhere from 10 seconds to two minutes. Of course, it got longer over the months. What I mean by this is, if I were to create a new directory via a Samba connection, the light (on the front of the enclosure) for one of the HDDs would light up, and the directory wouldn’t be created, until the array unfroze, at which point, the light would then go out. In other words, it was pegging one of the HDDs. However, this problem would only occur, when the array hadn’t been written to in some time. If I had recently written to the array (say, in the last 10 minutes), this problem would not surface. Nonetheless, I never noticed any out of the ordinary error messages. Since I wasn’t sure which drive it was, I didn’t want to replace it and mess w/ the array in any way.
   
  Two days ago, I noticed some issues accessing the drive via Samba. I SSHd to the box, and I checked /proc/mdstat. It showed 4 of the 8 drives as missing from the array. The first thing I did was check the lights on the front of the enclosure. In the past, the eSATA cables have come loose (4 of the 8 drive lights on the enclosure will go out), and it will cause 4 of the 8 HDDs to disengage from the array. However, plugging it back in will resolve the issue, although sometimes it has to re-sync. In this case, however, all 8 drive lights were lit up, so there was something else going on.
   
  Next, I checked fdisk, and all 8 HDDs showed up. I also checked dmesg, and there were clearly errors relating to the array, but I didn’t see anything specifically related to a drive failure. Regardless, I don’t understand why a single drive failing would knock four of them out of the array. 
   
  I’ve done a ton of reading, and I’ve found some interesting items. I tried reassembling the array, but the best I could do was add the four missing drives as spares. I’m not sure why that happened, but it was as close as I got. I’ve noticed that the UUIDs are the same on all 8 drives. I’ve also read that it’s best to reassemble the array leaving one drive out to prevent a re-sync from occurring. In the Ubuntu forum archive I read a thread ([http://ubuntuforums.org/archive/index.php/t-410136.html](http://ubuntuforums.org/archive/index.php/t-410136.html)) that said that it’s important to know the exact order of the drives in the array, since the drive letters change. I will say, this is something that happens regularly. My drive letters change all the time, so I was worried about using the --build switch to rebuild the array, b/c I don’t know how to find out the original order of the drives in the array.
   
  One other item of note, in dmesg, I searched for info on all 8 HDDs (/dev/sdb - /dev/sdi). All the info was the same for all the drives w/ the exception of /dev/sdi, the drive that I have a feeling is the one that’s gone, or is going, bad. This was the info that was the same for all the drives including /dev/sdi:
   
  ```
jeffe@USC:/disk$ cat /var/log/dmesg |grep sdh
  [    9.121457] sd 1:2:0:0: [sdh] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
  [    9.121490] sd 1:2:0:0: [sdh] Write Protect is off
  [    9.121492] sd 1:2:0:0: [sdh] Mode Sense: 00 3a 00 00
  [    9.121509] sd 1:2:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
  [    9.121655]  sdh:
  [    9.589969]  sdh1
  [    9.590127] sd 1:2:0:0: [sdh] Attached SCSI disk
  [   18.415636] md: bind<sdh1>
```  However, for /dev/sdi, this info was added after the last line:
   
  ```
[   10.052109] md: unbind<sdi1>
  [   10.685573] md: export_rdev(sdi1)
  [   18.215051] md: export_rdev(sdi1)
  [   18.216447] md: export_rdev(sdi1)
```  At this point, I’m wondering what my next step should be. Any thoughts would be greatly appreciated. Thank you!
   
   
  Jeff

---

### Post by jmg999 on 2011-05-18
Is this in the correct forum, or should I post this elsewhere?

---

### Post by jmg999 on 2011-05-19
Anyone?

---

