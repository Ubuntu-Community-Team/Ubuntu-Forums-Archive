---
title: "Ownership of fat32 partition"
date: 2011-01-24
forum: General Help
---

### Post by connel on 2011-01-24
Hi. I just installed Ubuntu but forgot to automatically mount my fat32 partition I use to store files so they can be accessed on Windows and Ubuntu. I have edited my fstab using this guide:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

My partition is coming up automatically when I boot in the folder I wanted but I do not have write access :/ how abouts do I get full ownership or access to the folder? I'm guessing its a chmod command but I've looked online and I find it very confusing.

Thanks

---

### Post by lightningfox on 2011-01-24
Hi

Try the instructions on this webpage: 

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I hope it helps.

---

### Post by lukeiamyourfather on 2011-01-24
Either the options in the fstab don't allow writing or the permissions are not proper. Can you share the contents of the fstab and also the output of "ls -o" from the mount.

---

### Post by connel on 2011-01-24
My fstab file looks like this. The bottom line is the one I don't have write access to:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=26220c4f-bdba-48e4-b8ba-1da8a2edc7ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2e7aa341-468e-42f2-ac78-cda423b4b4ae none            swap    sw              0       0
UUID=FEFC-0092	/shared		vfat
```

Here is the command you asked for:
```
connel@connel-desktop:/shared$ cd /shared
connel@connel-desktop:/shared$ ls -o
total 16
drwxr-xr-x 4 root 16384 2010-12-07 18:59 Users

```

Usually when I specify the partitioning manually when installing Ubuntu I use this folder for my fat partition but I guess I'm automatically given write access to it by the installer.

---

### Post by connel on 2011-01-24
Also I just tried the following command (taken from the site lightningfox sent me):

```
sudo chown -R connel:connel /shared
```

But it lists loads of files and says "Operation not permitted" after every file.

Thanks for all your help

---

### Post by CharlesA on 2011-01-24
FAT does not support linux style permissions. You can only change the owner/group/permissions of the folder where it is mounted.

---

### Post by psusi on 2011-01-24
FAT does not understand ownership and permissions, so the kernel has to fake it.  You need to specify the uid= and gid= mount options to tell it who it should pretend owns the files ( like your uid/gid ).

---

### Post by connel on 2011-01-24
> **CharlesA said:**
> FAT does not support linux style permissions. You can only change the owner/group/permissions of the folder where it is mounted.

That's what I thought... But I can't create new files in the /shared folder

---

### Post by connel on 2011-01-24
> **psusi said:**
> FAT does not understand ownership and permissions, so the kernel has to fake it.  You need to specify the uid= and gid= mount options to tell it who it should pretend owns the files ( like your uid/gid ).

Ah I see, so I have to edit fstab to state I have ownership.

I tired this but it didn't work:
UUID=FEFC-0092	/shared		vfat	uid=connel,gid=connel

Thanks for your help!

---

### Post by CharlesA on 2011-01-24
> **connel said:**
> That's what I thought... But I can't create new files in the /shared folder
If you wanted to you can just set the permissions of the mountpoint to 777, but it might be easier just to set the user in fstab.

---

### Post by Morbius1 on 2011-01-24
> UUID=FEFC-0092    /shared        vfatWhere's the rest of it?
It should look something like this:
>  UUID=FEFC-0092    /shared        vfat  utf8,umask=007,uid=1000,gid=46 0 2That will make you the owner of the mount point (uid=1000) and will give all other local login users (gid=46) read write access (umask=007).

If you want the /shared directory to be "shared" not only with other local login users but also network users via Samba I would change the umask to 000 and remove the gid part:
>  UUID=FEFC-0092    /shared        vfat  utf8,umask=000,uid=1000 0 2

---

### Post by sisco311 on 2011-01-24
EDIT:
Never mind. Morbius1 beat me to it.

[s]
You have to change the last line in your fstab to something like:
```
UUID=FEFC-0092  /shared  vfat  defaults,uid=**username**,gid=**groupname**,dmask=002,fmask=113  0  0
```

Where **username** is your login name and **groupname** is your primary login group.
[/s]

---

### Post by psusi on 2011-01-24
> **connel said:**
> Ah I see, so I have to edit fstab to state I have ownership? How do I do this? This wasn't on any of the how to's I read.


You need to add the uid=<yournamehere> option to the options column.

---

### Post by connel on 2011-01-24
Got it to work now, I was trying what you said and typing "sudo mount -a" but it still weren't working, turned out I needed a full reboot :) Thanks for all your help guys :)

---

### Post by victorhugo289 on 2011-01-24
The way I mount my NTFS and VFAt partition is this on Fstab:

---UUID=SD63-1DDA /media/automount1 vfat defaults,uid=1000,noatime 0 0
---UUID=D4A80DSA80E99DE /media/automount2 ntfs defaults,uid=1000,noatime 0 0

This way you can even delete files from the so-mounted partitions and the TRASH bin works :biggrin:

I got this info from he Ubuntu forums too, it's great.

---

