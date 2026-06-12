---
title: "mount command help?"
date: 2010-10-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-10-10
i want to mount my partition that has my Virtual machines when i open VirtualBox OSE
i was goin to make a 2 line sh file but i do not know the command to mount the NTFS partition
label=VirtualBoxes uuid=341EB25C353F6DC0
i wanted to mount it the same way it does  by clicking it under places (just without the folder opening)
any ideas?

---

### Post by pqwoerituytrueiwoq on 2010-10-11
you are kidding no reply
i have tryed 
mount -U 341EB25C353F6DC0
mount: no such partition found
also tryed 
mount /dev/sda6
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab

---

### Post by dino99 on 2010-10-11
no need to use virtualbox to read/write directly from ubuntu: ntfsprogs & ntfs-3g does the job

---

### Post by pqwoerituytrueiwoq on 2010-10-11
i am not using virtual box to read/write an ntfs partition just saying my vdi is no a ntfs partition

i just forget to mount the partition before i open virtual box and it gives me an error saying directory does not exist
so i wanted to make short script to mount the partition then open VB and maybe then unmount the partition when i close VB
i keep my vdi files on a separate partition
just to keep 10-20gb files out of my way

---

### Post by Morbius1 on 2010-10-11
Why not have the ntfs partition mount automatically at boot. That way it's always available and the system will do an unmount for you when you shut down?

It's relatively easy and you may have given us all the information we require. For example:

Make a permanent mount point:
```
sudo mkdir /media/VBox
```Edit fstab as root:
```
gksu gedit /etc/fstab
```Add the following line at the end of fstab:
```
UUID=341EB25C353F6DC0 /media/VBox ntfs defaults,nls=utf8,uid=1000 0 0
```[COLOR=Blue]*I'm assuming that's the correct uuid number for your partition.*[/COLOR]

If you have the partition currently mounted then unmount it and run the following command:
```
sudo mount -a
```Now see if you can access your /media/VBox mount point.

If everything works as you want it to then the next time you boot it will already be mounted.

---

### Post by pqwoerituytrueiwoq on 2010-10-11
not quite what i wanted i just wanted a mount command i can use without being root
i want to mount a partition via script
i do not want it to always be mounted i like a clean desktop

---

### Post by Morbius1 on 2010-10-12
> **pqwoerituytrueiwoq said:**
> i do not want it to always be mounted i like a clean desktop
Having a permanent mount has nothing to do with a clean desktop. You have a permanent mount of your root directory yet you have no desktop icon. You will only get a desktop icon if your mount point is located in /media or /home/user_name. So just change the mount point:

Change this:
> sudo mkdir /**[COLOR=Blue]media[/COLOR]**/VBox
UUID=341EB25C353F6DC0 /**[COLOR=Blue]media[/COLOR]**/VBox ntfs defaults,nls=utf8,uid=1000 0 0To this:
> sudo mkdir /**[COLOR=Blue]mnt[/COLOR]**/VBox
UUID=341EB25C353F6DC0 /**[COLOR=Blue]mnt[/COLOR]**/VBox ntfs defaults,nls=utf8,uid=1000 0 0

---

### Post by pqwoerituytrueiwoq on 2010-10-12
thanks

---

