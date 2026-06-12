---
title: "is there a way to resize the root partition without using a livecd?"
date: 2010-02-07
forum: General Help
---

### Post by Miki800 on 2010-02-07
that is - while using it or in any way that does not include restarting the pc?

I don't really have high hopes for this or anything, it's just that if there is a way I think it would be interesting enough for me to want to know :)

---

### Post by Mark Phelps on 2010-02-07
Not aware of any Linux utilities that will allow you to resize a partition while actively using it.

You could TRY launching Partition Editor and then manually unmounting the root partition -- but my guess (having never done this) is that your session would end -- and you'd have to reboot.

---

### Post by Miki800 on 2010-02-07
yeah, I guess you are absolutely right.

how about un-mounting the swap partition, enlarging it and then remount it?
shouldn't cause me any trouble right?

---

### Post by tom.swartz07 on 2010-02-07
> **Miki800 said:**
> yeah, I guess you are absolutely right.

how about un-mounting the swap partition, enlarging it and then remount it?
shouldn't cause me any trouble right?

ehhhhh.... I really wouldnt suggest doing that. Although it might work, theres a possibility that it might cause some damage. The only safe way to change partitions is to boot to a LiveCD where none of the partitions are in use.

---

### Post by HermanAB on 2010-02-07
Yes, you can use swapoff and change the swap partition, if there is  free disk space next to it, which is unlikely. Typically, messing with the partitions is a good way to lose all your data...

---

### Post by bcbc on 2010-02-07
I've done it:

```

$ sudo swapoff -a
... resize
$ sudo /sbin/mkswap /dev/sdXY 
$ sudo swapon -a 

```

Update /etc/fstab and /etc/initramfs-tools/conf.d/resume (for hibernate assuming swap is >= size of RAM) with new UUID.
And 
```
$ sudo update-initramfs -u
```

---

### Post by sandkernel on 2010-02-07
> **Miki800 said:**
> yeah, I guess you are absolutely right.

how about un-mounting the swap partition, enlarging it and then remount it?
shouldn't cause me any trouble right?

unmounting swap should be a joke and in fact I did that a couple weeks ago. The default install gave me 4G swap which was overkill big time.

As root, just issue swapoff -a. Go into Gparted, delete it and re-create it. Note, you'll have to change the /etc/fstab entry so that it points to the right device.

---

### Post by Miki800 on 2010-03-19
by the way guys, I do not remember the program itself, maybe acronis or something else,

but in windows there is definitely a program which allows you to do this - resize the 'root' partition there which actively using it! :)

---

### Post by Compintuit on 2010-03-20
No, the partition is not enlarged then; on the next reboot, it is. Because of LiveCDs, there has been no need for this functionality on linux. 

I wonder if you could perhaps temporarily move / to ram, while using it. You could certainly edit your fstab, and instead of mounting / from disk, load it as a ramdisk. No changes would sync, though, after you changed the partition. Of course you'd need enough ram, also; swap should work too.

---

