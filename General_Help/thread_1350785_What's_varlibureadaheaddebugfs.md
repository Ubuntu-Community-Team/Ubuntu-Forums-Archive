---
title: "What's /var/lib/ureadahead/debugfs ?"
date: 2009-12-09
forum: General Help
---

### Post by zefew on 2009-12-09
I'm on Karmic and my HDD is formatted in ext4. What's /var/lib/ureadahead/debugfs and why is it there? How do it get rid of it?

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             448G  271G  173G  62% /
udev                  2.0G  300K  2.0G   1% /dev
none                  2.0G  100K  2.0G   1% /dev/shm
none                  2.0G  208K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                  448G  271G  173G  62% /var/lib/ureadahead/debugfs

```

---

### Post by zefew on 2009-12-10
No one knows what it is?

I couldn't find any documentation.

---

### Post by missive@hotmail.com on 2009-12-22
[FONT=Courier New][B]> What's /var/lib/ureadahead/debugfs ?

I started seeing this recently also.

I installed 9.10 fresh in virtualbox and I see it there also.

I asked on IRC #ubuntu and no one else would admit to seeing 
this, but I asked if anyone was using encrypted home folders 
and no one would admit to that either.

My guess is that it is something that is happening because of 
using the encrypted home folders feature.

Are you using encrypted home folders?

One way I was able to get rid of the debugfs entry was:

chmod 0 /sbin/debugfs

The virtual system booted and logged in to my account normally. 
I do not see any problems, but I have not used it extensively like 
that.

Anyone know if that will cause any other problems?

[/B][/FONT]

---

### Post by missive@hotmail.com on 2009-12-22
[FONT=Courier New][B]> chmod 0 /sbin/debugfs

Strangely, this worked in the virtualbox install, but on my
actual install there is still a debugfs entry in the df output.

[/B][/FONT]

---

### Post by cybermatthieu on 2010-01-11
I had the same /var/lib/ureadahead/debugfs listed in df.

I'm running VmWare, and after deleting my only snapshot /var/lib/ureadahead/debugfs disappeared.

Could this really be related to snapshots?

---

### Post by madmonkeyz on 2010-01-24
I have the same problem on an "unvirtual" machine (if thats the word) - its actually at 97%.

---

### Post by jfhopkin on 2010-02-06
I'm seeing it too, no VMware, no encryption - it's not far off being an out-of-the-box installation.

df:
```
none                  142G   18G  117G  14% /var/lib/ureadahead/debugfs
```

mount:
```
none on /var/lib/ureadahead/debugfs type debugfs (rw)
```

Now if all that space were *real* ...!

---

### Post by packs on 2010-02-12
i can see the same /var/lib/ureadahead/debugfs on my ubuntu 9.10 server box
no encryptions,fresh install.

/dev/sda3              21G  1.9G   18G  10% /
udev                 1006M  200K 1006M   1% /dev
none                 1006M     0 1006M   0% /dev/shm
none                 1006M  296K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
none                   21G  1.9G   18G  10% /var/lib/ureadahead/debugfs
/dev/sda1             204G   70G  124G  36% /home

---

### Post by AncientPC on 2010-03-09
FWIW, I see it to and it's mimic'ing my / partition.  I've upgraded this laptop from 8.04 -> 8.10 -> 9.04 -> 9.10.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.6G  5.9G  3.7G  62% /
udev                  1.5G  256K  1.5G   1% /dev
none                  1.5G  844K  1.5G   1% /dev/shm
none                  1.5G  368K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
none                  9.6G  5.9G  3.7G  62% /var/lib/ureadahead/debugfs
/dev/sda3              64G   42G   22G  66% /home


/dev/sda1 on / type jfs (rw,relatime,errors=remount-ro)
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
/dev/sda3 on /home type jfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/xxxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxx)

```

---

### Post by NHclimber on 2010-03-21
The kernel filesystem tracers that ureadahead uses to 'profile' the boot process are expected to be at the debugfs mountpoint, /sys/kernel/debug. If a quick test reveals that the mountpoint isn't up yet, rather than wait for the mountpoint (and potentially missing more profiling it could do), ureadahead mounts a temporary debugfs at /var/lib/ureadhead/debugfs so that it can get to the filesystem tracers (do_sys_open, open_exec & uselib syscalls).

According to the dev in this bug report ([https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/499773](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/499773)), a left-over temporary mountpoint indicates that ureadahead crashed out, leaving the mountpoint in /etc/mtab. A quick scan of the source seems to confirm this, but maybe something was overlooked.

Can you confirm if the mountpont is stale ('cat /proc/self/mountinfo')?

---

### Post by dannyboy79 on 2010-03-28
how do we confirm if the mount point is stale? I ran the cat command and this is what it returned.
df -h: [http://pastebin.com/2M8irKCh](http://pastebin.com/2M8irKCh)
mountinfo: [http://pastebin.com/8vWx7DVk](http://pastebin.com/8vWx7DVk)

is it really even using any space? it looks like it has the same info as my / partition. 22g total, 11g used, 9.4g avail.

---

### Post by mark0978 on 2010-04-02
Here is what I am getting, and yes, it seems to be mirroring /

```
mark@render:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            138321868  89303892  41991552  69% /
udev                   2016080       256   2015824   1% /dev
none                   2016080         0   2016080   0% /dev/shm
none                   2016080       592   2015488   1% /var/run
none                   2016080         0   2016080   0% /var/lock
none                   2016080         0   2016080   0% /lib/init/rw
none                 138321868  89303904  41991540  69% /var/lib/ureadahead/debugfs
/dev/sdb1            732549604 329335260 403214344  45% /backup
/dev/sdc1            244076732 123009564 121067168  51% /audio


mark@render:~$ cat /proc/self/mountinfo
14 17 0:0 / /sys rw,nosuid,nodev,noexec,relatime - sysfs none rw
15 17 0:3 / /proc rw,nosuid,nodev,noexec,relatime - proc none rw
16 17 0:14 / /dev rw,relatime - tmpfs udev rw,mode=755
17 1 8:1 / / rw,relatime - ext3 /dev/disk/by-uuid/450a759c-f5c2-4239-9bd0-b04976666696 rw,errors=remount-ro,data=writeback
18 14 0:8 / /sys/kernel/security rw,relatime - securityfs none rw
20 14 0:15 / /sys/fs/fuse/connections rw,relatime - fusectl none rw
21 14 0:5 / /sys/kernel/debug rw,relatime - debugfs none rw
22 16 0:11 / /dev/pts rw,nosuid,noexec,relatime - devpts none rw,gid=5,mode=620,ptmxmode=000
23 16 0:16 / /dev/shm rw,nosuid,nodev,relatime - tmpfs none rw
24 17 0:17 / /var/run rw,nosuid,relatime - tmpfs none rw,mode=755
25 17 0:18 / /var/lock rw,nosuid,nodev,noexec,relatime - tmpfs none rw
26 17 0:19 / /lib/init/rw rw,nosuid,relatime - tmpfs none rw,mode=755
27 17 8:17 / /backup rw,relatime - reiserfs /dev/sdb1 rw
28 17 8:33 / /audio rw,relatime - xfs /dev/sdc1 rw,noquota
29 15 0:20 / /proc/fs/nfsd rw,relatime - nfsd nfsd rw
30 15 0:21 / /proc/sys/fs/binfmt_misc rw,nosuid,nodev,noexec,relatime - binfmt_misc binfmt_misc rw

```

---

### Post by pichel.vercors on 2010-04-05
Hello,  I'm experiencing the same problem with Ext4 and ubuntu 9.10, except I discovered it while tracking another problem : a sa called full root partition, which is as big as 20G whereas I use only 6 Gb (my home is on a separate one). df reports / as being nearly as full, where du -sxc confirms me that only 6 Gb are used.  I've looked at mount info, and the relevant line is :  22 15 0:5 / /sys/kernel/debug rw,relatime - debugfs none rw  Does it sounds to you ?  Michel

---

### Post by NHclimber on 2010-08-17
> **dannyboy79 said:**
> how do we confirm if the mount point is stale?

/proc/self/mountinfo is current.  df returns what's in /etc/mtab which can be old (stale).

---

### Post by nealmcb on 2011-04-03
You can learn more and track the status of the bug at [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773)

---

