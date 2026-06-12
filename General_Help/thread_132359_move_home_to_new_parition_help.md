---
title: "move /home to new parition help"
date: 2006-02-18
forum: General Help
---

### Post by awalsh on 2006-02-18
Hi,

Recently ive decided to move my /home directory to a new partition, as it seems the best thing to do. I have created the partition, moved the /home files across to the new partition, below is the setup:

/home <----- This needs moving
/newhome <------ This is the new partition

Now i need to know how can i get it to recognise /newhome as /home, if i renamed it to /home then would it by default use that partition or is there something im missing? I dont want to lose my data, as i havent really got time to backup at the moment.

```

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              63G   12G   50G  19% /
tmpfs                 364M  8.0K  364M   1% /dev/shm
tmpfs                 364M   13M  351M   4% /lib/modules/2.6.12-10-686/volatile
/dev/hda4              46G   14G   30G  31% /newhome


```

Any help would be appreciated

Thank you

Andrew

---

### Post by JasonL on 2006-02-18
I found this guide [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) seems pretty good, should help you.

---

### Post by awalsh on 2006-02-18
done thanks, do you think 20gb / is ok? Considering shrinking / now home is out of the way....

---

### Post by cronholio on 2006-02-18
20 gig is more than enough. Even 5 should do it.

---

### Post by JasonL on 2006-02-18
Yeh, should be plenty.

---

