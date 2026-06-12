---
title: "WTF Guys? New kernel wrecked my install!"
date: 2010-01-08
forum: General Help
---

### Post by tom.swartz07 on 2010-01-08
Hi all

I'm in a bit of a pickle. I just installed
my updates today, among them the newest Linux-image xxxxxx.17. After that, my entire
system became somewhat unstable. I noticed, twice, upon restarts GDM took really long to load - around 45 to 60 seconds. I figured it was a fluke. 

Next came something more serious. I was simply chatting on Pidgin when all of a sudden many if my icons became 'corrupted' - they changed to the squares with red x's in them. These icons were, but not limited to; battery indicator applet, wifi, and session
manager. I also notice at the same time that I could no longer type text in my Pidgin chat. The system was responsive through it all, but new windows and various other things wouldn't draw.  

I shutdown the computer with a hard reset- the session manager wouldn't work. I rebooted tomfind that
my Grub menu, that used to have a background image, was now altered and was only black and white text. Selecting my ubuntu partition resulted in the system hanging for about 15 seconds and a busybox terminal.

No kernel image will boot now, and from a liveCD, the hdd is shown 'unmountable' with a bad filesystem or bad blocks 

What exactly happened, and how do I fix it? Is there some way to fix the partition to access some logs on the subject?

Sorry if this post is a bit poorly formatted. I only have interet access from my iPod at this point. 

Any help is grand. Thanks!!!

---

### Post by s.fox on 2010-01-08
Hello,

With regards to the bad  blocks I would try what was suggested [here]("http://ubuntuforums.org/showthread.php?t=715050").   Please post back with an update :)

-Silver Fox

P.S.Is the LiveCD not giving you access to the internet?

---

### Post by tom.swartz07 on 2010-01-08
> **Silver_fox_ said:**
> Hello,

With regards to the bad  blocks I would try what was suggested [here]("http://ubuntuforums.org/showthread.php?t=715050").   Please post back with an update :)

-Silver Fox

P.S.Is the LiveCD not giving you access to the internet?

Hey SilverFox, 

Thanks for the guide; unfortunately the posted command to 'replace' the bad blocks is no longer supported in 9.10...


Heres the output of my other stuff though

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      128519       64228+  de  Dell Utility
/dev/sda2          129024    21100543    10485760    7  HPFS/NTFS
/dev/sda3   *    21109410   191237759    85064175    7  HPFS/NTFS
/dev/sda4       191237760   625137344   216949792+   f  W95 Ext'd (LBA)
/dev/sda5       308962080   314199269     2618595   dd  Unknown
/dev/sda6       191237886   300784994    54773554+  83  Linux
/dev/sda7       300785058   308962079     4088511   82  Linux swap / Solaris
/dev/sda8       369141633   394733114    12795741   83  Linux
/dev/sda9       394733178   581247764    93257293+   7  HPFS/NTFS

Partition table entries are not in disk order
```

```
ubuntu@ubuntu:~$ sudo fsck.reiserfs /dev/sda8
reiserfsck 3.6.21 (2009 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda8
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes 

reiserfs_open: the reiserfs superblock cannot be found on /dev/sda8.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

```

```
ubuntu@ubuntu:~$ sudo badblocks /dev/sda8
2300032
2300064
2300065
2300066
2300067
2300068
2300069
2300070
2300071
2300072
2300073
2300074
2300075
2300076
2300077
2300078
2300079
2300080
2300081
2300082
2300083
2300084
2300085
2300086
2300087
2300088
2300089
2300090
2300091
2300092
2300093
2300094
2300095
2300096
2300097
2300098
2300099
2300100
2300101
2300102
2300103
2300104
2300105
2300106
2300107
2300108
2300109
2300110
2300111
2300112
2300113
2300114
2300115
2300116
2300117
2300118
2300119
2300120
2300121
2300122
2300123
2300124
2300125
2300126
2300127
2300128
2300129
2300130
2300131
2300132
2300133
2300134
2300135
2300136
2300137
2300138
2300139
2300140
2300141
2300142
2300143
2300144
2300145
2300146
2300147
2300148
2300149
2300150
2300151
2300152
2300153
2300154
2300155
2300156
2300157
2300158
2300159
2300160
2300161
2300162
2300163
ubuntu@ubuntu:~$ 

```


HOLY MOLEY is that a lot of bad blocks! What really has me confused is- this drive is almost brand new! I got it just a few months ago - the week JUST before Karmic was released...

Would it be worth it to keep on with this drive, or should I contact the vendor and see if i could get a replacement?

What are my options?


PS- My liveCD seems to have a problem with the restricted broadcom driver for my wifi....
i guess ill have to occupy myself with my 9.04 partition until this gets sorted out.. dannngg

---

### Post by HappyFeet on 2010-01-08
> **tom.swartz07 said:**
> should I contact the vendor and see if i could get a replacement?


I would do that.

---

### Post by tom.swartz07 on 2010-01-08
As a precaution- I would like to see if my drive is still under warranty on Western Digital's site; how would i determine the serial number without physically removing the drive?

---

### Post by KeLa on 2010-01-08
> **tom.swartz07 said:**
> As a precaution- I would like to see if my drive is still under warranty on Western Digital's site; how would i determine the serial number without physically removing the drive?

use following:
```
sudo lshw | grep serial
```
it's the serial started with WD-

---

### Post by tom.swartz07 on 2010-01-08
> **KeLa said:**
> use following:
```
sudo lshw | grep serial
```
it's the serial started with WD-

That did it.

I was having some troubles with the support site, hopefully Ill get an email reply soon..


Just as a continuation, Im trying to exactly understand what may have caused this. Is it something from my actions or is that a Hard Drive defect? 

I have to laugh- the link posted here from SilverFox says that 10 bad blocks are enough to cause concern. I have 101! Fortunately, it seems like theyre all towards the end of the disk. 


What exactly is a bad block, how is it caused, and how could one prevent them (if possible)?

---

### Post by aklo on 2010-01-08
Can be from manufacturing defect or even from wear and tear.

Sometimes at first purchase you already have a bad sector in my country if the counts goes above like 5 badsector you can RMA it.

Having A bad sector is no big deal...my current 320GB harddisk has 1 bad sector for years already but it is still working.

The only thing you got to worry is when it gets more and more then your harddisk is in trouble.

Personal point of view: I think it happens randomly so it is not like your harddisk is only few months old and you can't get it. Like i said, sometimes a brand new hard disk will come with bad sectors too.

Just like dead pixel in monitor.

---

### Post by tom.swartz07 on 2010-01-08
> **aklo said:**
> Can be from manufacturing defect or even from wear and tear.

Sometimes at first purchase you already have a bad sector in my country if the counts goes above like 5 badsector you can RMA it.

Having A bad sector is no big deal...my current 320GB harddisk has 1 bad sector for years already but it is still working.

The only thing you got to worry is when it gets more and more then your harddisk is in trouble.

Personal point of view: I think it happens randomly so it is not like your harddisk is only few months old and you can't get it. Like i said, sometimes a brand new hard disk will come with bad sectors too.

Just like dead pixel in monitor.

I gotcha. It just seems alarming that after just under 3 months, i already have 101 bad blocks.

I mentioned it before, but no one commented about it. Is there an updated command to correct these bad blocks on the ext4 system? The guide that was posted was for 7.10 and ext3 filesystems...

---

### Post by tom.swartz07 on 2010-01-08
Okay: update

Im still waiting for a reply from WD about my drive, but I have managed to get my partition back to life for the time being, and im backing up like crazy.

all i did was run from a livecd
```
fsck /dev/sda8
```

on the partition (my case- 8) and i answered the questions - it prompted me to edit the bad blocks.
after that, the partition booted up great!


Hope this helps anyone with the same problem

---

