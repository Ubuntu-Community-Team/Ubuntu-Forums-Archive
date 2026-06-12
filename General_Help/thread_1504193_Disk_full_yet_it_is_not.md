---
title: "Disk full yet it is not"
date: 2010-06-07
forum: General Help
---

### Post by UggsY on 2010-06-07
Hi everyone, i'm having issues in trying to copy files from one hard drive to another. The destination disk is not full yet I get the message "Error creating directory: No space left on device".

Here's the df -h result :

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             450G  5.1G  422G   2% /
none                  1.6G  368K  1.6G   1% /dev
none                  1.6G  456K  1.6G   1% /dev/shm
none                  1.6G  104K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
/dev/sdb1             299G  282G   17G  95% /media/2AC2B4A5C2B476A3
/dev/sdc1             466G  245G  222G  53% /media/720974F52DB56D96

So I'm trying to copy from sdb1 to sdc1, which is obviously not full.


I did a df -i thinking that i had reached a file number limit, but it is far from it.

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1            29917184  197936 29719248    1% /
none                  212163     927  211236    1% /dev
none                  214272       6  214266    1% /dev/shm
none                  214272      54  214218    1% /var/run
none                  214272       1  214271    1% /var/lock
none                  214272       3  214269    1% /lib/init/rw
/dev/sdb1            17107440   24936 17082504    1% /media/2AC2B4A5C2B476A3
/dev/sdc1            232415200      15 232415185    1% /media/720974F52DB56D96

Can you help me ?
(edit: I forgot to say that both disks are formated in NTFS.)

(sorry for my poor english)

---

### Post by xoomer.ap on 2010-06-07
**UggsY**, maybe you should check out the mountpoints?
Maybe, similar problem was with me. Funny, I was forgot my "mountpoint-scheme". In my case, as result - I was copying big data to /. :)

Look at this:[http://translate.google.com.ua/translate?js=y&prev=_t&hl=ru&ie=UTF-8&layout=1&eotf=1&u=http://unixforum.org/index.php%3Fshowtopic%3D113591&sl=ru&tl=en]("http://translate.google.com.ua/translate?js=y&prev=_t&hl=ru&ie=UTF-8&layout=1&eotf=1&u=http://unixforum.org/index.php%3Fshowtopic%3D113591&sl=ru&tl=en")
Similar to your case?

---

### Post by bumanie on 2010-06-07
I too thought of / being full. Check out > df -h /

---

### Post by UggsY on 2010-06-07
Here's what i get with 

> df -h /                      Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             450G  4.7G  422G   2% /

It appears i cannot even create a new file on sdc1, it says it is full too.

Edit: Okey, I fixed my problem, I just unmounted both hard drives and mounted them back and I can create new file on the one that was said to be be full. I haven't got the faintest as to why but it is now working...

---

### Post by bumanie on 2010-06-07
Ok - sorry, I sort of misread the original post - you want to copy from /dev/sdb to /dev/sdc and both disks are formatted to ntfs; your original df -h is showing that /dev/sdb is 95% full - that is probably your problem.

---

