---
title: "Where to sss /mount partition question"
date: 2012-09-05
forum: General Help
---

### Post by matimont on 2012-09-05
Hi,

I have 2 partitions on my VPS, one 10GB and another one 20GB, I recently formated the 20GB partition to make it available, now here's my question:

I mounted in /home and it did drop all my sites there, I could not access them anymore until I unmounted a few minutes later. All I was getting was:
**Not Found**

 The requested URL / was not found on this server.


I did mount doing this: 
sudo mount /dev/vdb1 /home

and screwed up my sites until I unmounted a few minutes later...

Where's the best place to mount the partition?

I guess my question is if I mount the partition let's say in /extraspace will I be able to increase my /home folder size anyways?

Hope I'm being clear.

Thanks!

---

### Post by ajgreeny on 2012-09-05
It sounds as if you are trying to increase the size of your /home folder or partition by mounting another partition in /home; correct?

I think that you will be disappointed doing that, though you should be able to mount it in a separate  folder in your /home.

So instead of ```
sudo mount /dev/vdb1 /home
```make a new folder in /home called anything you like that makes sense to you, eg mount, then use command ```
sudo mount /dev/vdb1 /home/*username*/mount
``` It may work; it may not, but I think it more likely than direct in /home.

---

### Post by matimont on 2012-09-05
So If I would like to add exta space to /home where I have all my sites hosted, will make sense to create a folder under /home and mount a partition there?
My VPS provider gave me 10GB root partition plus 20GB on another partition, so I'm running out of space on my Home directory and would like to increase it by mounting the 20GB partition. My provider said they can't resize the root partition so I have to figure out a way to increase my storage in /home.

---

