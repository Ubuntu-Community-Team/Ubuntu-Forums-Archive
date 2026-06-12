---
title: "Disk Space filled Up..!!!"
date: 2010-12-28
forum: General Help
---

### Post by shredderbond on 2010-12-28
Sorry if i am reposting, but i have tried most of things and it didn't worked out. :cry:

I have installed Ubuntu 10.04 x86_64 onto an existent Windows platform using Wubi installer with a disk size (for ubuntu) of 25 GB. Recently i started getting messages like:- disk space not sufficient etc.
Here is the output of the command: df -h

Filesystem            Size  Used Avail   Use% Mounted on
/dev/loop0             17G   16G   16M   100% /
none                     1.6G  296K  1.6G   1% /dev
none                     1.6G  300K  1.6G   1% /dev/shm
none                     1.6G   92K   1.6G   1% /var/run
none                     1.6G     0     1.6G   0% /var/lock
none                     1.6G     0     1.6G   0% /lib/init/rw
/dev/sda1              117G   70G  48G    60% /host

I have never seen /dev/loop0 device in my previous installations. I didn't know anything about dev/loop0 so a quick wikipedia link shows that its a 'loop mount of the file system'. Which in turn confuses me with the normal mounting of file system, because 'loop mount' should happen with the ISO images. But after installation of Ubuntu why it is still loop0, instead of some sda device.
Anyway, i tried 
sudo apt-get clear to clean up temp files. I have also tried: sudo du -sch * and got the following output:

7.8M    bin
30M    boot
4.0K    cdrom
596K    dev
15M    etc
du: cannot access `home/vishram/.gvfs': Permission denied
8.5G    home
69G    host
0    initrd.img
0    initrd.img.old
314M    lib
13M    lib32
0    lib64
16K    lost+found
8.0K    media
4.0K    mnt
4.0K    opt
du: cannot access `proc/6744/task/6744/fd/3': No such file or directory
du: cannot access `proc/6744/task/6744/fdinfo/3': No such file or directory
du: cannot access `proc/6744/fd/3': No such file or directory
du: cannot access `proc/6744/fdinfo/3': No such file or directory
0    proc
2.4G    root
7.3M    sbin
4.0K    selinux
200K    srv
0    sys
200K    tmp
3.5G    usr
378M    var
0    vmlinuz
0    vmlinuz.old
84G    total


The Host size is 117 GB out of which only 69 GB is used. Removing that if i sum up all, it does not exceed 9 GB. Still i am out of space..!!!

Please help me.
Thank you in anticipation.

---

### Post by mcduck on 2010-12-28
Your root is loop mounted since you are using a Wubi install. So the root is not its own partition, but a file located inside your Windows filesystem, and it's then loopmounted as the root of the Ubuntu system.

The size  or available space of the host OS is meaningless, the only thing that matters is the amount of space your reserved for Ubuntu. (while you may access the fels on the host filesystem, it's not usable space on your Linux root)

..and what comes to space used, you have a 17GB root, from which /home uses 8,5GB, /root 2,4GB and /usr 3,5GB. Those three alone give you 14,4GB of used space... Add all the smaller stuff and the numbers add up just fine to the reported 16GB used space....

If you want to free some more space, take a look into /root. You probably have deleted some files as the root suer, using a graphical file manager, but didn't empty root's trash so the files are still there...

Everything else seems perfectly normal, after those 2,5GB in /root the only thing left are your own personal files, located in /home.

---

### Post by shredderbond on 2010-12-29
Thanks for your reply. It really helped me a lot. When i logged in as root to see the content of the trash, it was already empty. But just after viewing the trash, my available space increased to 7 GB. I don't know what happened, but it's working fine for me now.
Thank you for your help.

regards
Vishram

---

