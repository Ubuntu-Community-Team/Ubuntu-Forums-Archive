---
title: "Root permissions for different Partition"
date: 2010-10-03
forum: General Help
---

### Post by sid.mallya on 2010-10-03
Hey .. I reinstalled Ubuntu 10.04 on partition /dev/sda1 because the GUI had gone haywire. Anyway, to back up my data I created a separate partition, /dev/sda3 and used the "do not use this partition" option whilst installed the OS.

Now the OS is working fine and all, but I cannot r-w-x certain folders in this sda3 partition. The only way for me to use the partition's files/folders is 

```
gksudo nautilus
```

I tried using 

```
sudo chmod u+x /media/xxxxx
```

It executes but the partition still functions the same way as earlier. What do I do ?

---

### Post by sikander3786 on 2010-10-03
Try this.

```
sudo chown <username>:<username> /place/to/mount
```

---

### Post by sid.mallya on 2010-10-03
@Sikander,

Hey .. I am sorry, I am new to Linux and do get confused with commands at times.

I tried "sudo chown root /media/xxxx" ..

Should I try changing the mount point from /media to /mnt ? Also, I don't get the funda of "username:username" 

:s

---

### Post by sikander3786 on 2010-10-03
**You** want to own it not root.

```
sudo chown <username>:<username> /place/to/mount
```

Replace <username> with your username and /place/to/mount with /media/xxxx, in my case,

```
sudo chown sikander:sikander /media/my_partition
```

---

### Post by sid.mallya on 2010-10-03
Lol ! Okay .. I tried it. Anyway, besides the new "lock" symbol on every folder, everything is still the same. :))

---

### Post by sid.mallya on 2010-10-03
This is the error I get. =/

---

### Post by sikander3786 on 2010-10-03
What is the output of

```
ls -l /media/xxxx
```

Where xxxx stands for problematic partition.

---

### Post by Sidewinder1 on 2010-10-03
Ok, I'll take a crack at this. Assuming your ubuntu, login, username is:
sid.mallya...
```
sudo chown -R sid.mallya:sid.mallya /media/sda3
```
If that does not work, you could try:

```
sudo chown -R sid.mallya:sid.mallya /dev/sda3
```

HTH and it works :-)

Side

---

### Post by sid.mallya on 2010-10-03
Oh .. I tried the -R thingy. It worked. Thanks ! :)

---

