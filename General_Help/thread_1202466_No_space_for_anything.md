---
title: "No space for anything"
date: 2009-07-02
forum: General Help
---

### Post by andrewrw66 on 2009-07-02
I am dual booting with Pista(i mean vista) and Ubuntu 9. I want to download the full Open Office suite as well as a few more tid bits, but when i try and even when i try and do the updates that ubuntu suggests, it says i have no room. It tells me to delete 272 mb of files. So i go through the apps and uninstall what i dont want and it still says the same error.

There is nothing in the trash at all.. 

Any suggestions ???

---

### Post by prem1er on 2009-07-02
Post the results of this from the command line.

```
df -h
```

---

### Post by andrewrw66 on 2009-07-02
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                 470M     0  470M   0% /lib/init/rw
varrun                470M  104K  470M   1% /var/run
varlock               470M     0  470M   0% /var/lock
udev                  470M  160K  469M   1% /dev
tmpfs                 470M  500K  469M   1% /dev/shm
lrm                   470M  2.4M  467M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp


Thank you

---

### Post by moster on 2009-07-02
You install Ubuntu in partition which have size of 2.3 GB I though it was impossible :)
Obviusly it is too small :)

---

### Post by philcamlin on 2009-07-02
/dev/sda6             2.3G  2.3G     0 100% !!!!!!!!!

you need atlest 4 gigs to install and have room for updates and such :popcorn:

---

### Post by andrewrw66 on 2009-07-02
How do i change this ???

---

### Post by Hangwire on 2009-07-02
I guess you could do it with the ubuntu built-in partition manager. Or Norton PartitionMagic. Take some space from some other partition and add it to the one you have Ubuntu installed on. Its always risky, I've done it 3 times and I still never had a problem.

---

### Post by moster on 2009-07-03
Huh, if you are lost, boot again from live cd and go to partition editor. He can resize that for you. I think it can take few hours, be aware.

You cannot do it from installed linux because partition you trying to resize is in use.

---

