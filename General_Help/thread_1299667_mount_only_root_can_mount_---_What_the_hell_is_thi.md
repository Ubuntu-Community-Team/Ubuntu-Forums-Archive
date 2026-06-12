---
title: "mount: only root can mount --- What the hell is this?"
date: 2009-10-24
forum: General Help
---

### Post by baskar007 on 2009-10-24
iam using ubuntu9.04,
recently i format my HDD(ntfs) to ext3 with Gpart.

now i can't access my harddisk(drive)
dolphin give an error look like this
```
mount: only root can mount
```

i have tried chown,chmod to change permissions to this drive, but still i can't access that drive?

help me friend
[RIGHT]-baskar[/RIGHT]

---

### Post by scragar on 2009-10-24
You could make it automount using fstab, or you could try using the -o option and seeing if that accepts the "user" option to let you mount it as a normal user(unlikely, but worth a try).

---

### Post by baskar007 on 2009-10-24
> **scragar said:**
> You could make it automount using fstab, or you could try using the -o option and seeing if that accepts the "user" option to let you mount it as a normal user(unlikely, but worth a try).
i can't get you,
Where i can use this   -o option

---

### Post by nothingspecial on 2009-10-24
Try ```
sudo mkdir /media/drive
```

```
sudo mount -t ext3 /dev/sdb1/ /media/drive
```

substitute /dev/sdb1 for whatever your drive has been given.

Check by typing ```
sudo fdisk -l
``` 

And if you`ve got a minute ...... vote for the washing machine:)

---

### Post by prshah on 2009-10-24
> **baskar007 said:**
> 
i have tried chown,chmod to change permissions to this drive, but still i can't access that drive?

If you want the partition to be automatically (statically) mounted, you need to add the specific information to the /etc/fstab file. For example, you need to add an entry such as ```
# /dev/sda6
[color=red]UUID=AB707BCE707F8DE8[/color] [color=blue]/media/sda6[/color]     ext3    [color=green]defaults,relatime,auto[/color] 0       1
```

In the above example (your details will differ), you can find out the correct UUID for your partition (the part in red) using the command```
sudo blkid /dev/sda6
``` (Replace sda6 with the actual partition device ID in your case).

You should also create the mount point (the part in blue)```
sudo mkdir /media/sda6
sudo chown root:plugdev /media/sda6

```

Note that directories / files subsequently created on the mounted drive will carry ownership / permissions relevant to the user.

Post back if you need more details. A look at your current partition/hdd structure will be helpful; give the following commands from a terminal (Applications-Accessories-Terminal)```
sudo fdisk -l
mount
```

Also, as an aside: I'd suggest you mind your language on public forums such as these; you may well end up with an infraction for inappropriate language.

---

### Post by baskar007 on 2009-10-24
> **prshah said:**
> If you want the partition to be automatically (statically) mounted, you need to add the specific information to the /etc/fstab file. For example, you need to add an entry such as ```
# /dev/sda6
[color=red]UUID=AB707BCE707F8DE8[/color] [color=blue]/media/sda6[/color]     ext3    [color=green]defaults,relatime,auto[/color] 0       1
```

In the above example (your details will differ), you can find out the correct UUID for your partition (the part in red) using the command```
sudo blkid /dev/sda6
``` (Replace sda6 with the actual partition device ID in your case).

You should also create the mount point (the part in blue)```
sudo mkdir /media/sda6
sudo chown root:plugdev /media/sda6

```

Note that directories / files subsequently created on the mounted drive will carry ownership / permissions relevant to the user.

Post back if you need more details. A look at your current partition/hdd structure will be helpful; give the following commands from a terminal (Applications-Accessories-Terminal)```
sudo fdisk -l
mount
```

Also, as an aside: I'd suggest you mind your language on public forums such as these; you may well end up with an infraction for inappropriate language.
THankyou

---

### Post by dez93_2000 on 2012-11-02
Thank you from me too.

An aside: I've been a fan of ubuntu/linux for a while, and since being given a win7 laptop for work it's justified my decision somewhat, but it's things like this which I couldn't begin to explain to fans of other OSs. Look at prshah's post, minus the quote: clearly written, explaining the various highly technical steps one must take so you can look at stuff on your external hard drive (assumes one knows how to edit files as root. and how to GET to fstab in the first place - neither of which are super simple).
In short: I love linux for its open, dependable, flexible nature. But i hate it for the times it makes simple tasks so complicated one starts thinking "computers were supposed to make our lives SIMPLER".

---

### Post by wildmanne39 on 2012-11-02
Old thread closed.

---

