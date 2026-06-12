---
title: "How to reestablish permissions to chmod cmd if chmod itself was 644 as root user."
date: 2012-05-01
forum: General Help
---

### Post by Miguel Tavares on 2012-05-01
Problem #1:

In a given Interview i was asked on how would it be possible to 
reestablish permissions to chmod cmd if chmod itself was 644 as root user

Linux Chmod permissions were changed to -x as root user.
How to reestablish the cmd functionality back again?

Analysis:

```
root /bin # cp chmod ~
root /bin # chmod -x chmod
root /bin # ls -l chmod
-rw-r--r-- 1 root root 49952 Dec  7 21:43 chmod
root /bin # touch 1; chmod 777 1
-bash: /bin/chmod: Permission denied
```

Workaround:

Concept #1:

trying to use debugfs with 'mi'
in order to change the permissions within an inode corresponding to chmod. 
In this scenario inode 521248 will be accessed.

```
root /bin # ls -li chmod
521248 -rw-r--r-- 1 root root 49952 Dec  7 21:43 chmod
1042435
```

Test Run #1:

So we copy the /bin/chmod to /home as we wont be able to use the write mode on debugfs on /
And we will have the following:

```
root ~ # df -kh
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-lv_root
                       19G  598M   17G   4% /
tmpfs                 122M     0  122M   0% /dev/shm
/dev/sda1             485M   38M  422M   9% /boot
/dev/sdb1             9.9G  1.4G  8.0G  15% /var
/dev/sdc1             9.9G  1.6G  7.9G  17% /home
/dev/sdd1             9.9G  1.2G  8.2G  13% /usr
/dev/sde1             9.9G  492M  8.9G   6% /opt
/dev/sdf1             9.9G  1.9G  7.6G  20% /backup
```


What we are interested is /dev/sdc1

```
root ~ # debugfs
debugfs 1.41.12 (17-May-2010)
debugfs:  open -w /dev/sdc1
debugfs:  params
Open mode: read-write
Filesystem in use: /dev/sdc1

debugfs:  ncheck 12
Inode Pathname
12 //chmod

debugfs:  stat chmod
Inode: 12   Type: regular    Mode:  0644   Flags: 0x0
Generation: 3121076680    Version: 0x00000000
User:     0   Group:     0   Size: 49952
File ACL: 0    Directory ACL: 0
Links: 1   Blockcount: 112
Fragment:  Address: 0    Number: 0    Size: 0
ctime: 0x4f9f6f8a -- Tue May  1 05:07:22 2012
atime: 0x4f9f6f8a -- Tue May  1 05:07:22 2012
mtime: 0x4f9f6f8a -- Tue May  1 05:07:22 2012
Size of extra inode fields: 4
BLOCKS:
(0-11):16384-16395, (IND):16396, (12):16397
TOTAL: 14
```

We can see the above set permissions 0644 but what we would really need would be 744 so:

> debugfs:  mi chmod
                          Mode    [0100644] **0100744**
                       User ID    [0]
                      Group ID    [0]
                          Size    [49952]
                 Creation time    [1335848842]
             Modification time    [1335848842]
                   Access time    [1335848842]
                 Deletion time    [0]
                    Link count    [1]
              Block count high    [0]
                   Block count    [112]
                    File flags    [0x0]
                    Generation    [0xba07d9c8]
                      File acl    [0]
           High 32bits of size    [0]
              Fragment address    [0]
               Direct Block #0    [16384]
               Direct Block #1    [16385]
               Direct Block #2    [16386]
               Direct Block #3    [16387]
               Direct Block #4    [16388]
               Direct Block #5    [16389]
               Direct Block #6    [16390]
               Direct Block #7    [16391]
               Direct Block #8    [16392]
               Direct Block #9    [16393]
              Direct Block #10    [16394]
              Direct Block #11    [16395]
                Indirect Block    [16396]
         Double Indirect Block    [0]
         Triple Indirect Block    [0]
debugfs:  quit

Proof of concept at inode 12:

> root ~ # ls -la
total 184
dr-xr-x---  3 root root   4096 May  1 04:49 .
dr-xr-xr-x 21 root root   4096 May  1 04:07 ..
-rw-------  1 root root  29326 Apr 29 04:35 .bash_history
-rw-r--r--  1 root root     18 May 20  2009 .bash_logout
-rw-r--r--  1 root root    176 May 20  2009 .bash_profile
-rw-r--r--  1 root root    262 Feb 28 12:53 .bashrc
```
**-rwxr-xr-x**  1 root root  49952 May  1 04:49 chmod
```
-rw-r--r--  1 root root    100 Sep 23  2004 .cshrc
-rw-r--r--  1 root root     51 Feb 22 04:24 .gitconfig
-rw-------  1 root root    103 Feb 23 22:40 .lesshst
-rw-------  1 root root     34 Jan  1 00:33 .lvm_history
-rw-------  1 root root  43777 Feb 24 20:55 .mysql_history
-rwxr-xr-x  1 mtavares mtavares   205 Nov 25  2008 ._noip-2.1.9-1
-r--------  1 root root   1675 Feb 26 04:07 rod.pem
drwx------  2 root root   4096 Feb 22 04:27 .ssh
-rw-r--r--  1 root root    129 Dec  3  2004 .tcshrc
-r--------  1 root root   1671 Feb 18 17:45 testserver.pem
root ~ #

To finish and wrap this up, we just cp the /home/chmod to /bin and permissions available again to root.

Kindest Regards

Miguel Tavares
*stryng@gmail.com*

---

### Post by codemaniac on 2012-05-01
are you asking something or this is a HOWTO ?

---

### Post by Miguel Tavares on 2012-05-01
Hello codemaniac.

As you can see in the first few lines this is a reply for a question that have been made to me.
The scenario was simple. Imagine a given user as root user, on path / issues a chmod -R 000.
The obvious question, how can he use again chmod since the binary in /bin is 000 chmoded???

In this case i used degugfs to manipulate the inodes permissions.

Can i dare you to come up with a different answer ??????? Or a different solution ???


Kindest Regards
Miguel

---

