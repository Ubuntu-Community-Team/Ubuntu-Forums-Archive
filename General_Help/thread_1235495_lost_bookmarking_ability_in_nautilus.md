---
title: "lost bookmarking ability in nautilus"
date: 2009-08-09
forum: General Help
---

### Post by zedi on 2009-08-09
I had total freeze of desktop; mouse & keyboard were not responding so I had to turn of power. From that moment Nautilus is forgetting bookmarks after log out. It's very annoying! I tried to reinstall Nautilus, but it didn't work. Searched Goggle & forums – no results.
One more thing, in syslog I have about 1000 disturbing messages, quote: “attempt to access beyond end of device” (sdb7 – my home partition). 
I'm completely lost and desperately need help. Anybody, please!

---

### Post by XCan on 2009-08-09
I would recommend you to unmount your home partition and run ```
 fsck /dev/sdb7 
```

Also, you could try and remove the contents inside your .nautilus dir in your home dir, make a backup of it first though.

---

### Post by zedi on 2009-08-09
Xcan,
        Thank you! You were right, mine home partition had errors. Couldn't run fsck (couldn't unmount it), but I used Live CD & did check with GParted. Seems to be OK now. I lost few files & had to reset aMule etc.
BTW, I'm thinking about formating my home partition now, because  it is third time already mine “~” had an errors. What command should I use to copy mine home folder to external drive? I know nothing about terminal, but I'm able to copy and paste command, if someone will supply it for me. Would you be so kind, please?

---

### Post by XCan on 2009-08-10
If you are going to keep the installation and just reformat the home partition I think the easiest for you is to tar your home folder first and copy it to an external drive. You can use

```
 tar -cf home.backup.tar /home/your/user 
```
```
 mv home.backup.tar /path/to/your/external/drive 
```

tar will keep the permissions and timestamps on your files which may come in handy when you restore it later.

---

### Post by zedi on 2009-08-10
Xcan,
    Great idea! You are a legend. Most definitely I'm going to do it.
Many thanks for your help!!!

---

### Post by XCan on 2009-08-10
You're welcome, good luck with the partition! :)

---

