---
title: "Extend extended partition"
date: 2011-07-12
forum: General Help
---

### Post by scathlock on 2011-07-12
My partitions looks like on the picture:


[[IMG]http://img683.imageshack.us/img683/1678/hddv.th.png[/IMG]]("http://img683.imageshack.us/i/hddv.png/")

I wanted to create NTFS partition from unallocated space but by my mistake that space is beyond extended partition. How can I add unallocated space to extended partition and then create NTFS partition without deleteing any partitions?

---

### Post by CatKiller on 2011-07-12
You need to make sda4 bigger. Make sure none of the partitions inside it are mounted (in particular, the swap partition) and then hit the Resize/Move button. Drag the right end of the partition (the box round all the other partitions) all the way to the right. Hit Apply and you should be done.

EDIT: Obviously, you can't do this from your normal Ubuntu environment because you're using those partitions to run everything. Boot from either the Ubuntu install CD or a [GParted CD]("http://gparted.sourceforge.net/livecd.php") and you should be fine. You'll probably still need to turn off swap.

---

### Post by pqwoerituytrueiwoq on 2011-07-12
you will need to use a live usb/cd

---

### Post by scathlock on 2011-07-12
> **CatKiller said:**
> You need to make sda4 bigger. Make sure none of the partitions inside it are mounted (in particular, the swap partition) and then hit the Resize/Move button. Drag the right end of the partition (the box round all the other partitions) all the way to the right. Hit Apply and you should be done.

EDIT: Obviously, you can't do this from your normal Ubuntu environment because you're using those partitions to run everything. Boot from either the Ubuntu install CD or a [GParted CD]("http://gparted.sourceforge.net/livecd.php") and you should be fine. You'll probably still need to turn off swap.

I can't - I've tried. Move/resize option in GParted is disabled. Of course partitions are unmounted.

---

### Post by CatKiller on 2011-07-12
> **scathlock said:**
>  Of course partitions are unmounted.

They're mounted in your screenshot.

---

### Post by scathlock on 2011-07-12
> **CatKiller said:**
> They're mounted in your screenshot.

Because I first make screenshot and then reboot and use LiveCD ;)

---

### Post by CatKiller on 2011-07-12
> **scathlock said:**
> Because I first make screenshot and then reboot and use LiveCD ;)

Fair enough.

I've only ever seen the Resize/Move option unavailable when a partition is mounted. I suspect swap, since it's generally automatically mounted for performance reasons.

```
sudo swapoff -a
```

(IIRC) should do it from an Ubuntu cd. Something similar if you're using the GParted cd.

---

### Post by scathlock on 2011-07-13
Ok, disabling swap works and I've succesfully resized partition. Thanks!

---

