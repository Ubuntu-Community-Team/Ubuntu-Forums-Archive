---
title: "RAID 10 high cpu utilization freezes computer"
date: 2012-07-01
forum: General Help
---

### Post by quickk on 2012-07-01
Can anyone with experience with raid 10 (or raid in general) comment on what is typical for CPU utilization?   [I have a raid 10 setup using 2 x 2TB drives]("http://ubuntuforums.org/showthread.php?t=1984249"), and when there is any io going on, I get on average 100% utilization of 2 cpus.   What's worse: when the raid drives are busy the system sometimes completely locks up!   

I am surprized that this is the case as I have a decent system (2.8 GHz core 2 quad, 12 GB ram).  

Is this normal?   If so, then I think that I'll go back to having no raid since this makes the system way less responsive overall.

---

### Post by DJ_Max on 2012-07-01
RAID 10 requires a minimum of 4 hard drives, so you're using fake raid which will degrade performance. So either use RAID 1, or buy two more hard drives.

---

### Post by quickk on 2012-07-01
Thanks for your reply.   With mdadm, you can use 2 drives to do raid 10.   It is software raid, true, but the performance is similar to software raid 0 for reading (see the link in my first post).   

If I get 2 more drives, will I have the same cpu utilization problems than I have with 2 drives?  I'm just wondering what other people with raid 10 setups are experiencing.

---

### Post by DJ_Max on 2012-07-01
You have something wrong regardless, there is no reason you should be using 100% CPU.

What processes are utilizing all of your CPU power?

---

### Post by quickk on 2012-07-03
That's what I thought...  the problem is that I don't have any other processes going on.  For example, simply copying a large file onto the raid array will result in very high cpu useage.

Here's an example: (downloading the kubuntu image) [IMG]http://s18.postimage.org/929tsw1y1/high_cpu.jpg[/IMG]

The same thing happens when just copying big file from one disk to another.

I'm really not sure what is going on!

---

### Post by s3a on 2012-07-03
Open a terminal, type "top" (without the quotes) and then press enter. It will show you which program is using the most of your CPU.

---

### Post by quickk on 2012-07-03
I tried top, but the problem is that it does not actually show that anything is using the cpu.   The problem is 100% reproducible each time I have lots of disk i/o.   

Can anyone else with a raid setup (mdadm) comment on what their cpu utilization is when copying a large file onto the array?

---

### Post by DJ_Max on 2012-07-03
One of your drives could be going bad.

---

### Post by quickk on 2012-07-03
Maybe, but I doubt it.   They are brand new (1 month old), and the problem has existed since the start.  Also, the smart status reports that everything is ok.  

This is frustrating... I think that I might just abandon RAID.

---

### Post by rubylaser on 2012-07-03
My CPU usage on a 8 disk RAID6 mdadm array on an old AMD 4600+ X2 is around 15% when I transfer a large file. Try taking a look at iotop while you transfer files to the array.

```
sudo -i
apt-get install iotop
iotop -a -p $(sed 's, , -p ,g' <<<`pgrep "_raid|_resync|jbd2"`)
```
It should give you output in this format...
```
Total DISK READ:       0.00 B/s | Total DISK WRITE:      27.95 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                       
  287 be/3 root          0.00 B    152.00 K  0.00 %  0.02 % [jbd2/sda1-8]
  721 be/3 root          0.00 B     84.02 M  0.00 %  0.02 % [jbd2/md0-8]
  274 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [md0_raid6]
```

---

### Post by rubylaser on 2012-07-03
> **quickk said:**
> Maybe, but I doubt it.   They are brand new (1 month old), and the problem has existed since the start.  Also, the smart status reports that everything is ok.  

This is frustrating... I think that I might just abandon RAID.

No need to abandon RAID, you really should just be using a RAID1.  I know of many users in the Server section that use mdadm RAID10 with a lot of success, but they all use 4 or more drives.

---

### Post by DJ_Max on 2012-07-03
> **quickk said:**
> Maybe, but I doubt it.   They are brand new (1 month old), and the problem has existed since the start.  Also, the smart status reports that everything is ok.  

This is frustrating... I think that I might just abandon RAID.
Drives are more likely to fail within 2 months than any other time, just saying.

---

### Post by quickk on 2012-07-04
> Try taking a look at iotop while you transfer files to the array.

This is what I get when copying a large file:

[IMG]http://s17.postimage.org/nyhwubv5r/iotop.jpg[/IMG]

Nothing else was running in the same time.   The top command said that kio_file was using 10% or so, but that's it.   The system monitor shows that almost all cpus are at 100% (like in my screenshot above).

---

### Post by rubylaser on 2012-07-04
> **quickk said:**
> This is what I get when copying a large file:

[IMG]http://s17.postimage.org/nyhwubv5r/iotop.jpg[/IMG]

Nothing else was running in the same time.   The top command said that kio_file was using 10% or so, but that's it.   The system monitor shows that almost all cpus are at 100% (like in my screenshot above).

Well, your array is definitely capped out on IO.  Can you run iotop without any options and paste what that gives you?  That should show if one disk is at fault.  This is strongly pointing at the atypical RAID10 setup as the culprit at this point.

---

### Post by quickk on 2012-07-04
Great.   I installed linux mint 13 on a different drive, ensured that I told the installer not to use any of the raid drives, and now it looks like my raid array is completely fubared and my original Kubuntu won't boot.

I tried the following:

```
sudo mdadm --assemble --scan
```

and got this error:

```
mdadm: Devices UUID-bc6275e2:882f945d:6f378849:15c417a4 and UUID-bc6275e2:882f945d:6f378849:15c417a4 have the same name: /dev/md/1
mdadm: Duplicate MD device names in conf file were found.

```

Ugh...  I thought that RAID was supposed to be robust, but my experience so far is completely the opposite.  I backup up most of the data on the array, but it looks like I forgot a few things.  

Anyone know what could be the problem?

---

### Post by rubylaser on 2012-07-04
It's hard to say way happenned, but as long as you didn't install to your RAID array, the data should be fine (you might have messed up GRUB if Mint setup GRUB on the wrong disk).  Why don't you take a look at the superblock info on each disk to verify.  Also, based on this message, it appears that your mdadm.conf file is messed up.  Could you post that too?

```
mdadm -E /dev/sd[ab]1
```

```
cat /etc/mdadm/mdadm.conf
```

---

### Post by quickk on 2012-07-05
Thanks rubylaser for your help.   I think what happened is that linux mint installed grub onto one of the drives.   

I ended up rebuilding the array with one of the drives "missing" like this:

```
sudo mdadm --create /dev/md1 --metadata 1.2 --level=10 --layout=f2 --raid-devices=2 /dev/sda1 missing 

```

I was quite nervous about doing this, but fortunately it worked!   No data loss, and the array was back up instantly.  I then added the second drive like this:
```
sudo mdadm --manage /dev/md1 --add /dev/sdb1 

```

It took a few hours to rebuild, but now my array is back to normal!
In hindsight, probably just recreating the array with both drives would of worked too.


So now I just have to figure out what was the problem with the high cpu, but I'll leave this for another day.  Most likely it has something to do with using raid 10 with only two drives, but according to [this page]("http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10"), it shouldn't be a problem.

---

