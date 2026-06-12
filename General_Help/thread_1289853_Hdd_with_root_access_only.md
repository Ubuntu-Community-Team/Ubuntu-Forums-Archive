---
title: "Hdd with root access only"
date: 2009-10-12
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-10-12
I recently backed up my / and /home to a 10 gig hdd and decided to copy a few folders to it as well. Since I reinstalled and mount that disk I have no permissions to it. I ran "sudo nautilus --no-desktop" but this is quite a process for all the files I have there.How can I change permissions On the disk its self?

---

### Post by Giblet5 on 2009-10-12
Where is the 10G drive mounted now?

Let's assume it's mounted at /mnt and that you have folders like

/mnt/etc
/mnt/home

etc.

I presume that you want to access /mnt/home/YourOldUserName, right?

That would be: ```
sudo chown -R $LOGNAME:$LOGNAME /mnt/home/YourOldUserName
```

Now you own all of those files and folders and can move them around, delete them, etc.

Does this help?

---

### Post by scouser73 on 2009-10-12
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by Feelin_froggy8877 on 2009-10-12
"nautilus --no-desktop" Ran that, but I have to many sub dir's for that. But tried it again and the owner is not root no more. "488 - user #488"??? now shows as owner. And get error trying to change owner "read only file system"

---

### Post by Feelin_froggy8877 on 2009-10-13
Still no luck w/ this. I had checked the disk in gparted but it is showing the disk as "unallocated"? It is mounted on /media/storage, I can brouse the folders but cannot open any of the pics. Is the data on this disk a loss?

---

### Post by bodhi.zazen on 2009-10-13
Either your disk is corrupted or perhaps is this a NTFS or FAT partition ?

NTFS and FAT partitions have permissions set at the time of mounting and can not be changed with chown or chmod.

---

### Post by Feelin_froggy8877 on 2009-10-13
No, its ext3. What a bummer. Alot of stuff on there I was backing up, for the disk to fail.

---

### Post by bodhi.zazen on 2009-10-13
> **Feelin_froggy8877 said:**
> No, its ext3. What a bummer. Alot of stuff on there I was backing up, for the disk to fail.

Try testdisk and photorec, they are in the repositories (apt-get install testdisk).

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Feelin_froggy8877 on 2009-10-13
Giving it a try. As far as the partition type should I use the Solaris? (Linux)

Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection

---

### Post by bodhi.zazen on 2009-10-13
You should use "Intel/PC"

there are fairly complete instructions on the test disk site I gave you earlier.

---

