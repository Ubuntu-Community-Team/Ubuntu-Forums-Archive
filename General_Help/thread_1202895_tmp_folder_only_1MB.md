---
title: "/tmp folder only 1MB ???"
date: 2009-07-02
forum: General Help
---

### Post by wiba40 on 2009-07-02
Hi all,

I am quite new to Ubuntu, and so far I like it! :)

However I have recently encountered a strange problem to which I can't find a solution anywhere. When I try to download a .deb file I get the following error message:
"Not enough space on disk to store /tmp/file.deb.par" (sorry for bad translation from Swedish version)

When I do df -h I get:
/dev/sdb1             4,6G  3,3G  1,2G  75% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  216K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  156K  501M   1% /dev
tmpfs                 501M  3,4M  498M   1% /dev/shm
lrm                   501M  2,2M  499M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb4              15G  862M   13G   7% /home
overflow              1,0M 1020K  4,0K 100% /tmp
/dev/sdb2             165G   61G  104G  37% /media/Stordisk

In my opnion everything looks fine, except for the "overflow" row. I can't understand this at all?

Any help is much appreciated!

Regards
William

---

### Post by wojox on 2009-07-02
Did you try this

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

---

### Post by wiba40 on 2009-07-02
> **wojox said:**
> Did you try this

```
sudo apt-get clean
``````
sudo apt-get autoclean
```

Yes, but without success :(

---

### Post by wiba40 on 2009-07-02
Problem solved. I browsed some more forums and learnt that the /temp folder is actually a part of the swap partition. And for some reason my swap partition had gone nuts and stopped workings, so I reformatted it in Gparted and now evereything is fine! Puh!

---

### Post by geirha on 2009-07-02
If, during boot, the root filesystem (where /tmp is located) is full, 1MB of RAM will be mounted to /tmp so that programs that need to write temporary files in order to function, will be able to run properly (i.e. actually let you boot). To fix, free up some space on /, which you had done by the time you ran that df, and either reboot, or run ```
sudo /etc/init.d/mountoverflowtmp stop
```

On some systems, /tmp is swap, but not in Ubuntu.

---

### Post by joehill on 2012-03-20
Hmm. I'm having this exact problem now but none of these solutions work. Any ideas?

---

### Post by uRock on 2012-03-20
This thread is very old. Please start a new thread on the subject.

Thread Closed.

---

