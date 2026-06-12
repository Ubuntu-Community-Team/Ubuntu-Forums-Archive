---
title: "Mound 2nd HDD automatically"
date: 2009-09-11
forum: General Help
---

### Post by carlosgs91 on 2009-09-11
.

---

### Post by islander_810 on 2009-09-11
Hi, you can mount any and all the partitions you want by editing the /etc/fstab file

A sample line is given in the file itself. Read it and add the partition you want

---

### Post by dcstar on 2009-09-11
> **carlosgs91 said:**
> Hi, I have 1 HDD with 2 partitions and I'd like Ubuntu automatically mounted the 2nd HDD. I can mount it by doble-clicking on it but I want it automatically, there's any way?

I know that programming an script it'd be veary easy, for example this would work:

sudo mount -t ntfs-3g /dev/sda1 /home/carlos/Desktop/disk

But this work in the terminal and:

a) I've never done it before and I don't know how to set up a file that can be read with the terminal.
b) I'd like to know if there's another way to do this

Thanks!

Install the **pysdm** package, that will give you a GUI to mount it automatically.

---

### Post by ankspo71 on 2009-09-11
Hi,
"a) I've never done it before and I don't know how to set up a file that can be read with the terminal."

You can type this in the terminal to edit the fstab file:
```
sudo gedit /etc/fstab
```

I tried many times to mount my hdd automatically by editing the fstab file, but I couldn't get it to work. With the help of someone else here, I was able to find a way to do it by installing and working with pysdm. It will appear as "Storage Device Manager" in your system>administration menu. So I recommend pysdm too.

my settings are:
* The files system is mounted at boot-time
* Owner user of the filesystem UID = james
* Owner group of the filesystem = james

(*) this means checkbox. Replace james (my name) with your ubuntu username.

Hope this helps,
James.

---

### Post by carlosgs91 on 2009-09-11
.

---

### Post by ankspo71 on 2009-09-11
Thanks. It was the options part I had a hard time with. I was trying to set up my hard drive so that it wasn't all 'root' files and folders. Now it works like my home directory.

I'll show my fstab for others to see:
```
/dev/sdb1  /media/sdb1  vfat  uid=james,gid=james  0  0 
```

I'm glad you got it working.
James

---

