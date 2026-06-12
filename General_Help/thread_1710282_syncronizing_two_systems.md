---
title: "syncronizing two systems"
date: 2011-03-19
forum: General Help
---

### Post by Jonker on 2011-03-19
Hello,
  I wanted to know, I it is possible to synchronize two systems. I’ve got one System on an ext. hard- drive, and one on a desktop computer. 



  An example for better understanding:
  If I update on the ext. HD and I connect the ext. HD to the desktop, the desktop should be updated to. Or, when I create a new user on the desktop, and I connect the ext. hd, the user should get created to.
  Is this possible???

---

### Post by Jonker on 2011-03-20
Ok, what do you think of this way?

/dev/sdb is my internal one and /dev/sdc is my external one.

First I want to make sure, that both have the exact same information on them. So I think this should work.

```
sudo dd if=/dev/sdc1 of=/dev/sdb1
```This code will copy the content of the first partition of the ext. HD (its newer) to the internal one. Is this correct?

Then for updating you could use a 'cp' or a 'rsync' command, but I'm not quite sure how these work. Because I don't wan't to copy each time the whole partition, I would appreciate an 'update' funktion ( maby there is a parameter for the commands?).

---

### Post by Jonker on 2011-03-20
why can nobody help me? Is this to exotic?

---

### Post by blueridgedog on 2011-03-20
Rsync would work, but it would not create the changes to the boot sector and grub.

If sdc1 (master) is mounted as / and sdb1 (slave or secondary) was mounted at /mnt/sdb1, then you could synchronize them with:

```
rsync -v / /mnt/sdb1 --delete
```

However, I am not certain how it would handle virtual file systems (/proc, /sys and /dev)

Look at 

```
man rsync
```

for more details.

After doing this, you may have to boot on sdb1 and setup grub.

---

### Post by Jonker on 2011-03-21
I was trying to copy the sdc to the sdb. But it couldn't finish, because it created a file called full in /dev. So I wonderd what would happen, if I just leave the virtual file systems away?

---

### Post by blueridgedog on 2011-03-21
I would use an exclude statement for the virtual file systems if using rsync.

---

### Post by Jonker on 2011-03-22
ok, so lets say, that I'm running Ubuntu on the internal one /dev/sdb. Now I connect the external one (/dev/sdc). When I have connected, I would like to update the internal one, so that it has the same stuff again, like the external one. Could you please post the code here, or (maby even better) write a script and upload it.

Thanks in advance!!!:)

---

### Post by blueridgedog on 2011-03-22
What partitions are in play on each drive and do you mount the partitions on the external drive in a particular way?

---

### Post by Jonker on 2011-03-23
> **blueridgedog said:**
> ...and do you mount the partitions on the external drive in a particular way?

What do you mean with that?

---

### Post by blueridgedog on 2011-03-23
rsync can synchronize partitions, not drives.  So to write an rsync command for you I/we need to know what partitions are on sdc and sdb.

You can get them with:

```
sudo fdisk -l 
```

While the drive is connected.

---

### Post by Jonker on 2011-03-28
Sorry, but I made a mistake and Ubuntu isn't working at the moment. I'll make a new installation, but this might take a week ( I am very busy at the moment).:(

PS: Do the partitions have to be the same size on both devices (when I reinstall it, then I can easily format it)?

---

### Post by Jonker on 2011-03-29
ok,

I reinstalled it. heres the result:
```
sudo fdisk -l
 [FONT=&quot]Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d470

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux
/dev/sdb2            4864        9221    35000000   83  Linux
/dev/sdb3            9221        9730     4087809    5  Extended
/dev/sdb5            9221        9730     4087808   82  Linux swap / Solaris

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021cf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       13984   112323584   83  Linux
/dev/sdc2           19206       20024     6567937    5  Extended
[/FONT][FONT=&quot]/dev/sdc3           13984       19206    41942016   83  Linux
/dev/sdc5           19206       20024     6567936   82  Linux swap / Solaris
 [/FONT]
  

```


PS: I have taken out sda. I hope this helps you.

---

### Post by blueridgedog on 2011-03-31
> **Jonker said:**
> I was trying to copy the sdc to the sdb.

dd will copy disk to disk, duplicating partitions.  Rsync can synchronize partitions/files/directories.



> **Jonker said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux
/dev/sdb2            4864        9221    35000000   83  Linux
/dev/sdb3            9221        9730     4087809    5  Extended
/dev/sdb5            9221        9730     4087808   82  Linux swap / Solaris


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       13984   112323584   83  Linux
/dev/sdc2           19206       20024     6567937    5  Extended
[/FONT][FONT=&quot]/dev/sdc3           13984       19206    41942016   83  Linux
/dev/sdc5           19206       20024     6567936   82  Linux swap / Solaris
 [/FONT]
  
[/CODE]


You have one main Linux partition on sdc, that is sdc1.  But, you have two main partitions on sdb, sdb1 and sdb2.

So, do you want to copy sdb1 to sdc1 or sdb2 to sdc1?

You can see how the partitions are currently used/mounted with the command:

```
mount
```

If that helps you determine which partitions are being used for what.

---

### Post by Jonker on 2011-04-02
Ok, so let's get this right:

I have repartitioned the drives, so here is the new sudo fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2be42be3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12277    98614971    7  HPFS/NTFS
/dev/sda2           12278       19457    57673350    f  W95 Ext'd (LBA)
/dev/sda5           12278       19457    57673318+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d470

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux
/dev/sdb2            4864        9221    35000000   83  Linux
/dev/sdb3            9221        9730     4087809    5  Extended
/dev/sdb5            9221        9730     4087808   82  Linux swap / Solaris

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005d6f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4980    39999488   83  Linux
/dev/sdc2            4980       20024   120834049    5  Extended
/dev/sdc5            4980        9338    34999296   83  Linux
/dev/sdc6            9338        9823     3898368   82  Linux swap / Solaris
/dev/sdc7            9823       18961    73400320    b  W95 FAT32
/dev/sdc8           18961       20024     8532992   83  Linux 
```Now, how have I got my system set up? 

Well I have on both HDD(sdb, sdc) a main system parition ( /sdb1 and /sdc1). Those are the partitions which are mounted at "/" and which I want to syncronise.
 
Then I have two times a partition (/sdb2 and /sdc5) which are mounted at "/home", I don't wan't to syncronise those, because I have different users on each system.

Finally I've got a swap space on each drive.

On /dev/sdc I've got in addition a backuppartition (/sdc8) and a partition for Windows acces (/sdc7 formated in Fat32).

On /dev/sda I've got Windows XP installed.

I hope you've got all you information now...

---

### Post by Jonker on 2011-04-04
> So, do you want to copy sdb1 to sdc1 or sdb2 to sdc1?No, I just want to syncronise those partitions which are mentioned in the post above.

---

### Post by blueridgedog on 2011-04-06
> **Jonker said:**
> Well I have on both HDD(sdb, sdc) a main system parition ( /sdb1 and /sdc1). Those are the partitions which are mounted at "/" and which I want to syncronise.

Rsync uses mounted paths to work from, so let's assume you are booted on sdb1, which would then be / and you have mounted sdc1 as /mnt/sdc1 (you can change it based on where you mounted it.

To go from sdb1 to sdc1 would be:

```
rsync -av / /mnt/sdc1 --delete
```

To go from sdc1 to sdb1, with sdb1 mounted as /mnt/sdb1 and sdc1 being booted off of and mounted as /

```
rsync -av / /mnt/sdb1 --delete
```

However, as I mentioned before, rsync will not update boot records...using it to attempt to syncronize a bootable partition may result in one that is not bootable.  If grub is installed in the master boot record of sdc, and new kernels are copied over to sdc1 via rsync, it may not boot or you may have to update grub.

I recommend ample testing to be certain the results are as you intend. 

dd could also be used, 

```
sudo dd if=/dev/sdb1 of=/dev/sdc1
```

If the boot loader was installed to the master boot record of sdb and sdc, then you may still have the issue of having a boot record that is not in sync with your kernels and initial ram disks on the copied drive.  This may be fixed by updating grub once booted off of the cloned partition.  As with rsync, I recommend testing it in a controlled environment before relying on it.

A final word of caution:  dd and rsync will do as you tell them, up to and including wiping important data.  If you get the target and destination confused, it will erase your data.

---

### Post by Jonker on 2011-04-07
Ok, I just want to doubble check the command.

First, I have booted of sdb (this is mounted at "/"). The folders at "/" are:
```
[FONT=&quot]bin[/FONT]  
[FONT=&quot]boot[/FONT]
[FONT=&quot]cdrom[/FONT]
[FONT=&quot]dev[/FONT]
[FONT=&quot]etc[/FONT]
[FONT=&quot]external[/FONT]
[FONT=&quot]home[/FONT]
[FONT=&quot]initrd.img[/FONT]
[FONT=&quot]lib[/FONT]
[FONT=&quot]lost+found[/FONT]
[FONT=&quot]media[/FONT]
[FONT=&quot]mnt[/FONT]
[FONT=&quot]opt[/FONT]
[FONT=&quot]proc[/FONT]
[FONT=&quot]root[/FONT]
[FONT=&quot]sbin[/FONT]
[FONT=&quot]selinux[/FONT]
[FONT=&quot]srv[/FONT]
[FONT=&quot]sys[/FONT]
[FONT=&quot]tmp[/FONT]
[FONT=&quot]usr[/FONT]
[FONT=&quot]var[/FONT]
[FONT=&quot]vmlinuz
[/FONT]
```The external HDD is mounted at "/external". The folders at "/external" are:
```
  [FONT=&quot]backup[/FONT]
  [FONT=&quot]cdrom[/FONT]
  [FONT=&quot]home[/FONT]
  [FONT=&quot]home_backup[/FONT]
    [FONT=&quot]media[/FONT]
  [FONT=&quot]proc[/FONT]
  [FONT=&quot]selinux[/FONT]
  [FONT=&quot]tmep[/FONT]
  [FONT=&quot]vmlinuz[/FONT]
  [FONT=&quot]bin[/FONT]
  [FONT=&quot]dev[/FONT]
  [FONT=&quot]lib[/FONT]
  [FONT=&quot]mnt[/FONT]
  [FONT=&quot]root[/FONT]
  [FONT=&quot]srv[/FONT]
  [FONT=&quot]usr[/FONT]
  [FONT=&quot]windows[/FONT]
  [FONT=&quot]boot[/FONT]
  [FONT=&quot]etc[/FONT]
  [FONT=&quot]intrd.img[/FONT]
  [FONT=&quot]lost+found[/FONT]
  [FONT=&quot]opt[/FONT]
  [FONT=&quot]sbin[/FONT]
  [FONT=&quot]sys[/FONT]
  [FONT=&quot]var
[/FONT]
  
```So I don't wan't to syncronise all these foldes, because some don't exist, or are not neccesary. I have a file called exclude.txt on my desktop, in which these folders (which are mounted at /external so they are on sdc) are listed:

exclude.txt```
[FONT=&quot]backup
cdrom
dev
home_backup
home
media
mnt
proc
root
windows
tmp
sys
[/FONT]
```Is this correct, or do the folders need to be like "/external/backup"?
So the command is:```
rsync -av / /external --delete --exclude-from '/sncronising.txt'--progress
```And after that, I'll run a ```
sudo update-grub
```Is this correct?

Thank you for helping me!!!!:)

---

### Post by blueridgedog on 2011-04-07
You will also need /external in your exclude list.

From the rsync man page:


 --exclude-from=FILE
This option is related to the --exclude option, but it specifies
a FILE that contains exclude patterns  (one  per  line).   Blank
lines  in  the  file  and  lines  starting  with  ’;’ or ’#’ are
ignored.  If FILE is -, the list  will  be  read  from  standard
input.

So your syntax should probably be:

```
rsync -av / /external --delete --exclude-from=/sncronising.txt --progress
```

I would test it significantly with "-n" for dry run.

---

### Post by Jonker on 2011-04-07
thanks, but do I need the full path of the folders which I want to exclude, or is "home"enough?

---

### Post by blueridgedog on 2011-04-07
The exclude is a bit tricky, as it wants a pattern, not a directory listing, so you will have to experiment.


```
       --exclude=PATTERN
              This option is a simplified form of  the  --filter  option  that
              defaults  to  an  exclude rule and does not allow the full rule-
              parsing syntax of normal filter rules.

              See the FILTER RULES section for detailed  information  on  this
              option.
```

If you look at the rsync man page and then go to the "include exclude pattern rules" section, you see:

```
/foo"  would  exclude a file (or directory) named foo in the
              transfer-root directory

```

So, I would use absolute paths in your exclude file, starting with / and test with the -n option until you are satisfied that it works as expected.

---

### Post by Jonker on 2011-04-07
OK, I'll try it and post the result here, this may take one/two days...

---

### Post by Jonker on 2011-04-08
So, I made a dry run, but I didn't do the sync. yet. I saved the output in a .txt file (Linux Line Endings). I don't think, that this is correct. I've cut it, because It would have  been nearly 9 MB big...
beginning:
```
  [FONT=&quot]sending incremental file list
./
deleting windows/
deleting home_backup/jonathan/Videos/
deleting home_backup/jonathan/Templates/
deleting home_backup/jonathan/Public/
deleting home_backup/jonathan/Pictures/
deleting home_backup/jonathan/Music/iTunes/iTunes Media/Automatisch zu iTunes hinzufügen/
deleting home_backup/jonathan/Music/iTunes/iTunes Media/.iTunes Preferences.plist
deleting home_backup/jonathan/Music/iTunes/iTunes Media/
deleting home_backup/jonathan/Music/iTunes/Album Artwork/Download/
deleting home_backup/jonathan/Music/iTunes/Album Artwork/Cache/
deleting home_backup/jonathan/Music/iTunes/Album Artwork/
deleting home_backup/jonathan/Music/iTunes/sentinel
deleting home_backup/jonathan/Music/iTunes/iTunes Music Library.xml
deleting home_backup/jonathan/Music/iTunes/iTunes Library.itl
deleting home_backup/jonathan/Music/iTunes/iTunes Library Genius.itdb
deleting home_backup/jonathan/Music/iTunes/iTunes Library Extras.itdb
deleting home_backup/jonathan/Music/iTunes/
deleting home_backup/jonathan/Music/
deleting home_backup/jonathan/Downloads/unetbootin-windows-502.exe
deleting home_backup/jonathan/Downloads/ubuntu-wallpaper2.jpg
deleting home_backup/jonathan/Downloads/sp42741.exe
deleting home_backup/jonathan/Downloads/maverick.sources.list
deleting home_backup/jonathan/Downloads/iTunesSetup.exe
deleting home_backup/jonathan/Downloads/faenza_icons_by_tiheum-d2v6x24.zip
[/FONT]
  

```the a litle later```
proc/1014/task/1015/mounts
proc/1014/task/1015/oom_adj
proc/1014/task/1015/oom_score
proc/1014/task/1015/pagemap
proc/1014/task/1015/personality
proc/1014/task/1015/root -> /proc
proc/1014/task/1015/sched
proc/1014/task/1015/schedstat
proc/1014/task/1015/sessionid
proc/1014/task/1015/smaps
proc/1014/task/1015/stack
proc/1014/task/1015/stat
proc/1014/task/1015/statm
proc/1014/task/1015/status
proc/1014/task/1015/syscall
proc/1014/task/1015/wchan
proc/1014/task/1015/attr/
proc/1014/task/1015/attr/current
proc/1014/task/1015/attr/exec
proc/1014/task/1015/attr/fscreate
proc/1014/task/1015/attr/keycreate
proc/1014/task/1015/attr/prev
proc/1014/task/1015/attr/sockcreate
proc/1014/task/1015/fd/
proc/1014/task/1015/fd/0 -> /dev/null
proc/1014/task/1015/fd/1 -> /dev/null
proc/1014/task/1015/fd/2 -> /dev/null
proc/1014/task/1015/fd/3 -> socket:[5588]
proc/1014/task/1015/fd/4 -> /dev/null
proc/1014/task/1015/fd/5 -> socket:[5589]
proc/1014/task/1015/fd/6 -> anon_inode:[eventfd]
proc/1014/task/1015/fd/7 -> anon_inode:[eventfd]
proc/1014/task/1015/fdinfo/
proc/1014/task/1015/fdinfo/0
proc/1014/task/1015/fdinfo/1
proc/1014/task/1015/fdinfo/2
proc/1014/task/1015/fdinfo/3
proc/1014/task/1015/fdinfo/4
proc/1014/task/1015/fdinfo/5
proc/1014/task/1015/fdinfo/6
proc/1014/task/1015/fdinfo/7
proc/1014/task/1016/
proc/1014/task/1016/auxv
proc/1014/task/1016/cgroup
proc/1014/task/1016/clear_refs
proc/1014/task/1016/cmdline
proc/1014/task/1016/cpuset
proc/1014/task/1016/cwd -> /proc
proc/1014/task/1016/environ
proc/1014/task/1016/exe -> /usr/lib/rtkit/rtkit-daemon
proc/1014/task/1016/io
proc/1014/task/1016/latency
proc/1014/task/1016/limits
proc/1014/task/1016/loginuid
proc/1014/task/1016/maps
proc/1014/task/1016/mem
proc/1014/task/1016/mountinfo
proc/1014/task/1016/mounts
proc/1014/task/1016/oom_adj
proc/1014/task/1016/oom_score
proc/1014/task/1016/pagemap
proc/1014/task/1016/personality
proc/1014/task/1016/root -> /proc
proc/1014/task/1016/sched
proc/1014/task/1016/schedstat
proc/1014/task/1016/sessionid
proc/1014/task/1016/smaps
proc/1014/task/1016/stack
proc/1014/task/1016/stat
proc/1014/task/1016/statm
proc/1014/task/1016/status
proc/1014/task/1016/syscall
proc/1014/task/1016/wchan
proc/1014/task/1016/attr/
proc/1014/task/1016/attr/current
proc/1014/task/1016/attr/exec
proc/1014/task/1016/attr/fscreate
proc/1014/task/1016/attr/keycreate
proc/1014/task/1016/attr/prev
proc/1014/task/1016/attr/sockcreate
proc/1014/task/1016/fd/
proc/1014/task/1016/fd/0 -> /dev/null
proc/1014/task/1016/fd/1 -> /dev/null
proc/1014/task/1016/fd/2 -> /dev/null
proc/1014/task/1016/fd/3 -> socket:[5588]
proc/1014/task/1016/fd/4 -> /dev/null
proc/1014/task/1016/fd/5 -> socket:[5589]
proc/1014/task/1016/fd/6 -> anon_inode:[eventfd]
proc/1014/task/1016/fd/7 -> anon_inode:[eventfd]
proc/1014/task/1016/fdinfo/
proc/1014/task/1016/fdinfo/0
proc/1014/task/1016/fdinfo/1
proc/1014/task/1016/fdinfo/2
proc/1014/task/1016/fdinfo/3
proc/1014/task/1016/fdinfo/4
proc/1014/task/1016/fdinfo/5
proc/1014/task/1016/fdinfo/6
proc/1014/task/1016/fdinfo/7
proc/1018/
proc/1018/auxv
proc/1018/cgroup
proc/1018/clear_refs
proc/1018/cmdline
proc/1018/coredump_filter
proc/1018/cpuset
proc/1018/cwd -> /
proc/1018/environ
proc/1018/exe -> /usr/lib/policykit-1/polkitd
proc/1018/io
proc/1018/latency
proc/1018/limits
proc/1018/loginuid
proc/1018/maps
proc/1018/mem
proc/1018/mountinfo
proc/1018/mounts
proc/1018/mountstats
proc/1018/oom_adj
proc/1018/oom_score
proc/1018/pagemap
proc/1018/personality
proc/1018/root -> /
proc/1018/sched
proc/1018/schedstat
proc/1018/sessionid
proc/1018/smaps
proc/1018/stack
proc/1018/stat
proc/1018/statm
proc/1018/status
proc/1018/syscall
proc/1018/wchan
proc/1018/attr/
proc/1018/attr/current
proc/1018/attr/exec
proc/1018/attr/fscreate
proc/1018/attr/keycreate
proc/1018/attr/prev
proc/1018/attr/sockcreate
proc/1018/fd/
proc/1018/fd/0 -> /dev/null
proc/1018/fd/1 -> /dev/null
proc/1018/fd/2 -> /dev/null
proc/1018/fd/3 -> pipe:[5607]
proc/1018/fd/4 -> /dev/null
proc/1018/fd/5 -> pipe:[5607]
proc/1018/fd/6 -> socket:[5610]
proc/1018/fd/7 -> inotify
proc/1018/fd/8 -> socket:[7562]
proc/1018/fdinfo/
proc/1018/fdinfo/0
proc/1018/fdinfo/1
proc/1018/fdinfo/2
proc/1018/fdinfo/3
proc/1018/fdinfo/4
proc/1018/fdinfo/5
proc/1018/fdinfo/6
proc/1018/fdinfo/7
proc/1018/fdinfo/8
proc/1018/net/
proc/1018/net/anycast6
proc/1018/net/arp
proc/1018/net/connector
proc/1018/net/dev
proc/1018/net/dev_mcast
proc/1018/net/if_inet6
proc/1018/net/igmp
proc/1018/net/igmp6
proc/1018/net/ip6_flowlabel
proc/1018/net/ip_mr_cache
proc/1018/net/ip_mr_vif
proc/1018/net/ipv6_route
proc/1018/net/mcfilter
proc/1018/net/mcfilter6
proc/1018/net/netlink
proc/1018/net/netstat
proc/1018/net/packet
proc/1018/net/protocols
proc/1018/net/psched
proc/1018/net/ptype
proc/1018/net/raw
proc/1018/net/raw6
proc/1018/net/route
proc/1018/net/rt6_stats
proc/1018/net/rt_acct
proc/1018/net/rt_cache
proc/1018/net/snmp
proc/1018/net/snmp6
proc/1018/net/sockstat
proc/1018/net/sockstat6
proc/1018/net/softnet_stat
proc/1018/net/tcp
proc/1018/net/tcp6
proc/1018/net/tr_rif
proc/1018/net/udp
proc/1018/net/udp6
proc/1018/net/udplite
proc/1018/net/udplite6
proc/1018/net/unix
proc/1018/net/wireless
proc/1018/net/dev_snmp6/
proc/1018/net/dev_snmp6/lo
proc/1018/net/netfilter/
proc/1018/net/netfilter/nf_log
proc/1018/net/netfilter/nf_queue
proc/1018/net/stat/
proc/1018/net/stat/arp_cache
proc/1018/net/stat/ndisc_cache

```later...```
sys/module/dell_wmi/sections/.symtab
sys/module/dell_wmi/sections/.text
sys/module/dell_wmi/sections/__mcount_loc
sys/module/drm/
sys/module/drm/initstate
sys/module/drm/refcnt
sys/module/drm/srcversion
sys/module/drm/drivers/
sys/module/drm/drivers/pci:nouveau -> ../../../bus/pci/drivers/nouveau
sys/module/drm/holders/
sys/module/drm/holders/drm_kms_helper -> ../../drm_kms_helper
sys/module/drm/holders/nouveau -> ../../nouveau
sys/module/drm/holders/ttm -> ../../ttm
sys/module/drm/notes/
sys/module/drm/notes/.note.gnu.build-id
sys/module/drm/parameters/
sys/module/drm/parameters/debug
sys/module/drm/sections/
sys/module/drm/sections/.altinstr_replacement
sys/module/drm/sections/.altinstructions
sys/module/drm/sections/.bss
sys/module/drm/sections/.data
sys/module/drm/sections/.exit.text
sys/module/drm/sections/.gnu.linkonce.this_module
sys/module/drm/sections/.init.text
sys/module/drm/sections/.note.gnu.build-id
sys/module/drm/sections/.parainstructions
sys/module/drm/sections/.rodata
sys/module/drm/sections/.rodata.str1.1
sys/module/drm/sections/.rodata.str1.4
sys/module/drm/sections/.smp_locks
sys/module/drm/sections/.strtab
sys/module/drm/sections/.symtab
sys/module/drm/sections/.text
sys/module/drm/sections/__bug_table
sys/module/drm/sections/__kcrctab
sys/module/drm/sections/__kcrctab_gpl
sys/module/drm/sections/__ksymtab
sys/module/drm/sections/__ksymtab_gpl
sys/module/drm/sections/__ksymtab_strings
sys/module/drm/sections/__mcount_loc
sys/module/drm/sections/__param
sys/module/drm_kms_helper/
sys/module/drm_kms_helper/initstate
sys/module/drm_kms_helper/refcnt
sys/module/drm_kms_helper/srcversion
sys/module/drm_kms_helper/holders/
sys/module/drm_kms_helper/holders/nouveau -> ../../nouveau
sys/module/drm_kms_helper/notes/
sys/module/drm_kms_helper/notes/.note.gnu.build-id
sys/module/drm_kms_helper/sections/
sys/module/drm_kms_helper/sections/.altinstr_replacement
sys/module/drm_kms_helper/sections/.altinstructions
sys/module/drm_kms_helper/sections/.data
sys/module/drm_kms_helper/sections/.gnu.linkonce.this_module
sys/module/drm_kms_helper/sections/.note.gnu.build-id
sys/module/drm_kms_helper/sections/.rodata
sys/module/drm_kms_helper/sections/.rodata.str1.1
sys/module/drm_kms_helper/sections/.rodata.str1.4
sys/module/drm_kms_helper/sections/.strtab
sys/module/drm_kms_helper/sections/.symtab
sys/module/drm_kms_helper/sections/.text
sys/module/drm_kms_helper/sections/__bug_table
sys/module/drm_kms_helper/sections/__kcrctab
sys/module/drm_kms_helper/sections/__ksymtab
sys/module/drm_kms_helper/sections/__ksymtab_strings
sys/module/drm_kms_helper/sections/__mcount_loc
sys/module/ehci_hcd/
sys/module/ehci_hcd/drivers/
sys/module/ehci_hcd/drivers/pci:ehci_hcd -> ../../../bus/pci/drivers/ehci_hcd
sys/module/ehci_hcd/parameters/
sys/module/ehci_hcd/parameters/ignore_oc

```and then ```
usr/share/pyshared/twisted/python/zsh/_websetroot
usr/share/pyshared/twisted/scripts/
usr/share/pyshared/twisted/scripts/__init__.py
usr/share/pyshared/twisted/scripts/_twistd_unix.py
usr/share/pyshared/twisted/scripts/_twistw.py
usr/share/pyshared/twisted/scripts/htmlizer.py
usr/share/pyshared/twisted/scripts/manhole.py
usr/share/pyshared/twisted/scripts/mktap.py
usr/share/pyshared/twisted/scripts/tap2deb.py
usr/share/pyshared/twisted/scripts/tap2rpm.py
usr/share/pyshared/twisted/scripts/tapconvert.py
usr/share/pyshared/twisted/scripts/tkunzip.py
usr/share/pyshared/twisted/scripts/trial.py
usr/share/pyshared/twisted/scripts/twistd.py
usr/share/pyshared/twisted/scripts/test/
usr/share/pyshared/twisted/scripts/test/__init__.py
usr/share/pyshared/twisted/scripts/test/test_mktap.py
usr/share/pyshared/twisted/spread/
usr/share/pyshared/twisted/spread/__init__.py
usr/share/pyshared/twisted/spread/banana.py
usr/share/pyshared/twisted/spread/flavors.py
usr/share/pyshared/twisted/spread/interfaces.py
usr/share/pyshared/twisted/spread/jelly.py
usr/share/pyshared/twisted/spread/pb.py
usr/share/pyshared/twisted/spread/publish.py
usr/share/pyshared/twisted/spread/refpath.py
usr/share/pyshared/twisted/spread/util.py
usr/share/pyshared/twisted/spread/ui/
usr/share/pyshared/twisted/spread/ui/__init__.py
usr/share/pyshared/twisted/spread/ui/gtk2util.py
usr/share/pyshared/twisted/spread/ui/login2.glade
usr/share/pyshared/twisted/spread/ui/tktree.py
usr/share/pyshared/twisted/spread/ui/tkutil.py
usr/share/pyshared/twisted/tap/
usr/share/pyshared/twisted/tap/__init__.py
usr/share/pyshared/twisted/tap/ftp.py
usr/share/pyshared/twisted/tap/manhole.py
usr/share/pyshared/twisted/tap/portforward.py
usr/share/pyshared/twisted/tap/socks.py
usr/share/pyshared/twisted/tap/telnet.py
usr/share/pyshared/twisted/test/
usr/share/pyshared/twisted/test/__init__.py
usr/share/pyshared/twisted/test/crash_test_dummy.py
usr/share/pyshared/twisted/test/generator_failure_tests.py
usr/share/pyshared/twisted/test/iosim.py
usr/share/pyshared/twisted/test/mock_win32process.py
usr/share/pyshared/twisted/test/myrebuilder1.py
usr/share/pyshared/twisted/test/myrebuilder2.py
usr/share/pyshared/twisted/test/plugin_basic.py
usr/share/pyshared/twisted/test/plugin_extra1.py
usr/share/pyshared/twisted/test/plugin_extra2.py
usr/share/pyshared/twisted/test/process_cmdline.py
usr/share/pyshared/twisted/test/process_echoer.py
usr/share/pyshared/twisted/test/process_fds.py
usr/share/pyshared/twisted/test/process_linger.py
usr/share/pyshared/twisted/test/process_reader.py
usr/share/pyshared/twisted/test/process_signal.py
usr/share/pyshared/twisted/test/process_stdinreader.py
usr/share/pyshared/twisted/test/process_tester.py
usr/share/pyshared/twisted/test/process_tty.py
usr/share/pyshared/twisted/test/process_twisted.py
usr/share/pyshared/twisted/test/proto_helpers.py
usr/share/pyshared/twisted/test/raiser.c

```the end is:```
  [FONT=&quot]var/spool/openoffice/uno_packages/cache/uno_packages/
var/spool/openoffice/uno_packages/cache/uno_packages/SomnWJ
var/spool/openoffice/uno_packages/cache/uno_packages/SomnWJ_/
var/spool/openoffice/uno_packages/cache/uno_packages/SomnWJ_/mailmerge.py
var/spool/plymouth/
var/tmp/
var/tmp/README.swp

sent 5603046 bytes  received 536180 bytes  132026.37 bytes/sec
total size is 3560279009  speedup is 579.92 (DRY RUN)
[/FONT]
  
```

But you see, the exclude list didn't work :-(, but I used full paths...

So let me know if you know what to do.

Thanks!!!

---

### Post by blueridgedog on 2011-04-08
In the command posted you refer to the exclude file as sncronising.txt, and in the listing you call it exclude.txt.  Are you pointing to the right file?

Based on this:

[http://www.mail-archive.com/rsync@lists.samba.org/msg08777.html](http://www.mail-archive.com/rsync@lists.samba.org/msg08777.html)

You may want the syntax of:

+ /dirtoexclude/

---

### Post by Jonker on 2011-04-08
> In the command posted you refer to the exclude file as sncronising.txt,  and in the listing you call it exclude.txt.  Are you pointing to the  right file?

Ok, I've got the exclude file saved on sdb at /sync/exclude.txt

> You may want the syntax of:

+ /dirtoexclude/ 	

In the exclude file? i.e. when I want to exclude a folder with the path /external/proc, then my exclude entry is:```
+/exernal/proc/
```

Is this right?

---

### Post by blueridgedog on 2011-04-08
I think there is a space after +

---

### Post by Jonker on 2011-04-09
Hello,

I'm not sure if this is working ok... 
Do I need to exclude the /external folder to?
Do I need to exclude the folders on sdb to (link /mnt)

I've updated my exclude file, according to the mail, you posted. here it is:```
### folders to exclude ###
### Virtual file systems ###
+ /external/dev/
- /external/dev/**
+ /external/sys/
- /external/sys/**
+ /external/proc/
- /external/proc/**
### home directories ###
+ /external/home/
- /external/home/**
+ /external/home_backup/
- /external/home_backup/**
+ /external/root/
- /external/root/**
### media and mountpoints ###
+ /external/cdrom/
- /external/cdrom/**
+ /external/media/
- /external/media/**
+ /external/mnt/
- /external/mnt/**
+ /external/windows/
- /external/windows/**
+ /external/backup/
- /external/backup/**
### temp. files ###
+ /external/tmp/
- /external/tmp/**
### folder with exclude file ###
+ /sync/
- /sync/**
### folders on sdb ###
+ /mnt/
- /mnt/**
+ /sys/
- /sys/**
+ /home/
- /home/**
+ /dev/
- /dev/**
+ /cdrom/
- /cdrom/**
+ /tmp/
- /tmp/**
+ /root/
- /root/**
+ /media/
- /media/**
+ /proc/
- /proc/**
+ /sync/
- /sync/**



```is this correct?

PS: on this man page ([http://ss64.com/bash/rsync.html](http://ss64.com/bash/rsync.html)) it says :> Syntax  
# Local file to Local file        rsync [*option*]... *Source* [*Source*]... *Dest*So It would be the other way round???

I hope, that I'm not totally bothersome...

---

### Post by Jonker on 2011-04-10
OK, that was not like planned. 
Good that I made an .iso before I sync. them!
It was the wrong way, and my system on the ext. HDD has crashed... So I'll restore it and try it again.

---

### Post by Jonker on 2011-04-10
I think, that the command should be:
```
sudo rsync -av /external / --exclude-from=/sync/exclude.txt --progress --delete
```

This would sync. the files from /external (mountpoint of sdc) with / (mountpoint of sdb). 
Now I see the reason why you need to exlude the /external folder )==> it would double the data...

Please tell me, if this is wrong!

---

### Post by blueridgedog on 2011-04-10
I think the syntax of your file is still off.  

See this great example:

[http://www.hyperorg.com/blogger/2008/05/10/beginner-to-beginner-rsync-exclude-from/](http://www.hyperorg.com/blogger/2008/05/10/beginner-to-beginner-rsync-exclude-from/)

```
### folders to exclude ###
### Virtual file systems ###
+ /external/dev/
(here you include it, though the comment is to exclude)
- /external/dev/**
+ /external/sys/
(same)
- /external/sys/**
+ /external/proc/
(same)

```

This back and forth continues in your file.

You stated that you thought the command should be:

> sudo rsync -av /external / --exclude-from=/sync/exclude.txt --progress --delete


However, in this post:

[http://ubuntuforums.org/showpost.php?p=10649438&postcount=17](http://ubuntuforums.org/showpost.php?p=10649438&postcount=17)

You indicated that you wanted to syncronize from the internal to the external.  Either way, the syntax of the command is the same, 

```
rsync -av /source /destination
```

If you want to synchronize your booted drive to a drive mounted at external, with your booted drive being the master, with the excludes we have thus far discussed, I would suggest an exclude file similar to:

- mnt/
- backup/
- dev/
- home_backup/
- home/
- external/
- media/
- proc/
- windows/
- tmp/
- sys/

If you want your external drive being the master, then you would want to reverse the order on the rsync command.

I strongly suggest mocking this up (making a test directory on each dist, putting subdirectories in the test directory then excluding certain directories via an exclude file and testing it until it works to your satisfaction).

While searching for syntax help, I can across this great thread:

[http://www.linuxquestions.org/questions/linux-software-2/rsync-include-exclude-problems-636504/](http://www.linuxquestions.org/questions/linux-software-2/rsync-include-exclude-problems-636504/)

---

### Post by Jonker on 2011-04-12
ok, I decidet to do this from a live -cd with sdb mounted at /internal and sdc mounted at /external.

Do I have to exclude both? Here an example:
```
###exclude file###
- /internal/home/
- /internal/home/**
- /external/home/
- /external/home/**
```Or is that to much?

---

### Post by blueridgedog on 2011-04-13
I would try it without the ** first.

---

### Post by Jonker on 2011-04-13
but do I need to exclude them on the source as on the dest. device?

---

### Post by blueridgedog on 2011-04-15
The exclude from should only apply to the source

---

### Post by Jonker on 2011-04-15
And what happens to the folders on the destination device. Should I leave the --delete parameter?

---

### Post by Jonker on 2011-04-16
Fine, I have tested the command on some test files and folders. Here's the result:

1. The exclude file entries are in the form:
```
###start exclude file###
- /testfolder1/
###end of exclude file###
```You don't have to do the [FONT=&quot]/**[/FONT] business.

2. If you have a folder [FONT=&quot]/testfolder1[/FONT] and you synchronize it with [FONT=&quot]/testfolder2[/FONT], the folders and files in [FONT=&quot]/testfolder2[/FONT] are:
```
/testfolder2
/testfolder2/testfolder1
and in /testfolder2/testfolder1 the content of /testfolder1
```So the commad creates the source folder in the destination folder. This is really a pain, because the system will crash ( it can't find the folders, because they all are in a folder). Is there a way of changing that?

3. Folders which don't exist on the source device are not deleted without the [FONT=&quot]--delete[/FONT] parameter. They are with it. So I think that I'll leave that parameter.

So my new command would be:```
sudo rsync -av /external /internal --exclude-from=/sync/exclude.txt --progress
```If you have answers to my problem, I would be very grateful, if you post them here.

---

### Post by Jonker on 2011-04-19
I've found out, that the dirs have to be like "/dir/" so the command is :
```
sudo rsync -av /external/ /internal/ --exclude-from=/sync/exclude.txt --progress
```

And I've run it again, but there was a grub rescue, do I need to run a 'update-grub'?

If the whole system is a little bit tricky, would it be easier to just sync. the programms?

Thanks!!!

---

### Post by Jonker on 2011-04-20
Ok, it worked fine. \\:D/

I first sync. the two systems. Then I could not install grub (I don't know why) so I used Supergrub2 to boot. Then I did update the grub.cfg from the system ==> it worked.

By the way. The Internal had Ubuntu 10.04 and the external 11.04 Beta 2. So it even works across different system versions. 

Thank you blueridgedog for being so patient with me, and helping me!!!

This Thead is solved!=D>

---

### Post by blueridgedog on 2011-04-20
> **Jonker said:**
> 
By the way. The Internal had Ubuntu 10.04 and the external 11.04 Beta 2. So it even works across different system versions. 


Interesting.  I think at this point you know more about rsync than I!

The syntax of the file is very tricky.  I hope you use what you developed to help others looking to do something similar.

---

### Post by Jonker on 2011-04-22
I thought that a summary would be helpful to certain people. Here it is.


  **Summary over the rsync command and the exclude file**

1. The syntax:
   
  The syntax of the rsync command with an exclude file is:
  ```
sudo rsync –av /source/ /target/ --exclude-from=/path/to/file.txt --progress
```  [FONT=Symbol]·         [/FONT]The source can be a folder or a mountpoint from a device. The target is the same.
  [FONT=Symbol]·         [/FONT]You only need to run this command as root (sudo) when you are copying system files (like with a full system backup).
  [FONT=Symbol]·         [/FONT]It’s very important, that you don’t forget the / after the source and target path!
   
  2.       The exclude file
   
  The exclude file is built up like this (“#” is a comment)
  ```
### Start exclude file ###
  ### folders to exclude ###
  - /path/to/folder1/
  - /path/to/folder2/
  ### files to exclude ###
  - /path/to/file1.txt
  - /path/to/file2.sh
  ### end of exclude file ###
```  [FONT=Symbol]·         [/FONT]Don’t forget the / after the folder. You don’t need an /path/to/folder/**.
  [FONT=Symbol]·         [/FONT]You need to save this file as .txt!
  [FONT=Symbol]·         [/FONT]There is a space after the minus.
  [FONT=Symbol]·         [/FONT]If you want to _include _a folder, then you need a plus instead of a minus (I haven’t tried this out).
   
  3.       The dry run (Testing the configurations)
  In general, you can try out, if your configurations work, with the parameter ‘-n’.
  Because the output on the screen is rather fast, I would suggest saving the output in a file:
  ```
 sudo rsync –av /source/ /target/ --exclude-from=/path/to/file.txt –progress –n > /path/to/resultfile.txt
```  This code will save the result in a file called “resultfile.txt” in the directory /path/to/.
   
   
   
   Thank you for helping!!!

---

