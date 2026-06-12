---
title: "Reducing writes to SSD"
date: 2009-10-13
forum: General Help
---

### Post by BarsMonster2 on 2009-10-13
Hi there. 
I am using Ubuntu Server with an SSD, and working on reducing disk writes.

I have noatime mount option, /var/log and /tmp on tmpfs, but still have around 8 block/second writes in average. I have no idea where it comes from.
Also, munin graphs are on tmpfs.

Software running is Apache2, nginx, MySQL (very low load), munin for monitoring.

Current IOStat graph from munin looks like this:

Any ideas how can I monitor these writes and get rid of them? Any ideas?

[IMG]http://3.14.by/files/tf.14.by-iostat-day.png[/IMG]
[IMG]http://3.14.by/files/tf.14.by-iostat-week.png[/IMG]

---

### Post by P4man on 2009-10-13
try iotop to find out. Its in the repo's, and you can run it in batch mode (-b) and accumulated (-a) for logging.

---

### Post by BarsMonster2 on 2009-10-13
> **P4man said:**
> try iotop to find out. Its in the repo's, and you can run it in batch mode (-b) and accumulated (-a) for logging.
It has no -a, so I did -d 600 (accumulated for 10 minutes):

> Total DISK READ: 0 B/s | Total DISK WRITE: 0.67 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO>    COMMAND
   47 root           0 B/s    0.30 K/s  0.00 %  0.00 % [pdflush]
 2681 mysql          0 B/s    0.01 K/s  0.00 %  0.00 % mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/
 5778 mysql          0 B/s    0.07 K/s  0.00 %  0.00 % mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/
 3305 mysql          0 B/s    0.03 K/s  0.00 %  0.00 % mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/
  762 root           0 B/s    0.25 K/s  0.00 %  0.00 % [kjournald2]


That's all. How can this cause 8 blocks/second writes?

---

### Post by P4man on 2009-10-13
I certainly do have a '-a'; but Im on karmic right now, though it would surprise me that mattered. Check "man iotop". -d doesnt accumulate

---

### Post by BarsMonster2 on 2009-10-14
> **P4man said:**
> I certainly do have a '-a'; but Im on karmic right now, though it would surprise me that mattered. Check "man iotop". -d doesnt accumulate

Well, man have no signs of -a.
Any more ideas?

Is that possible to turn on aggressive write cache or something, so that it woun't flush writecache on disk at all? Server is at datacenter, so any power outages are extremely unlikely...

---

### Post by P4man on 2009-10-14
seems jaunty ships with a really old iotop version. The -a was added in v 0.3. Grab a newer one here:
[http://guichaz.free.fr/iotop/NEWS](http://guichaz.free.fr/iotop/NEWS)

As for the write delay, Im not sure, but I just stumbed across this:

[http://www.ubuntugeek.com/how-to-increase-ext3-and-reiserfs-filesystems-performance.html](http://www.ubuntugeek.com/how-to-increase-ext3-and-reiserfs-filesystems-performance.html)

Have a look at this:

> Remove update of access time for files

Having the modified time change you can understand but having the system updating the access time every time a file is accessed is not to my liking. According to the manual the only thing that might happen if you turn this off is that when compiling certain things the make might need that info.

To change this do the following

sudo vi /etc/fstab

add the following marked in bold

/dev/hda1 / ext3 defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1

Now reboot and enjoy a much faster system

Gonna have to try that myself :) If I understand it correctly, it should also reduce the disk writes considerably for you if there is a lot of file access going on.

---

### Post by BarsMonster2 on 2009-10-14
I already did noatime. data=write  back is not available in  2.6.28 kernel AFAIK. I am not sure I am ready to upgrade kernel just to enable writeback.

Thanks for the iotop update, trying that now.

---

### Post by t0p on 2009-10-14
I assume you're looking to reduce writes to disk because of concerns about SSD limited life expectancy?

If so, perhaps [this article]("http://www.storagesearch.com/ssdmyths-endurance.html") will put your mind at rest.  The author puts estimated life span of a 64 GB SSD at 51 years.

---

### Post by BarsMonster2 on 2009-10-14
> **t0p said:**
> I assume you're looking to reduce writes to disk because of concerns about SSD limited life expectancy?

If so, perhaps [this article]("http://www.storagesearch.com/ssdmyths-endurance.html") will put your mind at rest.  The author puts estimated life span of a 64 GB SSD at 51 years.

Yeah, I've seen this. I cannot agree with his estimations without practical tests (manufacturers keep saying 10'000, not 2'000'000. Even for SLC they say 100'000.). 

Anyway, I am perfectionist. I see these constant 8 block/second writes, and it looks annoying, I want to know where it comes from.

---

### Post by BarsMonster2 on 2009-10-20
Still no luck pinning down these writes :-(

---

### Post by Klondike on 2010-10-20
You ever figure it out?

---

### Post by psusi on 2010-10-20
> **BarsMonster2 said:**
> Yeah, I've seen this. I cannot agree with his estimations without practical tests (manufacturers keep saying 10'000, not 2'000'000. Even for SLC they say 100'000.). 

Anyway, I am perfectionist. I see these constant 8 block/second writes, and it looks annoying, I want to know where it comes from.

It's 100,000 writes PER BLOCK, not total, so for a 64gb disk with a 512kb erase block, that is AT LEAST 48 years at 8 writes per second, probably more since not every write will cause a block to be erased and re-written.

---

### Post by BarsMonster2 on 2010-10-20
> **psusi said:**
> It's 100,000 writes PER BLOCK, not total, so for a 64gb disk with a 512kb erase block, that is AT LEAST 48 years at 8 writes per second, probably more since not every write will cause a block to be erased and re-written.
5-10k writes, not 100k.

Yes, I figured it out, it was munin :-)
I just moved it to tmpfs

---

### Post by Klondike on 2010-10-20
Oh, okay, that's comforting. I'm likely to buy an SSD in the next day or two. It's good to know that with noatime and tmpfs, Ubuntu can be reasonably efficient with them.

---

