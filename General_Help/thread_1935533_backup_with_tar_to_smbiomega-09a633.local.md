---
title: "backup with tar to smb://iomega-09a633.local/"
date: 2012-03-04
forum: General Help
---

### Post by qwertyjjj on 2012-03-04
I would like to backup my computer to my network drive.
However, when I use df it does not appear even though I can navigate to it through nautilus.
ANy ideas how I can issue the command:
tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev / 

but replace backup.tar.gz with the external drive location?

---

### Post by qwertyjjj on 2012-03-05
anyone?

---

### Post by qwertyjjj on 2012-05-07
> **qwertyjjj said:**
> anyone?

any ideas?
When I do df I get:
```

j-media-centre@jmediacentre-A880G:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            957563524 556094604 352827436  62% /
udev                   1922972         4   1922968   1% /dev
tmpfs                   773148       956    772192   1% /run
none                      5120         0      5120   0% /run/lock
none                   1932868      1536   1931332   1% /run/shm
/home/j-media-centre/.Private
                     957563524 556094604 352827436  62% /home/j-media-centre


```

The drive is not there even though I can see it in the home folder under Browse network

---

### Post by bab1 on 2012-05-07
> **qwertyjjj said:**
> any ideas?
When I do df I get:
```

j-media-centre@jmediacentre-A880G:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            957563524 556094604 352827436  62% /
udev                   1922972         4   1922968   1% /dev
tmpfs                   773148       956    772192   1% /run
none                      5120         0      5120   0% /run/lock
none                   1932868      1536   1931332   1% /run/shm
/home/j-media-centre/.Private
                     957563524 556094604 352827436  62% /home/j-media-centre


```

The drive is not there even though I can see it in the home folder under Browse network

If you have mounted the share via Nautilus then the mount point is at ~/.gvfs (/home/*user_login*/.gvfs).  It's a hidden folder so you don't normally see it.  You could use this as the destination if you like.  If that is cumbersome or has other problems then un-mount the share and mount it via the command line (i.e. *sudo mount -t cifs //server/share /mount/point*).

---

### Post by qwertyjjj on 2012-05-07
edit holding post

---

### Post by qwertyjjj on 2012-05-09
The backup is running but it is taking forever!
It is only 600Gb or so and it has been running for about 2 days now.
Is tar the best compression to use?

---

### Post by bab1 on 2012-05-09
> **qwertyjjj said:**
> The backup is running but it is taking forever!
It is only 600Gb or so and it has been running for about 2 days now.

***Is tar the best compression to use?***
What is 600 Gb? Is that 600 giga bits or 600 giga bytes?

Have you translated that figure into a useful standard benchmark?

A website with fairly simple conversion mechanism can be found [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://web.forret.com/tools/bandwidth.asp").

I don't think *tar* is your problem.

---

### Post by qwertyjjj on 2012-05-10
> **bab1 said:**
> What is 600 Gb? Is that 600 giga bits or 600 giga bytes?

Have you translated that figure into a useful standard benchmark?

A website with fairly simple conversion mechanism can be found [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://web.forret.com/tools/bandwidth.asp").

I don't think *tar* is your problem.

GBytes

I'm not sure what the conversion rate is but it seems overly slow.
An imaging backup for example, would do this much quicker wouldn't it?

---

### Post by hjclaes on 2012-05-10
First, you have to analyze where the bottleneck is.

install eg. dstat:

$ sudo apt-get install dstat

then start it:

$ dstat

You should see, if the network or the cpus are the issue.

btw, what type of cpu and what network do you have? (This also means the interfaces of the affected computers.)

Regards, ixo

---

### Post by bab1 on 2012-05-10
> **qwertyjjj said:**
> GBytes

I'm not sure what the conversion rate is but it seems overly slow.
An imaging backup for example, would do this much quicker wouldn't it?

I provided you with a site that does the conversion for you.  Did you try it?

---

### Post by qwertyjjj on 2012-05-10
> **bab1 said:**
> I provided you with a site that does the conversion for you.  Did you try it?

The input on that site is the cvonversion rate not the file size as far as I can see.
I am transferring 600GB of data over an ethernet cable internal LAN with the NAS drive plugged into the router and the computer plugged into the router.

---

### Post by qwertyjjj on 2012-05-10
> **hjclaes said:**
> First, you have to analyze where the bottleneck is.

install eg. dstat:

$ sudo apt-get install dstat

then start it:

$ dstat

You should see, if the network or the cpus are the issue.

btw, what type of cpu and what network do you have? (This also means the interfaces of the affected computers.)

Regards, ixo

Gives this:
```

j-media-centre@jmediacentre-A880G:~$ dstat
You did not select any stats, using -cdngy by default.
----total-cpu-usage---- -dsk/total- -net/total- ---paging-- ---system--
usr sys idl wai hiq siq| read  writ| recv  send|  in   out | int   csw 
 41  12  47   0   0   1|1952k   28k|   0     0 |  86B  171B|6565  9432 
 69   9  21   0   0   1|2048k  144k|  79k 1879k|   0     0 |5715  9383 
 69  10  21   0   0   0|1792k   88k|  81k 1947k|   0    88k|5921  9228 
 44  10  44   0   0   1|1808k    0 |  81k 1921k|   0     0 |6639  9835 
 44  11  44   0   0   1|1536k    0 |  72k 1725k|   0     0 |6033  8946 
 48  12  39   0   0   1|1792k    0 |  75k 1785k|   0     0 |6434  9610 
 44  12  42   0   0   1|1792k    0 |  83k 1964k|   0     0 |6547  9828 
 44  10  45   0   0   1|1792k    0 |  79k 1874k|   0     0 |6316  9471 
 45  10  44   1   0   0|1792k   44k|  78k 1849k|   0     0 |6369  9593 
 43   9  47   0   0   1|1408k    0 |  65k 1538k|   0     0 |5438  8211 ^C

```

Athlon 3.1GHz and 4Gb RAM, it's on a LAN via home router (wired)

---

### Post by bab1 on 2012-05-10
> **qwertyjjj said:**
> The input on that site is the cvonversion rate not the file size as far as I can see.
I am transferring 600GB of data over an ethernet cable internal LAN with the NAS drive plugged into the router and the computer plugged into the router.
Your not just transferring files.  You are tarring and compressing those files and then transferring the gziped tarball.  FYI: if you are compressing already compressed data then the tarball can be bigger rather than smaller than the original data.  There is CPU and HDD overhead for this.   


Rate = file size / time

If you are transferring 600GB every 2 days that's the equivalent of:

```
300GB/day
12.50 GB/hour
208.33 MB/minute  (Megabytes)
3.47 MB/second    (Megabytes)
27.78 Mb/second   (Megabits)

Fast Ethernet is 100 Mb/second.

```

I wonder what overhead the entire network takes?  Something for you to figure out.

---

### Post by qwertyjjj on 2012-05-11
> **bab1 said:**
> Your not just transferring files.  You are tarring and compressing those files and then transferring the gziped tarball.  FYI: if you are compressing already compressed data then the tarball can be bigger rather than smaller than the original data.  There is CPU and HDD overhead for this.   


Rate = file size / time

If you are transferring 600GB every 2 days that's the equivalent of:

```
300GB/day
12.50 GB/hour
208.33 MB/minute  (Megabytes)
3.47 MB/second    (Megabytes)
27.78 Mb/second   (Megabits)

Fast Ethernet is 100 Mb/second.

```

I wonder what overhead the entire network takes?  Something for you to figure out.

Well, it's been 4 days now and it#s still not finished :) so the rate is even slower.
That's why I'm woindering if imaging would be a better approach?

---

### Post by bab1 on 2012-05-11
> **qwertyjjj said:**
> Well, it's been 4 days now and it#s still not finished :) so the rate is even slower.
That's why I'm woindering if imaging would be a better approach?
It sounds like the backup has stalled.  So we don't know what the rate of transfer is/was when it was working and what happened later on.  I don't know if it will help us at this point, but here is a  [**_[COLOR="Blue"]very basic tutorial[/COLOR]_**]("http://articles.slicehost.com/2010/11/12/using-dstat-to-check-i-o-and-swap") on dstat.

The original question in this thread was how to mount the drive.  I must confess that I never gave much thought about how or what you should backup on the computer.

I don't see any reason to backup the installed OS.  I backup only the data on any of my hosts.  I can install the OS from an ISO and configure it faster that trying to restore it.  Once the host (computer) is up I just transfer the data from the backup to that working computer. 

I use [**_[COLOR="Blue"]rsnapshot[/COLOR]_**]("http://rsnapshot.org/") to backup all data on all the computers in my home network.  These are typical Ubuntu installs.  The data on each is about 30GB for each machine  It takes about an hour to finish the first time.  After that only the added files or changes to the files are transferred.  So a backup is usually be under 2 minutes per day.

The data is not compressed at all so it is very easy to restore individual files or the all the data with copy  (cp).  If you wanted to compress the data with gzip or make compressed tarballs, I would do that on your Ubuntu machine (maybe to a directory like /srv/backup) and then move it to the NAS with rsanpshot.

I don't use tar (TapeARchive) anymore.  There is no need to archive the data during backup if you use rsnapshot or rsync.

Does that give you ideas?

---

### Post by hjclaes on 2012-05-12
> **qwertyjjj said:**
> Gives this:
```

j-media-centre@jmediacentre-A880G:~$ dstat
You did not select any stats, using -cdngy by default.
----total-cpu-usage---- -dsk/total- -net/total- ---paging-- ---system--
usr sys idl wai hiq siq| read  writ| recv  send|  in   out | int   csw 
 41  12  47   0   0   1|1952k   28k|   0     0 |  86B  171B|6565  9432 
 69   9  21   0   0   1|2048k  144k|  79k 1879k|   0     0 |5715  9383 
 69  10  21   0   0   0|1792k   88k|  81k 1947k|   0    88k|5921  9228 
 44  10  44   0   0   1|1808k    0 |  81k 1921k|   0     0 |6639  9835 
 44  11  44   0   0   1|1536k    0 |  72k 1725k|   0     0 |6033  8946 
 48  12  39   0   0   1|1792k    0 |  75k 1785k|   0     0 |6434  9610 
 44  12  42   0   0   1|1792k    0 |  83k 1964k|   0     0 |6547  9828 
 44  10  45   0   0   1|1792k    0 |  79k 1874k|   0     0 |6316  9471 
 45  10  44   1   0   0|1792k   44k|  78k 1849k|   0     0 |6369  9593 
 43   9  47   0   0   1|1408k    0 |  65k 1538k|   0     0 |5438  8211 ^C

```Athlon 3.1GHz and 4Gb RAM, it's on a LAN via home router (wired)

Ok,

I assume it's a dual core cpu, right?

If yes, then you have a little bit more than 50% cpu usage, which means one core is running the gzip compression.
On the io side, you read about 1.8MB from the disk and write about the same over the network which means, you are saving un-compressible data at the moment.

Your backup is still running. You should have a look at the generated tar file (eg. with `ls -lk` or `ls -lh`) which should grow (slowly).

So everything seems to be fine, despite the fact that your method of saving is - let's say - not the best one:

[LIST]
[*]you make only full backups
[*]you are compressing files which are not compressible
[*]if you want to restore a file you have to wait a day or so
[*]if your tar file is broken at some point, you will lose all data from that point
[*]others
[/LIST]
I'm using storebackup.
for a feature list, see: [http://www.nongnu.org/storebackup/en/](http://www.nongnu.org/storebackup/en/)

It's very space efficient because of deduplication spread over all files, so it recognizes renamed or copied files and renamed directories also (which also speeds things up). You will probably use less space (even for the first backup) than with you tar approach (and probably less than with all other free solutions).

The very first backup will be slow also (but much faster than tar with compression), because it will calculate md5 sums for all files and do compression also (but only if you want and only for compressible files). It also has very high sophisticated ways to delete old backups. - And - very important: You can restore you files easily and fast with a simple copy command without the need to use storeBackup itself. Naturally, you can use it's commands, but it's important that the storage format is native.

Regards, hjclaes

---

### Post by qwertyjjj on 2012-05-12
> **hjclaes said:**
> Ok,

I assume it's a dual core cpu, right?

If yes, then you have a little bit more than 50% cpu usage, which means one core is running the gzip compression.
On the io side, you read about 1.8MB from the disk and write about the same over the network which means, you are saving un-compressible data at the moment.

Your backup is still running. You should have a look at the generated tar file (eg. with `ls -lk` or `ls -lh`) which should grow (slowly).

So everything seems to be fine, despite the fact that your method of saving is - let's say - not the best one:

[LIST]
[*]you make only full backups
[*]you are compressing files which are not compressible
[*]if you want to restore a file you have to wait a day or so
[*]if your tar file is broken at some point, you will lose all data from that point
[*]others
[/LIST]
I'm using storebackup.
for a feature list, see: [http://www.nongnu.org/storebackup/en/](http://www.nongnu.org/storebackup/en/)

It's very space efficient because of deduplication spread over all files, so it recognizes renamed or copied files and renamed directories also (which also speeds things up). You will probably use less space (even for the first backup) than with you tar approach (and probably less than with all other free solutions).

The very first backup will be slow also (but much faster than tar with compression), because it will calculate md5 sums for all files and do compression also (but only if you want and only for compressible files). It also has very high sophisticated ways to delete old backups. - And - very important: You can restore you files easily and fast with a simple copy command without the need to use storeBackup itself. Naturally, you can use it's commands, but it's important that the storage format is native.

Regards, hjclaes

Don't sotebackup and rsync only sync the files?
Ideally, I'd want a full computer backup as I have settings and other things savedd.
I;ve seen some imaging utilities on the Live CD but not hw to transfer an image across to a network drive...

---

### Post by hjclaes on 2012-05-12
See

[http://www.nongnu.org/storebackup/en/node52.html#myfaqCompleteBackup](http://www.nongnu.org/storebackup/en/node52.html#myfaqCompleteBackup)

There is also the possibility to make backups of devices (with deduplication), see:

[http://www.nongnu.org/storebackup/en/node37.html](http://www.nongnu.org/storebackup/en/node37.html)

But if you want to use it, it's better to read the (whole) documentation.

Also, I do not save the whole box; just /etc and my own files. You can generate a list of all installed packages and save that also to be able to re-install the box also.

But that depends on your needs.

Regards

---

### Post by qwertyjjj on 2012-06-09
rsync seems to error on this:

```

j-media-centre@jmediacentre-A880G:~/.gvfs/backups on iomega$ **sudo rsync -azvv /home/j-media-centre/ /home/j-media-centre/.gvfs/backups\ on\ iomega/**
sending incremental file list
rsync: readlink_stat("/home/j-media-centre/.gvfs") failed: Permission denied (13)
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: ERROR: cannot stat destination "/home/j-media-centre/.gvfs/backups on iomega/": Permission denied (13)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(583) [Receiver=3.0.8]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]


```

---

