---
title: "automatic updates"
date: 2009-09-01
forum: General Help
---

### Post by Dr.Tran on 2009-09-01
Hi i'm new to linux and Ubuntu(first time using it),
      i am currently dual booting vista and ubuntu 9.04 on my laptop, When i try to download the automatic updates for ubuntu it gives me an error explaining that i have to free up disk space but i have over 100 GB of storage.
any help would be most appreciated.

---

### Post by Vishnu V on 2009-09-01
I think it is due to there is not enough space on partition for ubuntu and you have free space on other  drive(for windows).

---

### Post by matsuzine on 2009-09-01
Did you use the automated partition setup in the installer (As opposed to setting them up manually during the install)?  

[[COLOR=Green]this might be helpful[/COLOR]]("http://www.linuxquestions.org/questions/linux-newbie-8/cant-update-ubuntu-insufficient-drive-space-734585/")


Could you post the results of command:

```

df -h

```which will list the space available on each partition.  I think you will see that Ubuntu is indeed out of space, which may be happening b/c of a bug in the automated partition setup.  You can resize the partitions using gparted, which is available to install from the repositories, but you should back any data up before just in case.

---

### Post by anujpathania on 2009-09-01
You probably starved your ubuntu partition for space. In My Places check the properties for your disk and see the space available.

---

### Post by mortiment on 2009-09-01
I'm having the same problem and here's my result:
> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  104K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  152K  1.8G   1% /dev
tmpfs                 1.8G  532K  1.8G   1% /dev/shm
lrm                   1.8G  2.4M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp

---

### Post by P4man on 2009-09-01
**/dev/sda6 2.3G 2.3G 0 100% /**

Obviously, your root "/" is full

Hardly surprising with such a small size!!

Search the forum to find out how to resize them (short version: boot live cd, run partition editor, unmount and swap off, resize extended partition first).

---

### Post by matsuzine on 2009-09-03
Here's a link explaining this problem:

[http://ubuntuforums.org/showthread.php?p=7658271#post7658271](http://ubuntuforums.org/showthread.php?p=7658271#post7658271)

---

