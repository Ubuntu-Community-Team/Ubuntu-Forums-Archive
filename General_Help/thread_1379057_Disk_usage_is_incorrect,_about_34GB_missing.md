---
title: "Disk usage is incorrect, about 34GB missing"
date: 2010-01-12
forum: General Help
---

### Post by whatname on 2010-01-12
Hello guys,

  I've got this problem. Disk usage analyzer says I have a 70.3GB HDD which is correct. However it says that 55.7GB is used even though disk usage analyzer shows me that I have only 21.4GB filled up with data (filesystem). 
What is taking up all the space then?

Could someone help me with this issue? I have tried to search the forums with no satisfying result. Thank you very much.

Here is the disk usage analyzer output:
------------------------------------------------
[IMG]http://img.photobucket.com/albums/v234/mo-d/disk_usage-2.png[/IMG]

And here is the df output from terminal:
---------------------------------------------------
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73742752  58371236  11625564  84% /
udev                   1026116       244   1025872   1% /dev
none                   1026116      1508   1024608   1% /dev/shm
none                   1026116        76   1026040   1% /var/run
none                   1026116         0   1026116   0% /var/lock
none                   1026116         0   1026116   0% /lib/init/rw

---

### Post by John Bean on 2010-01-12
Not enough information to be precise, but I'd look at places that can't be accessed by ordinary users, like /root and /lost+found for example. It's not uncommon for people to use (say) nautilus as root to delete something then forget to empty trash, resulting in the "deleted" files still occupying space but invisible to the ordinary user.

---

### Post by whatname on 2010-01-12
> **John Bean said:**
> Not enough information to be precise, but I'd look at places that can't be accessed by ordinary users, like /root and /lost+found for example. It's not uncommon for people to use (say) nautilus as root to delete something then forget to empty trash, resulting in the "deleted" files still occupying space but invisible to the ordinary user.
Thank you for a fast response. I've checked /root and /lost+found but I havent found the culprit(s) yet.
I've also checked the trash in sudo but there is nothing there (if I am doing it correctly).

---

### Post by John Bean on 2010-01-12
In that case have a look for any large files in places you don't expect. Try```
sudo find / -size +100M -print | less
``` and see what comes up. Change the "100M" to any size you want, the purpose is just to see where the large files are. You'll get a few "false positives" with this rather crude approach (perhaps places like /sys/device/ for example) but it may give you a clue.

---

### Post by HiImTye on 2010-01-12
try using
```
gksudo boabab
```
in a terminal

---

### Post by John Bean on 2010-01-12
> **whatname said:**
> I've also checked the trash in sudo but there is nothing there (if I am doing it correctly).

Root's trash is normally in /root/.local/share/Trash but sometimes ends up in a folder called .Trash-0 if a root nautilus gets confused when invoked with sudo instead of gksu. In any case you can find them all easily```
sudo find / -name Trash -print
```or```
sudo find / -name .Trash* -print
```and see if any of them have unreasonable contents.

---

### Post by whatname on 2010-01-12
> **John Bean said:**
> In that case have a look for any large files in places you don't expect. Try```
sudo find / -size +100M -print | less
``` and see what comes up. Change the "100M" to any size you want, the purpose is just to see where the large files are. You'll get a few "false positives" with this rather crude approach (perhaps places like /sys/device/ for example) but it may give you a clue.
I tried that, it didnt show any "hidden" large files.

---

### Post by whatname on 2010-01-12
> **HiImTye said:**
> try using
```
gksudo boabab
```
in a terminal
Thanks, already tried that. Gives me the same result, unfortunately.

---

### Post by whatname on 2010-01-12
> **John Bean said:**
> Root's trash is normally in /root/.local/share/Trash but sometimes ends up in a folder called .Trash-0 if a root nautilus gets confused when invoked with sudo instead of gksu. In any case you can find them all easily```
sudo find / -name Trash -print
```or```
sudo find / -name .Trash* -print
```and see if any of them have unreasonable contents.
Unfortunately for me, there are no files in the trash folder you specified. :(

---

### Post by John Bean on 2010-01-12
I'm out of ideas on this one. Maybe your computer is just bad at maths ;-)

---

### Post by whatname on 2010-01-12
> **John Bean said:**
> I'm out of ideas on this one. Maybe your computer is just bad at maths ;-)
:D...ok, thanks for your support anyway. Maybe I will just reinstall Ubuntu ;)

---

### Post by warfacegod on 2010-01-12
Sounds like you are running into the system reserve.

Try adjusting it with this:

```
tune2fs -m x% /dev/sd
```

x is default 5%. If you have only the one drive then set it at 1 or 2% like this:

```
tune2fs -m 2% /dev/sda1
```

Your swap file could also account for some of that missing space.

---

### Post by audiomick on 2010-01-12
> **warfacegod said:**
> Sounds like you are running into the system reserve.

From what I have read, some "resource meters" take that into account, and some don't, although I don't know which does what. If accounts for apparently conflicting statistics, anyway.

---

### Post by warfacegod on 2010-01-12
> **audiomick said:**
> From what I have read, some "resource meters" take that into account, and some don't, although I don't know which does what. If accounts for apparently conflicting statistics, anyway.

I don't think the Usage Analyzer does nor will looking at the Properties. I believe Gparted does. That's how I figured this out for my external. Properties and Gparted were showing a difference of almost 50 GB. I used tune2fs and the discrepancy is now only like 6 MB.

---

### Post by john newbuntu on 2010-01-12
Sometime back, I noticed a thread between baobab and transmission bit torrent client.  Do you happen to use the latter?  Just curious.
Also, did you refresh/rescan of your filesystem/home folder in baobab and compare with the output given by du -k to narrow down the issues?

---

### Post by audiomick on 2010-01-12
There is a terminal command that does take it into account, but I can't remember what it is...

edit: happy coincidence, it just turned up in another thread

```
top
```
in terminal is what I was thinking of

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> Sounds like you are running into the system reserve.

Try adjusting it with this:

```
tune2fs -m x% /dev/sd
```

x is default 5%. If you have only the one drive then set it at 1 or 2% like this:

```
tune2fs -m 2% /dev/sda1
```

Your swap file could also account for some of that missing space.
Thanks for the tip. This is what I get though:

[I]tune2fs 1.41.9 (22-Aug-2009)
tune2fs: bad reserved block ratio - 2%
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
	[-i interval[d|m|w]] [-j] [-J journal_options] [-l]
	[-m reserved_blocks_percent] [-o [^]mount_options[,...]] 
	[-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
	[-M last_mounted_dir] [-O [^]feature[,...]]
	[-E extended-option[,...]] [-T last_check_time] [-U UUID]
	[ -I new_inode_size ] device[/I]

---

### Post by whatname on 2010-01-12
> **john newbuntu said:**
> Sometime back, I noticed a thread between baobab and transmission bit torrent client.  Do you happen to use the latter?  Just curious.
Also, did you refresh/rescan of your filesystem/home folder in baobab and compare with the output given by du -k to narrow down the issues?
Hi, yes I do use transmission quite often.

Baobab - refresh gives me the same results.

---

### Post by warfacegod on 2010-01-12
Sorry, put sudo in front of it.

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> Sorry, put sudo in front of it.
Tried that too, no difference though.

---

### Post by warfacegod on 2010-01-12
> **whatname said:**
> Tried that too, no difference though.

Then take out the 1 like this:

```
sudo tune2fs -m 2% /dev/sda
```

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> Then take out the 1 like this:

```
sudo tune2fs -m 2% /dev/sda
```

Still says: "*tune2fs: bad reserved block ratio - 2%*"

---

### Post by warfacegod on 2010-01-12
> **whatname said:**
> Still says: "*tune2fs: bad reserved block ratio - 2%*"

Then I'm stumped on that one. You only have the one drive? Do you have more than one partition on it?



Here's a thread to help you get back *some* space from the OS, read carefully before you decide to do things in it.

[http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager]("http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager")

You may also want to try:

```
sudo apt-get autoremove
```

---

### Post by warfacegod on 2010-01-12
How big is your swap space? If you're using Karmic 9.10, you can check with:

System> Admin.> Disk Utility or Gparted


If you don't have Gparted:

```
sudo apt-get install gparted
```

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> Then I'm stumped on that one. You only have the one drive? Do you have more than one partition on it?



Here's a thread to help you get back *some* space from the OS, read carefully before you decide to do things in it.

[http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager]("http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager")

You may also want to try:

```
sudo apt-get autoremove
```
No, I have just one partition and SWAP (3.1GB)

Autoremove freed about 2MB :)

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> How big is your swap space? If you're using Karmic 9.10, you can check with:

System> Admin.> Disk Utility or Gparted


If you don't have Gparted:

```
sudo apt-get install gparted
```
Here is output from gparted:
[IMG]http://img.photobucket.com/albums/v234/mo-d/gparted.png?t=1263309761[/IMG]

---

### Post by Slim Odds on 2010-01-12
> **whatname said:**
> Still says: "*tune2fs: bad reserved block ratio - 2%*"

drop the % sign

---

### Post by audiomick on 2010-01-12
the command
```
top
```
will show you that too.

```
mick@ubuntu-desktop:~$ top

top - 16:21:24 up  5:43,  2 users,  load average: 0.00, 0.00, 0.00
Tasks: 164 total,   3 running, 161 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.1%us,  1.0%sy,  0.0%ni, 97.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
[COLOR="Red"]Mem:   4057984k total,  1259284k used,  2798700k free,   154672k buffers[/COLOR]
[COLOR="Blue"]Swap:  6257268k total,        0k used,  6257268k free,   521624k cached
[/COLOR]
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 1763 root      20   0  383m  43m  14m S    1  1.1   4:33.48 Xorg              
 2378 mick      20   0  315m  53m  18m S    1  1.4   0:32.79 compiz.real       
 6113 mick      20   0  235m  16m  11m S    1  0.4   0:00.51 gnome-terminal    
 1260 root      20   0 22180 1236 1036 S    0  0.0   0:00.17 hald-addon-inpu   
 2382 mick      20   0  552m  44m  23m S    0  1.1   0:07.03 nautilus          

```

I have highlighted RAM in red and Swap in blue

---

### Post by whatname on 2010-01-12
> **Slim Odds said:**
> drop the % sign
Output: Setting reserved blocks percentage to 2% (374595 blocks)

Thanks, that gave me about 2GB

---

### Post by warfacegod on 2010-01-12
I just looked at your first post again and added up (roughly) everything shown in the disk usage shot and subtracted that from from what it says is used and got about 12 GB. So really, you are "only" short that, not 34 GB. Your swap brings it to about 9 GB missing, not great but better than 34. I'm betting that most of the rest is system reserve (still don't why it won't let you change it). Try rebooting and using tune2fs before starting anything else.

Here's another idea. Your swap space could be unnecessarily big. For instance, I have 2 GB RAM and 512 MB swap. Swap almost never gets used and because I don't Hibernate or Suspend, I could get away will shrinking it to 100 or so MB or possibly disposing of it entirely.

---

### Post by warfacegod on 2010-01-12
> **whatname said:**
> Output: Setting reserved blocks percentage to 2% (374595 blocks)

Thanks, that gave me about 2GB

Duh! My fault, haven't had my morning ubuntu beans yet, sorry!

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> I just looked at your first post again and added up (roughly) everything shown in the disk usage shot and subtracted that from from what it says is used and got about 12 GB. So really, you are "only" short that, not 34 GB. Your swap brings it to about 9 GB missing, not great but better than 34. I'm betting that most of the rest is system reserve (still don't why it won't let you change it). Try rebooting and using tune2fs before starting anything else.

Here's another idea. Your swap space could be unnecessarily big. For instance, I have 2 GB RAM and 512 MB swap. Swap almost never gets used and because I don't Hibernate or Suspend, I could get away will shrinking it to 100 or so MB or possibly disposing of it entirely.
Ok, according to the analyzer, 21.4GB is used by me, also 3GB of swap = 24.4GB. It however says that I use 55.7GB in total, that's 31GB of data space I am missing or not?

---

### Post by warfacegod on 2010-01-12
> **whatname said:**
> Ok, according to the analyzer, 21.4GB is used by me, also 3GB of swap = 24.4GB. It however says that I use 55.7GB in total, that's 31GB of data space I am missing or not?

Yeah, your right, again my fault no coffee yet sorry. Your gparted shot is showing about the same. I assume the filesystem properties would say the same.

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> Yeah, your right, again my fault no coffee yet sorry. Your gparted shot is showing about the same. I assume the filesystem properties would say the same.
I would recommend sleep instead of a coffee :D

---

### Post by warfacegod on 2010-01-12
> **whatname said:**
> I would recommend sleep instead of a coffee :D

But I just woke up! Besides, the wife will shoot me if I go back to sleep.

---

### Post by audiomick on 2010-01-12
Hallo.
The thread got me wondering and looking.
What does
```
df -h
```
tell you?

or maybe
```
df -a -h
```

---

### Post by warfacegod on 2010-01-12
Do a search in filesystem for gvfs-metadata there might be some very big files in there.

---

### Post by michy99 on 2010-01-12
Do you backup to an external drive or another partition? If ever do that without the target drive mounted, the backup gets stored at the mountpoint but on the root partition. Then, when the drive is mounted, it masks the misplaced backup.

---

### Post by whatname on 2010-01-12
> **audiomick said:**
> Hallo.
The thread got me wondering and looking.
What does
```
df -h
```
tell you?

or maybe
```
df -a -h
```

lukas@lukas-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   56G   14G  81% /
udev                 1003M  244K 1002M   1% /dev
none                 1003M  1.5M 1001M   1% /dev/shm
none                 1003M   64K 1003M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw


lukas@lukas-laptop:~$ df -a -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   56G   14G  81% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
udev                 1003M  244K 1002M   1% /dev
none                     0     0     0   -  /dev/pts
none                 1003M  1.5M 1001M   1% /dev/shm
none                 1003M   64K 1003M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
gvfs-fuse-daemon         0     0     0   -  /home/lukas/.gvfs

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> Do a search in filesystem for gvfs-metadata there might be some very big files in there.
Tried that no big files...

---

### Post by whatname on 2010-01-12
> **michy99 said:**
> Do you backup to an external drive or another partition? If ever do that without the target drive mounted, the backup gets stored at the mountpoint but on the root partition. Then, when the drive is mounted, it masks the misplaced backup.

I usually back my stuff either online or just a dvd, not much stuff I need to back up on this computer. ;)

---

### Post by warfacegod on 2010-01-12
Have you checked the drive for bad sectors and such?

I'm going to bow out of this thread and watch from the sidelines. I'm at a loss as to explaining 30 GB.

---

### Post by warfacegod on 2010-01-12
Try this:

[http://ubuntuforums.org/showthread.php?t=1088911&highlight=root+disk+space]("http://ubuntuforums.org/showthread.php?t=1088911&highlight=root+disk+space")

And This:

[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

### Post by whatname on 2010-01-12
> **warfacegod said:**
> Try this:

[http://ubuntuforums.org/showthread.php?t=1088911&highlight=root+disk+space]("http://ubuntuforums.org/showthread.php?t=1088911&highlight=root+disk+space")

And This:

[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")
Thanks, will try.

---

