---
title: "mkdir slow"
date: 2009-07-28
forum: General Help
---

### Post by ubdime on 2009-07-28
I currently run a 6x500gb software raid5 on ext3 which is beginning to fill up.

/dev/md1             1kblocks: 2403601996 used: 2019513560 avail: 384088436  85% /save

I had it hovering around 1.5tb for a while until I recently filled it past 2tb. Since then, I've noticed that mkdirs seem to take up a lot of time.

This is a shared fileserver on a local network of 13 other computers. So at any given time, other people are accessing files over the network and I'll notice that it'll usually be transfering at ~1m/sec on average, 3-4m/s high and 10m/s peaks. The read/write is fine. Everything works great when I download onto it 10m/s from the internet while it's dishing out 10m/s to local users.

But whenever I use a mkdir on the raid, all other disk access stops for 10 seconds. Here's me doing a mkdir test.

[img]http://img11.imageshack.us/img11/2286/mkdir.png[/img]

I'll notice that shortly after I create this directory, I have a small window of time in which I can mkdir test2, mkdir test3, etc and it won't take up any time at all.

Here's me running fibmap script on a recently created directory on the raid which I put 6 files into.

```

root@lanfear:~/fibmap# ./fibmap.pl /save/s/ps/1/
Configurator ran OK; FIBMAP is 1; BLOCK_SIZE is 4096
    80  231.2MB  2959.95kB /save/s/ps/1/1.avi
    61  174.4MB  2927.02kB /save/s/ps/1/3.avi
    61  231.7MB  3889.31kB /save/s/ps/1/6.avi
    49  174.4MB  3645.63kB /save/s/ps/1/5.avi
    48  174.3MB  3719.08kB /save/s/ps/1/2.avi
    47  174.4MB  3800.17kB /save/s/ps/1/4.avi
Non-contiguous:
  Files 6 (1160.5MB, avg. 198055.67kB per file), blocks 346, average block 3434.49kB
No contiguous files found!

```

The first number is how many fragments the file is split into. Second # is the file size and 3rd # is the average size of each fragment.

As a comparison, I ran this script on a folder of 4 videos that are on my desktop (which is on a 2x250gb software raid1)

```

root@lanfear:~/fibmap# ./fibmap.pl ~/Desktop/temp/
Configurator ran OK; FIBMAP is 1; BLOCK_SIZE is 4096
   316  623.4MB  2020.24kB /home/dime/Desktop/temp/ap.wmv
   276  524.3MB  1945.29kB /home/dime/Desktop/temp/p2.avi
   220  587.9MB  2736.22kB /home/dime/Desktop/temp/dh.mp4
   165  327.9MB  2034.74kB /home/dime/Desktop/temp/im.wmv
Non-contiguous:
  Files 4 (2063.5MB, avg. 528247.11kB per file), blocks 977, average block 2162.73kB
No contiguous files found!

```

So, it doesn't seem like the raid is anymore fragmented than my normal system drive, which is sitting pretty at:
/dev/md0             1k blocks: 241251392  used: 58511572 avail: 170581436  26% /

fibmap.pl is a script from here: [http://www2.lut.fi/~ilonen/ext3_fragmentation.html](http://www2.lut.fi/~ilonen/ext3_fragmentation.html)

---

### Post by fleder on 2010-08-15
I'm having problems with a large ext3 file system as well, and this sounds kind of similar, so I'll ask in this thread.

The situation:
A Ubuntu 10.04 Server PC whose main purpose is being a data storage and serving some other PCs via Samba. It contains an internal true hardware RAID system which provides two virtual IDE drives and one large virtual drive on SATA.
Ubuntu Server starts from the 1st IDE drive; the large SATA one (largeext3) is the virtual drive I'm having performance issues with.

Have a look at this:
```
login as: xyz
xyz@ubuntuserv's password:
Linux ubuntuserv 2.6.32-24-server #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Sun Aug 15 19:43:51 CEST 2010

  System load:  1.96              Processes:           182
  Usage of /:   X.X% of XX.XXGB   Users logged in:     1
  Memory usage: 46%               IP address for lo:   127.0.0.1
  Swap usage:   0%                IP address for eth0: XXX.XXX.XXX.XXX

  => /media/largeext3 is using 90.1% of X.XXTB

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Sun Aug 15 02:59:52 2010 from XXXXXXXX
xyz@ubuntuserv:~$ cd /media/largeext3/testfolder/
xyz@ubuntuserv:/media/largeext3/testfolder$ time mkdir testmkdir

real    2m17.815s
user    0m0.000s
sys     0m0.560s
xyz@ubuntuserv:/media/largeext3/testfolder$ du -hs .
648G    .
xyz@ubuntuserv:/media/largeext3/testfolder$ find . | wc -l
25310
xyz@ubuntuserv:/media/largeext3/testfolder$

```While I did this, another PC was copying off some large files via Samba  using robocopy on Windows XP. This PC was furthermore playing a video  file from ubuntuserv using VLC.

As you can see, the creation of a folder takes over 2 minutes. 2 whole minutes during whose any IO on largeext3 freezes completely.

What happened was:

[LIST]
[*]I did the "time mkdir" command
[*]the HDD activity indicator LED went wild and stayed that way until mkdir was finished
[*]After about 20 seconds the video playback stopped and VLC crashed
[*]robocopy stalled and reported a "resource is no longer available" error
[/LIST]
This is just one example. Also, when other machines create folders over Samba while the file system is under some (only moderate or even low) load, they get connection errors since every IO seems to stall on largeext3 and the connection times out. People just can't copy stuff on that thing without getting errors!

There are some other programs running on ubuntuserv doing file access. When somebody creates a new directory while they are trying to write, they report "Access denied" errors and I have to clean up after them, it is very annoying.

Honestly: Something like this couldn't be used in any kind of productive environment as a file server. For an OS labeled "Server" this is unusably poor, people are supposed to use *that *on their business server machines?!

My question to you is as to how I can mitigate those performance bottlenecks, for instance by tweaking the ext3 file system. Maybe changes in the journaling procedures might help? Although I can't switch right now, does XFS handle large file systems better than that?
I'd rather not convert to ext4 because I'm currently incapable of doing full backups due to the vast amount of data.

largeext3 is NOT in /etc/fstab. It is not supposed to be mounted automatically.

Here's an excerpt of the output of "sudo tune2fs -l" done on largeext3:
```
tune2fs 1.41.11 (14-Mar-2010)
Filesystem volume name:   largeext3
Last mounted on:          <not available>
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Reserved block count:     0
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      567
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Fri Apr 30 22:23:46 2010
Last mount time:          Sat Aug  7 15:35:17 2010
Last write time:          Sat Aug  7 15:35:17 2010
Mount count:              5
Maximum mount count:      39
Last checked:             Fri Jul  2 21:16:18 2010
Check interval:           15552000 (6 months)
Next check after:         Wed Dec 29 20:16:18 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Journal backup:           inode blocks

```There's over 99,9% inodes left, the files on largeext3 are also usually large ones that don't change at all. One should think this would be a rather simple task for a file system...

---

### Post by fleder on 2010-09-19
There, I managed to back up all my data and re-format the large drive with XFS. The mkdir issue seems to have been solved, no more hangs and timeouts. Took about a week with all the copying involved, though. #-o

My conclusion from that: Large file system + ext3 = BAD.

---

### Post by jsalin on 2011-01-30
I noticed the same problem on my 1.7TB file system in my home server.

/dev/sda3             1.7T  1.4T  357G  80% /home

Linux desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

Creating a new directory takes sometimes even 15 seconds and the box is not under any kind of load CPU or hard disk wise. All other file operations like renaming and copying work at normal expected speeds. It seems to be a fault in ext3's design so I will start using definitely some other FS at partitions this large.

---

