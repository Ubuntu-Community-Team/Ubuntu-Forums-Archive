---
title: "Mounting a new partition. Problem"
date: 2009-09-02
forum: General Help
---

### Post by Cluster_teg on 2009-09-02
Hello. I'm new here and this is my first thread. I've faced a newbie problem an I need some assistance please.

1. I've created a new fat32 partition using Gparted program
2. I create a folder /home/username/foldername and give 777 rights to it. It's owner is 'username' for example.
3. I mount the partition to this folder but after mounting the partiton, the owner of the folder becomes 'root:root' and so I can not write to it using 'username' account.

What actions do I need to do in order to have full access to this folder?

Thank you all in advance.

---

### Post by davetv on 2009-09-02
might try "sudo chown username:username foldername"

---

### Post by scouser73 on 2009-09-02
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by Cluster_teg on 2009-09-02
Thank you very much for your answers =) , but they did not solve the problem. Here is what I get:
```

cluster@clusterx:~$ pwd
/home/cluster
cluster@clusterx:~$ mkdir test
cluster@clusterx:~$ chmod 777 test
cluster@clusterx:~$ ls -la
drwxrwxrwx  2 cluster cluster   4096 2009-09-02 16:06 test
cluster@clusterx:~$ sudo mount /dev/sda1 /home/cluster/test
cluster@clusterx:~$ ls -la
drwxr-xr-x  2 root    root     16384 1970-01-01 03:00 test
cluster@clusterx:~$ sudo chown cluster:cluster test
chown: changing ownership of `test': Operation not permitted

```
(i've deleted part of '-ls' command output because there are much more files and folders)

---

### Post by Cluster_teg on 2009-09-02
I've spent several hours last evening to get this work out but none of the options from instructions helped, so I've decided to ask here, on forums.
The reason of all this is to have full access to the partition in order to use it as a regular folder. I want to set up an FTP server on this PC and also to upload torrents from it.

---

### Post by P4man on 2009-09-02
I think you have to change the permissions in fstab.
Imagine you dont have write permission on some folder or drive.. you mount it to another folder, and give yourself ownership of the mountpoint. Would be too easy to overcome any restrictions :) 

So i guess whats happening here is that the ownership and permissions defined in fstab are applied to your mountpoint. Or you have no fstab entry for /dev/sda1, and the default is read only. Can you post the output of

cat /etc/fstab

?

---

### Post by Cluster_teg on 2009-09-02
```

root@clusterx:/home/cluster# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=57c38cd0-0a86-4b95-bcf2-2dd81aac9cc2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=3c122bbe-c832-4d10-9b50-5c7845dd7c46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0 

/dev/sda1   /home/cluster/test   vfat  user,exec,rw 0 0 

```

The last string I've added yesterday.
Also before performing the actions from previous my posts I've unmounted it manually using 'sudo umount /dev/sda1' command.

Here is what I get with df command:
[HTML]
cluster@clusterx:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              5131108   2739596   2130860  57% /
tmpfs                   191664         0    191664   0% /lib/init/rw
varrun                  191664       108    191556   1% /var/run
varlock                 191664         0    191664   0% /var/lock
udev                    191664      2696    188968   2% /dev
tmpfs                   191664         0    191664   0% /dev/shm
lrm                     191664      2204    189460   2% /lib/modules/2.6.27-14-generic/volatile
/dev/sda1             33302496        32  33302464   1% /home/cluster/test
[/HTML]

---

### Post by P4man on 2009-09-02
Just saw this:
> ntfs/vfat = permissions are set at the time of mounting the partition with umask, dmask, and fmask and **can not be changed with commands such as chown or chmod.**

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Not too sure how to make an fstab entry with rw permissions for a vfat partition, but if you google that, Im sure you'll find it

---

### Post by Cluster_teg on 2009-09-02
**P4man**As far as I understand the /fstab/ is used to automate the process of mounting partitions. I want first it to work out the general way and then to automate the process ))
But as I've already tried everything I could, I will now try out your suggestion. Thank you =)

I am also thinking about reformatting it to NTFS or EXT3 if this is the problem of the file system on partition.

---

### Post by Cluster_teg on 2009-09-02
**P4man, **I've tried the instructions from the article you've adsvised:
```

cluster@clusterx:~/test$ cat /etc/fstab
(some code is deleted here not to spam the thread)
/dev/sda1   /home/cluster/test   vfat  user,exec,rw,dmask=000,fmask=111 0 0 
cluster@clusterx:~$ sudo mount -a
cluster@clusterx:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             33302496        32  33302464   1% /home/cluster/test

```

and here is what I've got:

```

cluster@clusterx:~$ ls -la
drwxrwxrwx  3 root    root     16384 2009-09-02 16:53 test
cluster@clusterx:~$ cd test
cluster@clusterx:~/test$ mkdir test2
cluster@clusterx:~/test$ ls -la
drwxrwxrwx  2 root    root    16384 2009-09-02 17:00 test2

```

This makes me happy because for now this is the only way I've finally made it working (I've became a little bit nervous messing with all this).
But I have a question in this case: is this security-safe to let it be this way? Is that normal that the folder has root permissions and the full access to it?

(Will now try to find out how to make user permissions to the folder in fstab and if I find - I will answer here) =)

---

### Post by nikhilk on 2009-09-02
> **Cluster_teg said:**
> Hello. I'm new here and this is my first thread. I've faced a newbie problem an I need some assistance please.

1. I've created a new fat32 partition using Gparted program
2. I create a folder /home/username/foldername and give 777 rights to it. It's owner is 'username' for example.
3. I mount the partition to this folder but after mounting the partiton, the owner of the folder becomes 'root:root' and so I can not write to it using 'username' account.

What actions do I need to do in order to have full access to this folder?

The uid and gid options can be used with a fat32 partition to specify the ownership of that partition after it is mounted instead of root:root

The options are specified using the -o switch in the mount command-line. e.g.
```
mount -t vfat /dev/sda2 /home/cluster/test -o "user,exec,rw,uid=username,gid=usergroup"
```

---

### Post by Cluster_teg on 2009-09-02
You can congratulate me )) I've found the solution.
Adding uid=1000,gid=1000 to fstab made correct the permissions to the folder =)
```

/dev/sda1   /home/cluster/test   vfat  user,exec,rw,uid=1000,gid=1000 0 0 

```
Result:
```

cluster@clusterx:~$ ls -la
drwxr-xr-x  4 cluster cluster  16384 1970-01-01 03:00 test
cluster@clusterx:~$ cd test
cluster@clusterx:~/test$ mkdir test4
cluster@clusterx:~/test$ ls -la
drwxr-xr-x  2 cluster cluster 16384 2009-09-02 17:00 test2
drwxr-xr-x  2 cluster cluster 16384 2009-09-02 17:07 test3
drwxr-xr-x  2 cluster cluster 16384 2009-09-02 17:13 test4

```

Thank you very much!!!
The problem is solved now, will go further with setting other things up.

Thank you all who were involved in this troubleshooting =D>

---

