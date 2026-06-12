---
title: "how can I get Trashcan in second partition"
date: 2012-01-21
forum: General Help
---

### Post by sudodus on 2012-01-21
I have a running Ubuntu 10.04 LTS system, but I think that the question is relevant for all variants.

In my second partition, I have multimedia data. It is mounted via the following line(s) in [FONT="Courier New"][SIZE="3"]/etc/fstab[/SIZE][/FONT]
```
# /dev/sda2
UUID=d3f3f4a3-3d6e-4e4f-8e1a-c2f0de792f90 /media/multimed-2     ext3    defaults 0       2
```

My problem is that there is no trashcan, so that when I delete using the file browser Nautilus, it deletes the files definitely at once. In my system partition I have a trashcan , and if I mount a USB drive (disk or flash), it will be mounted in such a way that I can delete to the trashcan, and recover the file easily if I made a mistake.

Can you help me get a trashcan also in my second partition? I'll post more info about the drive and partition if you need it.

---

### Post by carl4926 on 2012-01-21
Rather than defaults
Would using
```
acl,user_xattr        1 2
```make any difference
So long as you make yourself owner of said dir

---

### Post by sudodus on 2012-01-21
> **carl4926 said:**
> Rather than defaults
Would using
```
acl,user_xattr        1 2
```make any difference
So long as you make yourself owner of said dir
Thanks Carl,

Do you mean like this?
```
UUID=d3f3f4a3-3d6e-4e4f-8e1a-c2f0de792f90 /media/multimed-2     ext3    defaults,acl,user_xattr        1 2
``` and what does it mean?

---

### Post by drs305 on 2012-01-21
Here are a couple of things to try. I can't gurantee they will solve your issue but they might.

Are you the owner of the /media/multimed-2 folder? If not, *with the partition unmounted*, run:
```

sudo umount /media/multimed-2
sudo chown $USER: /media/multimed-2
sudo mount -a  
```
I think that would direct future deleted files to your Trash bin.

If not, you could try creating a Trash bin in the folder. Assuming you are user ID 1000:```

[s]touch /media/multimed-2/.Trash-1000[/s]
mkdir /media/multimed-2/.Trash-1000
```

---

### Post by carl4926 on 2012-01-21
> **drs305 said:**
> Here are a couple of things to try. I can't gurantee they will solve your issue but they might.

Are you the owner of the /media/multimed-2 folder? If not, *with the partition unmounted*, run:
```

sudo umount /media/multimed-2
sudo chown $USER: /media/multimed-2
sudo mount -a  
```I think that would direct future deleted files to your Trash bin.

If not, you could try creating a Trash bin in the folder. Assuming you are user ID 1000:```

touch /media/multimed-2/.Trash-1000
```

@drs305
Might he need use -R on chown

---

### Post by sudodus on 2012-01-21
> **drs305 said:**
> Here are a couple of things to try. I can't gurantee they will solve your issue but they might.

Are you the owner of the /media/multimed-2 folder? If not, *with the partition unmounted*, run:
```

sudo umount /media/multimed-2
sudo chown $USER: /media/multimed-2
sudo mount -a  
```
I think that would direct future deleted files to your Trash bin.

If not, you could try creating a Trash bin in the folder. Assuming you are user ID 1000:```

touch /media/multimed-2/.Trash-1000
```

Thank you drs305,

No, root owns /media/multimed-2. I have tried what you suggest but it does not work. After unmounting I can change owner (I tested it with ls -l), but after remounting, the ownership goes back to root, so I cannot create the trashcan (as user 1000).

---

### Post by sudodus on 2012-01-21
> **carl4926 said:**
> @drs305
Might he need use -R on chown
I guess after re-mounting? Otherwise it won't see the subdirectories.

---

### Post by drs305 on 2012-01-21
Using -R after mounting the partition will change the ownership of *all* the files mounted thereon to you. If that is ok, use the -R switch with the chown command. Just be careful you run the command only on the correct mountpoint or you can seriously damage your system.

As *carl4926* suggested, you can/should probably use the -R switch initially, which was an oversight. Thanks carl4926.

---

### Post by sudodus on 2012-01-21
I tried again without unmounting, also this time changing owner without recursing into subdirectories. Now I could create .Trash-1000. But it did not work until I made it a directory (touch created a file) so instead I used the following commands

```
sudo chown $USER: /media/multimed-2
[COLOR="Red"]mkdir /media/multimed-2/.Trash-1000/
chmod ug+w /media/multimed-2/.Trash-1000[/COLOR]
```

Thank you for leading me to the solution :KS

Now I have a Trashcan in the second partition (at least for my own user). I also noticed that there is one for root.

---

### Post by drs305 on 2012-01-21
> **sudodus said:**
> I tried again without unmounting, also this time changing owner without recursing into subdirectories. Now I could create .Trash-1000. But it did not work until I made it a directory (touch created a file) so instead I used the following commands

```
sudo chown $USER: /media/multimed-2
[COLOR="Red"]mkdir /media/multimed-2/.Trash-1000/
chmod ug+w /media/multimed-2/.Trash-1000[/COLOR]
```

Thank you for leading me to the solution :KS

Now I have a Trashcan in the second partition (at least for my own user). I also noticed that there is one for root.

Glad you were able to figure it out. It's still a couple of hours before my wakeup time, and it's showing a bit.  ;-)

Happy Ubuntu-ing !

---

