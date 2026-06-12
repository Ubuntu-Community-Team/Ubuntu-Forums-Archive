---
title: "Unable to find partition"
date: 2010-04-04
forum: General Help
---

### Post by Nevyn on 2010-04-04
My recent setup was 32-bits Ubuntu 9.10 with / on a 20 gb partition and /home on a different partition on the same physical hard drive. Two days ago the system suddenly froze while idle. I rebooted and got the error message at start up that the system was unable to mount every unit that was listed in fstab. 

I troubleshooted by using a Live CD but could not find any reason to why i _could not find the home partition_. It lists in gparted but not in terminal using df.

I've made another install on a different physical hard drive and don't care about the previous installs, but I would like to get the data out of the home partition. 
If anybody have any idea what to try to access it, I'd really appreciate it. Thanks!

---

### Post by conradin on 2010-04-04
does the OS see the partition in question?
have you tried to force it to mount?
perhaps you can se e2fsck to repair the partition

---

### Post by Nevyn on 2010-04-04
No, the new install can not see the partition, except when using gparted.
Since it can't be seen, wouldn't know how to try to force mount it (since there is "nothing" to mount).
I'll read up on e3fsck.

---

### Post by conradin on 2010-04-04
what does Gparted show you?

---

### Post by garvinrick4 on 2010-04-04
In gparted does it show the label as home. If not label it home.
Right click on partition and choose label. label it and apply it.

sudo mkdir /media/home

sudo mount /dev/sdax /media/home


sdax= whatever your home partition is.

home= your label

sudo blkid (will show your labels second letter is small L)

---

### Post by Nevyn on 2010-04-04
Gparted shows it as a partition as any other (/dev/sdc3, ext3, size and used, no label, no flag).

I have used gparted to put new labels on existing partitions before and doing so caused me to lose all the data on that partition (I eventually got it back using a recovery program). 
So I'd rather not do that.

I don't need to mount it as home, I only need to mount it so I can extract the data.

---

### Post by srs5694 on 2010-04-04
> **Nevyn said:**
> I don't need to mount it as home, I only need to mount it so I can extract the data.

For that, don't mess with any complex recovery procedures unless you can't mount it like this:

```

sudo mount /dev/sdc3 /mount/point

```

Substitute any convenient empty directory for "/mount/point". Your files should appear there. If this doesn't work, post back with details (error messages, symptoms, etc.).

---

### Post by garvinrick4 on 2010-04-04
If you cannot mount it in a live CD how can you recover?

---

### Post by conradin on 2010-04-04
> **Nevyn said:**
> Gparted shows it as a partition as any other (/dev/sdc3, ext3, size and used, no label, no flag).


I don't need to mount it as home, I only need to mount it so I can extract the data.

mounting the device as "home" in /media/home was just an example, as long as the directory exists, you may mount a filesystem to it. For example:
```

sudo mkdir /mnt/happyBunny
sudo mount -t ext3 /dev/sdc3 /mnt/happyBunny -o force

```
here, you have your former home partition mounted to the /mnt/happyBunny directory unrelated to any other home directory. The -t option specifies the File System type. -o force forces the filesystem to mount. 

if this doesnt return an error, 
```

cd /mnt/happyBunny

ls 

```

to view files. If an error returns send us that.

---

### Post by Nevyn on 2010-04-05
I didn't think it was mountable since the command df didn't show the partition. Even though I tried it, it was the -t option that was missing.
Thanks for the help guys! I now have it mounted.

---

