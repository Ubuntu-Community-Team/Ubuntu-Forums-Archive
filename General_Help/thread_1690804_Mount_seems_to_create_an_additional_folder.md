---
title: "Mount seems to create an additional folder"
date: 2011-02-19
forum: General Help
---

### Post by delpi767 on 2011-02-19
I am trying to mount the device sdb in the folder /mirror so I issue the command 

dmd@dolly:/$ sudo mount /dev/sdb mirror.

I would now expect to see the contents of sdb in /mirror

but instead of mounting in /mirror it is being mounted in /mirror/mirror and the second mirror folder is created during the mount 

dmd@dolly:/mirror$ ls - returns no results

I then say dmd@dolly:/$ sudo mount /dev/sdb mirror
and look for my mounted files in /mirror

and I see this

dmd@dolly:/$ cd mirror
dmd@dolly:/mirror$ ls
lost+found  mirror  (an additional mirror folder)

mount says
/dev/sdb on /mirror type ext4 (rw)


I'm sure I'm just doing something goofy or otherwise have screwed things up but I've tried this several times with re-boots in the middle and wherever I choose to mount sdb it ends up being mounted one level lower in a folder of the same name. 

I'm new, I'm learning, and I'm stumped.

Thanks,

Mac

---

### Post by jquis8411 on 2011-02-19
Maybe I am missing the point here but did you try making the mount point first, then mounting the drive in it? 
```
 mkdir /home/mirror    
```  
```
 mount -t fstype /dev/sdb  /home/mirror 
```

---

### Post by kiyop on 2011-02-19
I suggest you to use absolute path, instead of relative path.
First, unmount.
```
sudo umount -l /dev/sdb
```

Check if /dev/sdb is mounted or not.
```
mount | grep /dev/sdb
```

If mounted, unmount again.

If /dev/sdb is not mounted, mount /dev/sdb as ext4
```
sudo mount -t ext4 /dev/sdb /mirror -o rw
```

Usually, partition device name ends with number. For example, "/dev/sdb1".

Is the device USB flash memory?

---

### Post by delpi767 on 2011-02-19
> **kiyop said:**
> I suggest you to use absolute path, instead of relative path.
First, unmount.
```
sudo umount -l /dev/sdb
```

Check if /dev/sdb is mounted or not.
```
mount | grep /dev/sdb
```

If mounted, unmount again.

If /dev/sdb is not mounted, mount /dev/sdb as ext4
```
sudo mount -t ext4 /dev/sdb /mirror -o rw
```

Usually, partition device name ends with number. For example, "/dev/sdb1".

Is the device USB flash memory?

Nope, the device is a SATA HDD

I have tried mounting from both absolute and relative paths with the same results.

Also, I am mounting the entire drive as it has only one partition that is the maximum size of the drive.  Should I still be mounting the partition?

Thanks,

Mac

---

### Post by delpi767 on 2011-02-19
> **jquis8411 said:**
> Maybe I am missing the point here but did you try making the mount point first, then mounting the drive in it? 
```
 mkdir /home/mirror    
```  
```
 mount -t fstype /dev/sdb  /home/mirror 
```

Yes, I have created the mount point first.  If I don't, mount complains with a message that says something like "Mount point does not exist".

I've tried every combination I can think of and the results are always that the filesystem is mounted at mountpoint/mountpoint

Thanks,

Mac

---

### Post by kiyop on 2011-02-20
> **delpi767 said:**
> Nope, the device is a SATA HDD

I have tried mounting from both absolute and relative paths with the same results.

Also, I am mounting the entire drive as it has only one partition that is the maximum size of the drive.  Should I still be mounting the partition?
If I were you, I would partition the SATA HDD and would not use entire drive.
Do as you like.

---

### Post by kiyop on 2011-02-20
Is there any entry relating "mirror" in /etc/fstab?

Is there any directory named "mirror" in /dev/sdb?

What is the result of 
$ ls -la / | grep mirror

Is there any symbolic link concerning "mirror" ?

Again, I should notice that I would use absolute path.

---

### Post by aeiah on 2011-02-20
/dev/sdb is your sata harddrive device. there will be one or more partitions in this, and that's what you should be mounting. maybe that's why its doing something strange

try mounting /dev/sdb1 instead (your first partition on the sdb device)

---

### Post by kiyop on 2011-02-20
> **delpi767 said:**
> 
I then say dmd@dolly:/$ sudo mount /dev/sdb mirror
and look for my mounted files in /mirror

and I see this

dmd@dolly:/$ cd mirror
dmd@dolly:/mirror$ ls
lost+found  mirror  (an additional mirror folder)


Some USB flash medias I used had only /dev/sdb or so, without any partition.

Please execute the following command in the terminal after booting with LiveCD.

```
sudo parted -l
sudo fdisk -l
sudo blkid
```

---

### Post by delpi767 on 2011-02-23
Thanks to one and all for your suggestions.  I was never quite able to resolve this.

As it was one of my first Ubuntu installs and I was/am still learning the finer points, I simply did a reinstall (good practice) and now everything works just fine.

Something was screwed up and I never like to leave a fresh install in less that perfect condition.

Once again.  Thanks everyone for your suggestions.

Mac

---

