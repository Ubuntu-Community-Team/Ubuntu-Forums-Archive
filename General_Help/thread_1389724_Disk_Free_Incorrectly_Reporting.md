---
title: "Disk Free Incorrectly Reporting"
date: 2010-01-24
forum: General Help
---

### Post by madmonkeyz on 2010-01-24
I have an computer that mounts an external hard drive for backups. The Computer hard drive is about 110 GB; the external drive is 120 GB.

When I do a df -h it tells me there is 97% in use.

Checking the computer harddrive I am using about 52.8 GB (of the 110 GB)
501,579 items, totalling 52.8 GB
(some contents unreadable)

The external drive is using roughly 49GB of the 120 GB available.

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/xanadu-root
                     114536088 104995108   3768692  97% /
udev                   1030572       328   1030244   1% /dev
none                   1030572      1008   1029564   1% /dev/shm
none                   1030572       228   1030344   1% /var/run
none                   1030572         0   1030572   0% /var/lock
none                   1030572         0   1030572   0% /lib/init/rw
/dev/sda1               241116     63114    165554  28% /boot
/dev/sdb1            117189600  48141920  69047680  42% /media/WD Passport__

It seems like the total % is a reflect of total space consumed calculated off of ONE of the hard drives. Am I insane?

---

### Post by warfacegod on 2010-01-24
Your state of mind remains to be seen. It may have nothing to do with the validity of your results.

I just checked mine and compared it to what Gparted says and the number are pretty much the same. Are you sure you haven't run up against your system reserve?

---

### Post by madmonkeyz on 2010-01-24
No. I'm not sure if I've run against my system reserves (whatever that means). If I select my root drive and go to properties it shows 52.8 GB should be about 52% on a 110GB drive. Unmounting the external hard drive doesn't seem to help:

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/xanadu-root
                      110G  101G  3.6G  97% /
udev                 1007M  328K 1007M   1% /dev
none                 1007M  1.1M 1006M   1% /dev/shm
none                 1007M  228K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda1             236M   62M  162M  28% /boot

I certainly don't know where the 101GB used is coming from but I'd like to find out! (Don't make fun of crazy people...)

---

### Post by madmonkeyz on 2010-01-24
After unmounting the external harddrive and rebooting the df -h shows:

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/xanadu-root
                      110G  101G  3.7G  97% /
udev                 1007M  320K 1007M   1% /dev
none                 1007M  412K 1007M   1% /dev/shm
none                 1007M  204K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
none                  110G  101G  3.7G  97% /var/lib/ureadahead/debugfs
/dev/sda1             236M   62M  162M  28% /boot

So supposedly ureadahead/debugfs folder is the culprit. 

When I do a status ureadahead from the terminal:
stop/waiting

So now what? Any kernel experts out there? I have no idea what the problem is or how to fix it. Anybody else run into this? Running (9.10 Ubuntu)

---

### Post by madmonkeyz on 2010-01-24
*bump*

---

### Post by madmonkeyz on 2010-01-24
Found this link trying to find a solution to the problem. I can't make sense of it, but if anyone is wondering I have 32-bit system and it appears to be the same problem.

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/499773]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/499773")

---

### Post by warfacegod on 2010-01-24
It's not nice bump a thread before a day or so. Naughty, naughty.

Is Disk Utility saying the same thing?

(I only laugh with crazy people not at them.)

---

### Post by madmonkeyz on 2010-01-24
I live in metric time (the days are shorter) I'll have to convert before posting/bumping.

The best I can tell (and that's not very well) /var/lib/ureadahead/debugfs has the majority of the space. I don't know what it is or what its for, I suspect this will be a problem in the foreseeable future (metric or imperial time).

Any suggestions?

---

### Post by warfacegod on 2010-01-24
This is the description in Synaptic about ureadahead:

> über-readahead is used during boot to read files in advance of when
they are needed such that they are already in the page cache,
improving boot performance.

Its data files are regenerated on the first boot after install, and
either monthly thereafter or when packages with init scripts or
configs are installed or updated.

ureadahead requires a kernel patch included in the Ubuntu kernel.

Canonical provides critical updates for ureadahead until April 2011.

It basically helps your computer start faster. My ureadahead folder contains a total of 550.6 KB. I don't see any reason to keep it if it's chewing up that much of your hard drive. Marking it for complete removal should empty out that folder. You can get rid of sreadahead too.

---

### Post by blueridgedog on 2010-01-24
It may be simply that you have large files in your trash or root's trash and debugfs is simply fooling you.

What is the output of:

```
cd /
sudo du --max-depth=1 | sort -g
```

Also, keep in mind that 5% of a disk is reserved for root.

---

### Post by madmonkeyz on 2010-01-25
The results:
andrew@xanadu:/$ sudo du --max-depth=1 | sort -g
[sudo] password for andrew: 
du: cannot access `./proc/3359/task/3359/fd/3': No such file or directory
du: cannot access `./proc/3359/task/3359/fdinfo/3': No such file or directory
du: cannot access `./proc/3359/fd/3': No such file or directory
du: cannot access `./proc/3359/fdinfo/3': No such file or directory
du: cannot access `./home/andrew/.gvfs': Permission denied
0	./proc
0	./sys
4	./initrd
4	./mnt
4	./.pulse
4	./selinux
16	./lost+found
92	./tmp
200	./srv
820	./dev
5528	./bin
8928	./sbin
16892	./root
23044	./etc
56951	./boot
208944	./opt
399536	./lib
423296	./var
4974496	./usr
7297432	./home
91371064	./media
104787267	.

I am a bit reticent to remove a package if it is required, but if continues to proceed like this I might have to. So, is something "lying" to me?

---

### Post by warfacegod on 2010-01-25
> **blueridgedog said:**
> It may be simply that you have large files in your trash or root's trash and debugfs is simply fooling you.

What is the output of:

```
cd /
sudo du --max-depth=1 | sort -g
```

Also, keep in mind that 5% of a disk is reserved for root.

We've already discussed that possibility and 5% doesn't even come close to accounting for 100 GB.

---

### Post by warfacegod on 2010-01-25
> I am a bit reticent to remove a package if it is required, but if continues to proceed like this I might have to. So, is something "lying" to me?

It isn't a required package per se. It is only required to boot *faster.*

---

### Post by blueridgedog on 2010-01-25
> **warfacegod said:**
> We've already discussed that possibility and 5% doesn't even come close to accounting for 100 GB.

True, but my point is that debugfs isn't the issue.

---

### Post by warfacegod on 2010-01-25
> **blueridgedog said:**
> True, but my point is that debugfs isn't the issue.

Then I would be interested to know what you think the issue is because mine is showing 80% total use. Not as much as madmonkeyz' but still certainly allot.

---

### Post by madmonkeyz on 2010-01-25
If it is "safe" to remove the aforementioned packages, then I will. I am curious to see if it is something more insipid - as it seems some related system function (optimization) has gone awry. Thank you both for looking into this!

---

### Post by warfacegod on 2010-01-25
> **madmonkeyz said:**
> If it is "safe" to remove the aforementioned packages, then I will. I am curious to see if it is something more insipid - as it seems some related system function (optimization) has gone awry. Thank you both for looking into this!

sreahahead is safe to remove. I states in its description that it is only transitional package for switching to ureadahead and that it can be removed safely.

Hold off on ureadahead for the moment. It ought to be safe to remove but blueridgedog seems to think that your getting a "false positive" on it being the culprit. I'm not convinced but there is no harm in being sure that he's right and I'm wrong or vice versa.

---

### Post by mcduck on 2010-01-25
> **warfacegod said:**
> sreahahead is safe to remove. I states in its description that it is only transitional package for switching to ureadahead and that it can be removed safely.

Hold off on ureadahead for the moment. It ought to be safe to remove but blueridgedog seems to think that your getting a "false positive" on it being the culprit. I'm not convinced but there is no harm in being sure that he's right and I'm wrong or vice versa.

blueridgedog is correct, it's just a virtual fileystem that doesn't even exist on the hard drive. It definitely can't use any of the drive space.

Same applies to the other filesystems that have filesystem "none" in the df output. None of those actually exists on your hard drive, they are created in RAM when the system is booted.

The debugfs shouldn't really even appear in the df output, but that's just a harmless bug that's already been reported in launchpad. You can ignore it.

---

### Post by madmonkeyz on 2010-01-25
Interesting theory, and I can't authoritatively comment on the validity of that statement one-way or the other. I am FAIRLY certain that I don't have 101 GB of RAM though. That being the case, is this machine heading for trouble? It concerns me...

---

### Post by mcduck on 2010-01-25
> **madmonkeyz said:**
> Interesting theory, and I can't authoritatively comment on the validity of that statement one-way or the other. I am FAIRLY certain that I don't have 101 GB of RAM though. That being the case, is this machine heading for trouble? It concerns me...

Like I said, it's a virtual filesystem, and doesn't really exist (in the sense that the real filesystems located in your hard drves do), and definitely not with actual size of 101GB.

Like I said, it's not even supposed to appear in the df output, df doesn't give correct size for it because there isn't one. 
```

udev 1007M 320K 1007M 1% /dev
none 1007M 412K 1007M 1% /dev/shm
none 1007M 204K 1007M 1% /var/run
none 1007M 0 1007M 0% /var/lock
none 1007M 0 1007M 0% /lib/init/rw
none 110G 101G 3.7G 97% /var/lib/ureadahead/debugfs
```

None of these exists on your hard drive, they are all virtual filesystems of their own and calculating real sizes for them is somewhere between pointless and impossible.

Just like you don't have a 101GB debugfs in your hard drive or RAM, you don't have any of the other seven virtual file systems that report their size as over a gigabyte each.

---

### Post by warfacegod on 2010-01-25
Could this be a corrupted partition table then?

---

### Post by madmonkeyz on 2010-01-25
So when disk usage analyzer says that 101 GB is used and 97% of the file system is full, I don't have to worry - as it's all virtual? I find it difficult to comprehend that I can't seem to find a utility that tells me how much disk space is actually being consumed.

---

### Post by mcduck on 2010-01-25
> **madmonkeyz said:**
> So when disk usage analyzer says that 101 GB is used and 97% of the file system is full, I don't have to worry - as it's all virtual? I find it difficult to comprehend that I can't seem to find a utility that tells me how much disk space is actually being consumed.

No, if it says that you have 97% of used space on that filesystem you of course either do have 97% of used space there, or then there's something wrong and you shoudld fix it.

What I was saying that other filesystems (even less the virtual ones!) have nothing to do with that.

Let's assume that you have one hard drive thats 90% full. If you then have another hard drive that's 50% full it has nothing to do with the first drive. It doesn't increase the available space in your first hard drive, and it doesn't use any available space on the fist hard drive either. Free (or used) space on one filesystem doesn't affect the available space on other file systems.

Each line if the df output is a completely different filesystem, separate from the others. Some of them are actual physical filesystems that exist on your hard drives, others are virtual filesystems that only really exist in RAM (even though Linux will show them as files inside the directory structure, because everyhting is a file in Linux).

---

### Post by madmonkeyz on 2010-01-25
I want to first off thank everyone for taking time out to try and explain this to me. My first initial conclusion, that Ubuntu was somehow mixing the drive space used (across multiple drives) and calculating a percentage of available (from the main drive) has long since sailed.

So far, I have nothing really tangible to go on. If I select my root drive (and go to properties - I see about 58.2 GB used). Home folder is approx. 3.8 GB. 

When I used the disk usage analyzer it shows 97% used, df from the command-line the same (albiet, with varying results).

What would I have to do to a)verify the actual space being used and is available? b)clean-up where appropriate? c)See where the largest folder culprits are?

Thanks in advance.

---

### Post by warfacegod on 2010-01-25
Try using:

```
df -a
```

---

### Post by madmonkeyz on 2010-01-25
Well, here are the results; even worse that I could have imagined.

andrew@xanadu:/$ df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/xanadu-root
                     114536088 107695204   1068596 100% /
proc                         0         0         0   -  /proc
none                         0         0         0   -  /sys
none                         0         0         0   -  /sys/fs/fuse/connections
none                         0         0         0   -  /sys/kernel/debug
none                         0         0         0   -  /sys/kernel/security
udev                   1030572       320   1030252   1% /dev
none                         0         0         0   -  /dev/pts
none                   1030572       904   1029668   1% /dev/shm
none                   1030572       204   1030368   1% /var/run
none                   1030572         0   1030572   0% /var/lock
none                   1030572         0   1030572   0% /lib/init/rw
**[B][COLOR="Red"]none                 114536088 107695204   1068596 100% /var/lib/ureadahead/debugfs[/COLOR]**[/B]
/dev/sda1               241116     63114    165554  28% /boot
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon             0         0         0   -  /home/andrew/.gvfs
/dev/sdb1            117189600  47951488  69238112  41% /media/WD Passport__

I'm truly at a loss as to how to proceed as it's not entirely clear what I can do from here.

---

### Post by madmonkeyz on 2010-01-25
Went to remove sreadahead via Synaptic and got prompted with the following dialog.

Needless to say, I opted against it.

Any other ideas? Anyone? Bueller...?

---

### Post by ibuclaw on 2010-01-25
> **madmonkeyz said:**
> Well, here are the results; even worse that I could have imagined.

andrew@xanadu:/$ df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
**[B][COLOR="Red"]none                 114536088 107695204   1068596 100% /var/lib/ureadahead/debugfs[/COLOR]**[/B]

I'm truly at a loss as to how to proceed as it's not entirely clear what I can do from here.

How is the filesystem mounted?

```
mount
```
Regards
Iain

---

### Post by madmonkeyz on 2010-01-25
andrew@xanadu:/$ mount
/dev/mapper/xanadu-root on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
/dev/sda1 on /boot type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andrew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrew)
/dev/sdb1 on /media/WD Passport__ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

---

### Post by ibuclaw on 2010-01-25
> **madmonkeyz said:**
> Went to remove sreadahead via Synaptic and got prompted with the following dialog.

Needless to say, I opted against it.

Any other ideas? Anyone? Bueller...?

Sorry, what on earth are you doing?

```

[$] sudo du -h /var/lib/ureadahead
0        /var/lib/ureadahead/debugfs
0        /var/lib/ureadahead/
[$]

```

That directory is empty? So is a non-issue...

I'm no good at reading du myself, but what is outputted when you do the more human-readable:
```
sudo du -hx --max-depth=1 /
```

Regards
Iain

---

### Post by madmonkeyz on 2010-01-25
> sreahahead is safe to remove. I states in its description that it is only transitional package for switching to ureadahead and that it can be removed safely.

Only trying to figure out why my HD is reporting that it is at 100%.

---

### Post by madmonkeyz on 2010-01-25
Results:

andrew@xanadu:/$ sudo du -hx --max-depth=1 /
[sudo] password for andrew: 
4.0K	/.pulse
3.1G	/var
4.8G	/usr
4.0K	/selinux
8.8M	/sbin
391M	/lib
16K	/lost+found
205M	/opt
4.0K	/mnt
5.4M	/bin
0	/proc
88G	/media
du: cannot access `/home/andrew/.gvfs': Permission denied
7.0G	/home
5.0K	/boot
0	/sys
200K	/srv
4.0K	/initrd
0	/dev
17M	/root
128K	/tmp
23M	/etc
103G	/


Thanks for your time - didn't see your post in its entirely before.

---

### Post by blueridgedog on 2010-01-25
> **madmonkeyz said:**
> The results:
```
andrew@xanadu:/$ sudo du --max-depth=1 | sort -g
16892	./root
23044	./etc
56951	./boot
208944	./opt
399536	./lib
423296	./var
4974496	./usr
7297432	./home
91371064	./media
104787267	.
```


This is similar to what you posted originally:
```

 114536088 104995108 3768692 97% /
```

I would conclude that it is accurate (allowing for a 5% root reserve).

---

### Post by ibuclaw on 2010-01-25
> **madmonkeyz said:**
> Results:

andrew@xanadu:/$ sudo du -hx --max-depth=1 /
<snip>
[COLOR="Red"]88G	/media[/COLOR]
</snip>

Thanks for your time - didn't see your post in its entirely before.

That is the bad egg...

```
sudo du -hx --max-depth=1 /media
```

Regards
Iain

---

### Post by madmonkeyz on 2010-01-25
andrew@xanadu:/$ sudo du -hx --max-depth=1 /media
[sudo] password for andrew: 
4.0K	/media/cdrom0
73G	/media/WD Passport
32K	/media/WD Passport__
15G	/media/WD Passport_
4.0K	/media/floppy0
88G	/media

What do I need to do?

---

### Post by ibuclaw on 2010-01-25
> **madmonkeyz said:**
> andrew@xanadu:/$ sudo du -hx --max-depth=1 /media
[sudo] password for andrew: 
4.0K	/media/cdrom0
73G	/media/WD Passport
32K	/media/WD Passport__
15G	/media/WD Passport_
4.0K	/media/floppy0
88G	/media

What do I need to do?

Well, currently, this is the mountpoint:
```
/dev/sdb1 117189600 47951488 69238112 41% **/media/WD Passport__**
```
/media/WD Passport with 2 underscores after it.

Where the other two came from is a mystery, but they aren't mountpoints, so what is inside them is contributing to the large size of your file system.

Look inside these two folders:
```

/media/WD Passport

/media/WD Passport_

```
And see what can be moved over to /media/WD Passport__

Anything else, remove - or find a place to put it, as it is taking up 73GBs of space.

Regards
Iain

---

### Post by madmonkeyz on 2010-01-25
Ah. makes sense...but I can't actually navigate to either WD Passport or WD Passport_.

I had Simple Backup running for awhile (and ignored it blissfully) and the external drive filled up. My guess is that it "created" those folders. I didn't really need them so I:

```
andrew@xanadu:/media$ sudo rm WD\ Passport -r
andrew@xanadu:/media$ sudo rm WD\ Passport_ -r
```


16% is MUCH better than 97-100%! And is closer to my version of reality; crazy though it may be!

andrew@xanadu:/media$ df -a -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/xanadu-root
                      110G   16G   89G  16% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
udev                 1007M  320K 1007M   1% /dev
none                     0     0     0   -  /dev/pts
none                 1007M  1.2M 1006M   1% /dev/shm
none                 1007M  204K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
none                  110G   16G   89G  16% /var/lib/ureadahead/debugfs
/dev/sda1             236M   62M  162M  28% /boot
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon         0     0     0   -  /home/andrew/.gvfs
/dev/sdb1             112G   46G   67G  41% /media/WD Passport__

Thank you very much Ian! Anytime you find yourself state-side let me know!

---

### Post by madmonkeyz on 2010-01-25
Thanks tinivole (don't know where ian came from?)

---

### Post by audiomick on 2010-01-25
> **madmonkeyz said:**
> Thanks tinivole (don't know where ian came from?)

That's his name, but it is Iain. He signs his posts with it. :D

---

### Post by ibuclaw on 2010-01-25
> **madmonkeyz said:**
> 
Thank you very much Ian! Anytime you find yourself state-side let me know!

No probs, I'll just put your name on a list right next to the Turk who wants to kiss me for fixing his broken partition table. :P

Since you seem happy with the resolution, I'll mark this thread as solved.

Regards
Iain

---

### Post by madmonkeyz on 2010-01-25
Until next time then.

---

