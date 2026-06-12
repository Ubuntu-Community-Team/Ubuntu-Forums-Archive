---
title: "two swap partitions?"
date: 2009-08-23
forum: General Help
---

### Post by stuart.reinke on 2009-08-23
I have two partitions on my hard drive. 

One is 20 GiB with Hardy It has a 1 GiB swap

The other is 5 GiB with Karmic. It has 275.52 MiB

My question is: Can I have both OS use the same swap? Thereby freeing up the 275 MiB for Karmic to use. 

If so, How?

If not, Why?

It seems the more I learn the more questions I find. Anyway, thanks for any answers you have for me.

Stu

---

### Post by drs305 on 2009-08-23
Yes, you can use one swap for both. Delete the one and then make sure both /etc/fstab files point to the correct swap partition.

You should also make sure the following file points to the swap's correct UUID:
```

sudo swapoff -a
sudo blkid | grep "swap"
gksudo gedit /etc/initramfs-tools/conf.d/resume
sudo update-initramfs -uk all
sudo swapon -a

```

---

### Post by stuart.reinke on 2009-08-23
> **drs305 said:**
> Yes, you can use one swap for both. Delete the one and then make sure both /etc/fstab files point to the correct swap partition.

You should also make sure the following file points to the swap's correct UUID:
```

sudo swapoff -a
sudo blkid | grep "swap"
gksudo gedit /etc/initramfs-tools/conf.d/resume
sudo update-initramfs -uk all
sudo swapon -a

```

I want to keep the 1 GiB swap on the Hardy Partition. Which OS do I need to use to enter the above code?

---

### Post by drs305 on 2009-08-23
> **stuart.reinke said:**
> I want to keep the 1 GiB swap on the Hardy Partition. Which OS do I need to use to enter the above code?

If you want to delete the Karmic swap partition (after unmounting swap), delete it and then run those commands from within Karmic and point everything to the current Hardy swap partition.

---

### Post by stuart.reinke on 2009-08-23
Just one more question before I attempt this.

Hardy refers to my hard drive as /hda.
Karmic refers to it as /sda

will this make any difference or cause any problems?

thanks so much for your help drs305.

---

### Post by drs305 on 2009-08-23
> **stuart.reinke said:**
> Just one more question before I attempt this.

Hardy refers to my hard drive as /hda.
Karmic refers to it as /sda

will this make any difference or cause any problems?

thanks so much for your help drs305.

No it won't - since the swaps are now identified by UUIDs.

Even if the swaps don't initially work you probably wouldn't notice the difference and you could easily make any necessary corrections. Once you have performed all the operations, you can see if swap is working with:
```

free -m

```
You may see a 0 but they won't all be zeros. Here is what mine looks like:
> Swap:         4102          0       4102

---

### Post by stuart.reinke on 2009-08-23
Thanks again for your help. 

I need to shut down for the night so I'll give it a try tomorrow.

---

### Post by stuart.reinke on 2009-08-24
Hope you're still there drs305, something isn't working right. When I try to turn the swap on, I get the following message...

> stuart@stuart-laptop:~$ sudo swapon -a
swapon: cannot find the device for UUID=ece2249b-0cb3-4ed8-87a0-12b1d891656c
stuart@stuart-laptop:~$ gksudo gedit /etc/initramfs-tools/conf.d/resume
stuart@stuart-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           354        330         23          0         17        130
-/+ buffers/cache:        183        171
Swap:            0          0          0
stuart@stuart-laptop:~$ 

It is still looking for the old swap partition that I deleted.

The /etc/intramfs-tools/conf.d file shows the correct UUID

> RESUME=UUID=e7107941-19ff-436b-99fd-b7459297ddba


---

### Post by drs305 on 2009-08-24
Stuart,

You now have one swap partition, I presume, 
UUID=e7107941-19ff-436b-99fd-b7459297ddba 

In the fstab files for both your systems, you should have a setting for the swap file:
> UUID=e7107941-19ff-436b-99fd-b7459297ddba  none swap  sw  0 0
  
You will have to check this by opening the /etc/fstab file in each system partition, either by checking /etc/fstab while that system is running or by mounting the non-operating system and then checking /mountpoint/etc/fstab. The same goes for checking the /etc/initramfs-tools/conf.d/resume files.

Assuming you deleted the extra swap file, you should **not** have any entry in either of your fstab files for 
UUID=ece2249b-0cb3-4ed8-87a0-12b1d891656c

If you run "sudo blkid" you should see only one swap listing, with XX being the drive letter and number:
> /dev/sdXX: UUID="e7107941-19ff-436b-99fd-b7459297ddba" TYPE="swap"

---

### Post by stuart.reinke on 2009-08-25
drs305

Thanks for the reply, and all the help. Unfortunately I goofed up when trying to create another primary partition and now I have to reinstall Karmic and start from scratch.  

I think I have all the pieces to the puzzle I need to make them share the same swap file.  

Thanks again.

---

