---
title: "how to fix grub.error 17?"
date: 2009-11-19
forum: General Help
---

### Post by g.zhen.ning on 2009-11-19
I upgraded to 9.10 a few weeks ago. after that, my box was running slower then before.
and pitfall is somehow full of log file in /var/log folder. so I have to cd /var/log && rm * rf (rm * is very very bad habit)

today I startup my computer, it say something like "filesystem check field" and run into a maintain-shell. so I stupid just fsck /var. it prompt me something and I just always y.......
restart, it appearer.
---
grub loading, please wait....
error 17
----

so I use my 8.04 livecd .
sudo grub
-----
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
------


Device Boot Start End Blocks Id System
/dev/sda1 * 1 3650 29318593+ 83 Linux
/dev/sda2 3651 6082 19535040 83 Linux
/dev/sda3 6083 9729 29294527+ 5 Extended
/dev/sda5 6083 7662 12691318+ 83 Linux
/dev/sda6 7663 9486 14651248+ 83 Linux
/dev/sda7 9487 9729 1951866 82 Linux swap / Solaris
ubuntu@ubuntu:~$


---------
any thought here would be appreciated... very appreciated..

---

### Post by oldfred on 2009-11-20
When you say upgraded I am assuming old grub not grub2 from a clean install. Or selecting to changed to new grub after the update.

Errors only come from old grub but it could be because you reinstalled old grub from your 8.04 CD? 

This script documents you system and how it is booting. You can download &  run it from the liveCD.

Boot Info Script 0.34 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions 
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) 
cd to directory saved to: 
chmod 755 boot_info_script034.sh 
sudo ./boot_info_script034.sh 
or as example if on desktop 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by g.zhen.ning on 2009-11-20
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________
```

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: 
```_________________________________________________________________________

```
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: 
```_________________________________________________________________________
```

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: 
```_________________________________________________________________________

```
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: 
```_________________________________________________________________________

```
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7:
``` _________________________________________________________________________

```
    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ 
```_____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b2a9b

```
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,637,249    58,637,187  83 Linux
/dev/sda2          58,637,250    97,707,329    39,070,080  83 Linux
/dev/sda3          97,707,330   156,296,384    58,589,055   5 Extended
/dev/sda5          97,707,393   123,090,029    25,382,637  83 Linux
/dev/sda6         123,090,093   152,392,589    29,302,497  83 Linux
/dev/sda7         152,392,653   156,296,384     3,903,732  82 Linux swap / Solaris
```


blkid -c /dev/null: ____________________________________________________________
```

/dev/sda1: UUID="6d31947e-7930-4cd8-bb31-289ff2df1bdd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="8424130b-dbc7-40ae-a5bd-9ca4f3f6cf20" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1a7ecf00-757e-47d1-9d28-881d9f3c3182" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="8d2c2261-3825-4791-9e9f-f8fd9ca459f3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="18cbff98-9301-459e-9bc0-41d7f7eb33df" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
```

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

---

### Post by oldfred on 2009-11-20
The script says you have grub looking in sda1 or partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst, but there are no files shown. It looks like your install did not complete?

Did you do an  upgrade or a clean install? An upgrade should not have erased the existing boot files or menu.lst.

---

