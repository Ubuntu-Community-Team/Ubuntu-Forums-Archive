---
title: "Odd directory permissions problem"
date: 2010-12-05
forum: General Help
---

### Post by Osedax on 2010-12-05
So, I've got a secondary hard drive mounted to a folder in my home directory, but for some reason it's listed as belonging to the root user. The permissions are configured like so: drwxr-xr-x, so I can't write files to the directory while logged in under my normal username. I tried fixing this with "chown", both sudo'd and while logged in as root, but it keeps telling me that the operation is not permitted. I tried using "chmod", and did not get an error, but the permissions did not get changed.
What gives?

Details that may be of use:
I'm running the 64 bit version of 6.10 (problem arose because I'm trying to upgrade, and need to copy all my stuff to that drive before installing 10.10)
The secondary drive is connected through a SATA II bus.
Drive is already formatted and has files on it, so it's not a hardware problem.

I apologize in advance if I've missed something totally obvious.

---

### Post by warfacegod on 2010-12-05
This is how I chown. It never fails me.

```
sudo chown -R username:usergroup /media/drivename
```

Of course, it helps if the proper drive is mounted.;)

---

### Post by Boondoklife on 2010-12-05
just out of curiosity, could you post the output of:
```

mount

```

---

### Post by sisco311 on 2010-12-05
What filesystem is on the drive? How did you mount it?

Please post the output of:
```
mount
```

---

### Post by Boondoklife on 2010-12-05
> **sisco311 said:**
> What filesystem is on the drive? How did you mount it?

Please post the output of:
```
mount
```

Jynx!

---

### Post by Osedax on 2010-12-05
> **Boondoklife said:**
> just out of curiosity, could you post the output of:
```

mount

```

it sez:
/dev/sda1 on /home/jack/barn type vfat (rw)

---

### Post by sisco311 on 2010-12-05
> **Osedax said:**
> it sez:
/dev/sda1 on /home/jack/barn type vfat (rw)

FAT and NTFS partitions do not support Unux/Linux file permissions. You have to set the ownership and permissions at mount time with the uid,dig,usmak.dmask,fmask mount options. 

Remount the partition:
```
sudo mount -o remount,defaults,uid=jack,gid=jack,dmask=002,fmask=113 /home/jack/barn
```

---

### Post by Osedax on 2010-12-05
> **sisco311 said:**
> FAT and NTFS partitions do not support Unux/Linux file permissions. You have to set the ownership and permissions at mount time with the uid,dig,usmak.dmask,fmask mount options. 

Remount the partition:
```
sudo mount -o remount,defaults,uid=jack,gid=jack,dmask=002,fmask=113 /home/jack/barn
```

Didn't work. Command seemed to go through like normal, but the directory and permissions are all the same.

---

### Post by sisco311 on 2010-12-05
Try unmounting it first:
```
sudo umount /home/jack/barn
sudo mount -o defaults,uid=**jack**,gid=**jack**,dmask=002,fmask=113 /dev/sda1 /home/jack/barn
```

Maybe the remount option does not work with FAT partitions. I don't have one, so I can't test it.

EDIT: Oh, and replace **jack** with your user name, I assumed it's jack from the name of your home directory.

---

### Post by Osedax on 2010-12-05
> **sisco311 said:**
> Try unmounting it first:
```
sudo umount /home/jack/barn
sudo mount -o defaults,uid=**jack**,gid=**jack**,dmask=002,fmask=113 /dev/sda1 /home/jack/barn
```

Maybe the remount option does not work with FAT partitions. I don't have one, so I can't test it.

EDIT: Oh, and replace **jack** with your user name, I assumed it's jack from the name of your home directory.

That worked! Thank you!

---

### Post by sisco311 on 2010-12-05
> **Osedax said:**
> That worked! Thank you!

You're welcome!

---

