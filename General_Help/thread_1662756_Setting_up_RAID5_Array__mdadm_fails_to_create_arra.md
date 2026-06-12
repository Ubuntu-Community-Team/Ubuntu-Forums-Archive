---
title: "Setting up RAID5 Array : mdadm fails to create array"
date: 2011-01-08
forum: General Help
---

### Post by kravitz999 on 2011-01-08
I've been sorting through the posts trying to find a suitable tutorial for a noob trying to set up a 3 disk RAID5 array without success.  I'm trying to make a non-bootable array for file sharing, not for installing ubuntu on.  I've read up on mdadm and it seemed relatively straight forward to me but in the end it wouldn't create the array.  

Im using a Gigabyte GA-880GA-UDH3 mobo and 3x2TB WD green drives

For each of the 3 drives [sdb, sdc, sdd] I made new partitions as below :[INDENT] [FONT=Courier New][SIZE=1]user@al9000:~$ sudo fdisk /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-243201, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-243201, default 243201): 
Using default value 243201

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.[/SIZE][/FONT]
[/INDENT]Then I used the following syntax with mdadm and got the following, unhelpful, result :[INDENT] [FONT=Courier New][SIZE=1]user@al9000:~$ mdadm --create /dev/md01 --verbose --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
mdadm: failed to create /dev/md01

user@al9000:~$[/SIZE][/FONT]
[/INDENT]I tried the --examine option on one of the drives :[INDENT][FONT=Courier New][SIZE=1] user@al9000:~$ sudo mdadm --examine /dev/sdb
mdadm: No md superblock detected on /dev/sdb.[/SIZE][/FONT]
[/INDENT]I'll confess to really just getting me feet wet in anything beyond the basics of ubuntu so perhaps i'm missing something very simple, any suggestions would be much appreciated.

I found this [site]("http://bredsaal.dk/software-raid-in-ubuntu") that did things along the same lines and the mdadm [manual]("http://man-wiki.net/index.php/8:mdadm") seemed well documented as well.  

thanks in advance

---

### Post by dcstar on 2011-01-09
> **kravitz999 said:**
> 
.........
Then I used the following syntax with mdadm and got the following, unhelpful, result :
```
user@al9000:~$ mdadm --create /dev/md01 --verbose --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
**mdadm: failed to create /dev/md01**
```
.........

```
man sudo
```

---

### Post by kravitz999 on 2011-01-09
well, that was staring me in the face the whole time - spent too much time in front of the posts to pick up the simple things i suppose :(

thanks

---

