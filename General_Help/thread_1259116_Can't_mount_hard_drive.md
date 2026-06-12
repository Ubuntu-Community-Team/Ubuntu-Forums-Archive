---
title: "Can't mount hard drive"
date: 2009-09-05
forum: General Help
---

### Post by brnat on 2009-09-05
I've got a pc running Jaunty as my backup server, and I have three hard drives in the box. Before today, I could mount all three, no problem.

Today I fdisk'd the second and third hard drives (sdb and sdc), and I set the partition type to fd, so I could use mdadm and set them up in a raid0. I actually did get the raid array set up, but I did something stupid and had to delete the array.

Now, when I try to do -anything- with sdc I get "/dev/sdc1 already mounted or /dev/sdc busy"

I even tried to do mount /dev/sdc1 /dev/sdc -o force, and it gave me the same message.

No matter what I do, I get the same error. I've re-partitioned it, restared the computer countless times... What can I do?

---

### Post by ckonestroh on 2009-09-06
Some hard drives have software to do reformatting to hard drive requires download there software to reformat hard drives....

Had this problem years ago with a hard drive had to run there software in order to reformat drive correctly....


Sorry I worked on over 2000 + computers... Not sure what type of drive it was..... 

Also check your bios to see if the drive is showing up... make sure it is set for slave not master....


Also why I'm at it you did take that jumper out of reformatting position on the back of the hard drive????????

---

### Post by brnat on 2009-09-06
All three drives are the same model.

The only jumpers they have are for master/slave/cable select.

I tried to do mkfs on it, and I got:

```
/dev/sdc is apparently in use by the system; will not make a filesystem here!

```

Any ideas?

---

### Post by tgrimley on 2009-09-06
> **brnat said:**
> 
I even tried to do mount /dev/sdc1 /dev/sdc -o force, and it gave me the same message.

That command doesn't make any sense.  You need to create a mount point on the file system and then mount there..

---

### Post by jobst on 2009-09-07
> **brnat said:**
> I've got a pc running Jaunty as my backup server, and I have three hard drives in the box. Before today, I could mount all three, no problem.

Today I fdisk'd the second and third hard drives (sdb and sdc), and I set the partition type to fd, so I could use mdadm and set them up in a raid0. I actually did get the raid array set up, but I did something stupid and had to delete the array.

Now, when I try to do -anything- with sdc I get "/dev/sdc1 already mounted or /dev/sdc busy"

I even tried to do mount /dev/sdc1 /dev/sdc -o force, and it gave me the same message.

No matter what I do, I get the same error. I've re-partitioned it, restared the computer countless times... What can I do?

Check:

[LIST=1]
[*]open a terminal and type "mount", do you see the drives mounted?
[*]go into fstab and check whether they are in there (maybe a "md0")
[/LIST]
You can unmount the drives by finding the mount point (using mount and/or df).
If they are mounted as "mdX" make sure you delete all the arrays using "mdadm".

Remember once you have specified "mdadm --create ..." and you reboot with the drives attached they will be known as an array.

so delete "/etc/mdadm.conf", delete the entries in fstab and delete the arrays.

jobst

---

