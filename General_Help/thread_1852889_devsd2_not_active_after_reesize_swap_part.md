---
title: "/dev/sd2 not active after reesize swap part"
date: 2011-10-01
forum: General Help
---

### Post by DanielSenat on 2011-10-01
Hi ,

I followed the guide in this FAQ([https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)) to get a bigger Swap. The swap(/dev/sd3) got bigger but my /dev/sd2 - filesystem extended is not active anymore. Can i delete it? Is it a problem?

df gives me: [http://pastebin.com/dvJhxw9N](http://pastebin.com/dvJhxw9N)
sudo fdisk -l[FONT=Verdana] gives me: [/FONT]http://pastebin.com/bvGqpuXr (sorry for swedish)

[http://imgbin.org/index.php?page=image&id=5254](http://imgbin.org/index.php?page=image&id=5254)

deleted the sd2 and resulted in [http://imgbin.org/index.php?page=image&id=5255](http://imgbin.org/index.php?page=image&id=5255)

---

### Post by plucky on 2011-10-01
> **DanielSenat said:**
> Hi ,

I followed the guide in this FAQ([https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)) to get a bigger Swap. The swap(/dev/sd3) got bigger but my /dev/sd2 - filesystem extended is not active anymore. Can i delete it? Is it a problem?

df gives me: [http://pastebin.com/dvJhxw9N](http://pastebin.com/dvJhxw9N)
sudo fdisk -l[FONT=Verdana] gives me: [/FONT]http://pastebin.com/bvGqpuXr (sorry for swedish)

[http://imgbin.org/index.php?page=image&id=5254](http://imgbin.org/index.php?page=image&id=5254)

deleted the sd2 and resulted in [http://imgbin.org/index.php?page=image&id=5255](http://imgbin.org/index.php?page=image&id=5255)

/dev/sda2 was just the extended partition,which used to contain the swap file.As you now have the swap file outside of the extended partition,it is ok to delete it.

Since you recreated the swap file,did you remember to include it in the /etc/fstab file?

Please post output from a terminal for ```
free -m
cat /etc/fstab
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by DanielSenat on 2011-10-01
> **plucky said:**
> /dev/sda2 was just the extended partition,which used to contain the swap file.As you now have the swap file outside of the extended partition,it is ok to delete it.

Since you recreated the swap file,did you remember to include it in the /etc/fstab file?

Please post output from a terminal for ```
free -m
cat /etc/fstab
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```

:)

[http://pastebin.com/anmz5jvT](http://pastebin.com/anmz5jvT)

---

### Post by DanielSenat on 2011-10-01
Looks ok?

---

### Post by plucky on 2011-10-01
> **DanielSenat said:**
> Looks ok?

Yes

---

