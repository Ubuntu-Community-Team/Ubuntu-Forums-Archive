---
title: "Missing hard drive space?"
date: 2009-11-16
forum: General Help
---

### Post by taquito on 2009-11-16
I have a desktop which is currently giving me the old "Free space: 0 bytes"

Running disk usage analyzer, I get total filesystem capacity: 35.3 GB, total filesystem usage: 33.6 GB.  So far, all of this makes sense for a 40 gig hard drive.

The problem that I'm having is that when I scan the filesystem, I can only find about 23 GB worth of files:


```
lethe@Eunoe:/$ sudo du / -h --max-depth=1 |grep [0-9]*G

3.9G	/usr
18G	/home
du: cannot access `/proc/9837/task/9837/fd/3': No such file or directory
du: cannot access `/proc/9837/task/9837/fdinfo/3': No such file or directory
du: cannot access `/proc/9837/fd/3': No such file or directory
du: cannot access `/proc/9837/fdinfo/3': No such file or directory
23G	/
```


```
lethe@Eunoe:/$ df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             36977704  35283816         0 100% /
varrun                  777912       248    777664   1% /var/run
udev                    777912        64    777848   1% /dev
devshm                  777912        12    777900   1% /dev/shm
overflow                  1024      1024         0 100% /tmp
```


I've cleared out the trash, I've looked for unexpectedly large files or backups stored in the wrong place, but haven't been able to find anything.  Does anyone have any hints for what might be taking up about a third of this partition?  Thanks in advance!

---

### Post by JoelOl75 on 2009-11-16
You can try:

sudo apt-get clean
sudo apt-get autoremove

This may get you some space.... You shouldn't be running on the edge like this as it causes fragmentation and slow performance.  I'd try dumping some media and unused packages.  Mostly 3rd party packages with static libraries take up alot of space, but MP3's and movies take up the lions share...

You can use a program like filelite to scan your drive and show you where all the space is being used (or misused/wasted)

Also bleachbit nad to a lesser extent the computer janitor may help clean up old logfiles and crap... Maybe a program is spewing alot of debug/log info into /var/log or into /var/mail

Hope this helps

---

### Post by pigphish on 2009-11-19
i have the same issue except I'm missing 10gb
df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             211G  200G  2.4G  99% /


Everytime I free space it still seems to eat it up somewhere.

---

### Post by XCan on 2009-11-19
Why not take a look at the Disk Usage Analyzer (Baobao) that's preinstalled in your Ubuntu? App -> Accs -> Disk Usage Analyzer.

---

### Post by wilee-nilee on 2009-11-19
I have a external HD that the package said was 320Gig. but it is actually only 298 gigs I forget the breakdown of why this is the case but it is a measurement issue.

---

