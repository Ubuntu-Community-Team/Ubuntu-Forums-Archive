---
title: "Multiple swap partitions"
date: 2011-08-01
forum: General Help
---

### Post by xdeathcorex on 2011-08-01
Reinstalled Ubuntu 11.04 and found out I have 3 swap partitions :facepalm:

Here's gparted info I took out earlier:
[img]http://i.imgur.com/qRDmV.png[/img]

My question is:
1. What's the benefit of having swap partition?

2. Does it really good to have more swap partitions?

3. If I want to delete two of them, will I gain more space HD space? If so how do I extend the space from the deleted partition? or if I delete the swaps from gparted, it will automatically extend the disk size?

Thanks. Excuse my english. Tried to be more simpler :p

---

### Post by pqwoerituytrueiwoq on 2011-08-01
delete sda5 and sda6 and grow sda8
or delete 6 and 8 and grow sda7
now edit /etc/fstab and change the UUID on the swap partition
right click partition -> properties to get the uuid of sda5

---

### Post by oldfred on 2011-08-01
Swap is when you do not have enough RAM to run program(s). It was very important when you only have 256MB or so of RAM. Now wtih GB of RAM it is less important. It now takes many programs or video editing to actually use swap. Swap is also used for hibernating if you do that.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you had multiple installs I suppose you could use different swaps, but I see no real good reason to have multiple swaps unless you are testing something unusual.

You need to check which swap you are using in fstab. Since your install is sda7 and sda8 is next to it, I would expect that to be the one you are using. But if you delete the other two you will not be able to expand sda7 as swap sda8 will be  in between. You will only be able to edit partition from a liveCD and will have to click on swap partitions and right click swap off to allow deleting.

To see UUIDs
```
sudo blkid
```

Backup fstab
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

then check that edit is ok
```
sudo mount -a
```

---

### Post by FormatSeize on 2011-08-01
I honestly don't know the answer to this question, but I've always done it, thinking that it is working (I don't know if it actually is, though).

I only have one swap partition when I use a disk with multiple partitions. And then when I boot into a particular distro, I go to a terminal and type:
```
/sbin/swapon sda[X]
```

Is this working, or am I just fooling myself?

---

