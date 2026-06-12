---
title: "How to change permissions in seperate partition?"
date: 2010-03-06
forum: General Help
---

### Post by oxf on 2010-03-06
Hi,

I created a new ext3 partition in the unformatted space on my HD specifically for the purpose of copying and backing up some files before I  do an upgrade. i.e a tempory storage area.

But... I cant copy to because the partitions are locked as root and I cant change them. How do I change them? I tried going in through: gksu nautilus but that doesn't seem to help either.
Soo how do I do tis?

Many Thanks...

---

### Post by flippo on 2010-03-06
can you print the output of:```
sudo blkid
sudo cat /etc/fstab
df -h
```
Each of these will give important information that we can use to help you figure out your permission problem.

---

### Post by scouser73 on 2010-03-06
> **oxf said:**
> Hi,

I created a new ext3 partition in the unformatted space on my HD specifically for the purpose of copying and backing up some files before I  do an upgrade. i.e a tempory storage area.

But... I cant copy to because the partitions are locked as root and I cant change them. How do I change them? I tried going in through: gksu nautilus but that doesn't seem to help either.
Soo how do I do tis?

Many Thanks...

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by flippo on 2010-03-06
Yes, that may work, but I believe the permissions will be reset on reboot (I could be wrong).  If they are, I can help you make the changes permanent if you want them that way.

---

### Post by oxf on 2010-03-06
> **scouser73 said:**
> **1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

Ok thanks....hmm?  At this point I haven't created any folders on the new partition (except lost/found is there. Even if I access via: gksu nautilus when I go to Properties>Permissions it list the owner as root and does not give me permission to change it! 

> **flippo said:**
> can you print the output of:```
sudo blkid
sudo cat /etc/fstab
df -h
```Each of these will give important information that we can use to help you figure out your permission problem.

OK here's what I get. The partition I'm having trouble with is sda4. 
Thanks!

sudo blkid
/dev/sda1: UUID="9AC0C555C0C53871" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="7110efb9-546c-45fe-ba31-687b3c4e2e15" 
/dev/sda3: UUID="60951191-6c7b-46aa-95b3-93fc8ad5076e" TYPE="ext3" 
/dev/sda4: UUID="8566b9d9-56d9-47a0-8521-ca501f42cc53" TYPE="ext3" 

~$ sudo cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=60951191-6c7b-46aa-95b3-93fc8ad5076e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=7110efb9-546c-45fe-ba31-687b3c4e2e15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              30G  7.1G   22G  26% /
tmpfs                 976M     0  976M   0% /lib/init/rw
varrun                976M  108K  976M   1% /var/run
varlock               976M     0  976M   0% /var/lock
udev                  976M  148K  976M   1% /dev
tmpfs                 976M   84K  976M   1% /dev/shm
lrm                   976M  2.4M  973M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda4              25G  173M   24G   1% /media/disk

---

### Post by flippo on 2010-03-06
If you add the line:
/dev/sda4 /media/disk ext3 users,defaults 0 0

to your /etc/fstab, it should fix your permission issue

NOTE:
please backup your fstab before editing it.  If things go wrong you'll have to restore it via livecd

---

### Post by oxf on 2010-03-06
Oh and one further thing. Although there is only the lost and found folder there on that partition which occupies only 16KB, 1.4GB of the partition is used up already. That seems a bit strange ???

---

### Post by oxf on 2010-03-06
> **flippo said:**
> If you add the line:
/dev/sda4 /media/disk ext3 users,defaults 0 0

to your /etc/fstab, it should fix your permission issue

NOTE:
please backup your fstab before editing it.  If things go wrong you'll have to restore it via livecd

Ok thanks! i'll try that in bit. Any idea why this happens in the first place?

---

### Post by flippo on 2010-03-06
EDIT: addressing post 7:

Yes, i suppose it does...

```
ls -al /media/disk
```
will show you all the files (including hidden) in the disk

```
du -hs /media/disk
```
Will show you where all the memory on the disk is going

---

### Post by flippo on 2010-03-06
EDIT: addressing post 8:

Without an entry in your fstab I'm not sure why it mounts in the first place...

You put an entry in your fstab to tell the OS what the disk drives are and how to mount them. The users option tells it to allow all users to access the disk.

Changes won't take place until you restart, and make sure the directory /media/disk exists.

---

### Post by oxf on 2010-03-06
> **flippo said:**
> If you add the line:
/dev/sda4 /media/disk ext3 users,defaults 0 0

to your /etc/fstab, it should fix your permission issue

NOTE:
please backup your fstab before editing it.  If things go wrong you'll have to restore it via livecd

Well I added that line to /etc/fstab and have rebooted. But it still wont let me change anything!:confused:

---

### Post by flippo on 2010-03-06
Whats the output of```
sudo ls -l /media/disk
```

---

### Post by oxf on 2010-03-06
> **flippo said:**
> Whats the output of```
sudo ls -l /media/disk
```

mbdb@L100:~$ sudo ls -l /media/disk
[sudo] password for mbdb: 
total 16
drwx------ 2 root root 16384 2010-03-05 22:10 lost+found
mbdb@L100:~$

---

### Post by flippo on 2010-03-06
Ooops:```
sudo ls -l /media/
```

---

### Post by oxf on 2010-03-06
> **flippo said:**
> Ooops:```
sudo ls -l /media/
```

mbdb@L100:~$ sudo ls -l /media/
total 8
lrwxrwxrwx 1 root root    6 2009-06-21 18:29 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-06-21 18:29 cdrom0
drwxr-xr-x 3 root root 4096 2010-03-05 22:10 disk
mbdb@L100:~$

---

### Post by Morbius1 on 2010-03-06
Open **Terminal**
Type **sudo** **chown morbius:morbius /media/disk**

Change morbius to your own user name and the ownership will pass from root to you

---

### Post by flippo on 2010-03-06
hmm :-/ try:```
sudo chown -R <username>:<username> /media/disk
```

NOTE: this *may* need to be redone on restart, try it...

---

### Post by scouser73 on 2010-03-06
When I say folder/file/drive I mean that the permissions are changed on either a folder, file or drive.  Sorry for any confusion.

---

### Post by oxf on 2010-03-06
> **flippo said:**
> hmm :-/ try:```
sudo chown -R <username>:<username> /media/disk
```NOTE: this *may* need to be redone on restart, try it...

Hmmm? 
when you said "may need to redone on restart" I assumed you meant the change might be lost when shutting down. Anyway I tried that and still wouldn't let me change anything. I then restarted the PC and tried it in terminal again and for now its letting me change the permissions/create folders etc etc. Whether this persists after I reboot remains to be seen but for now it's working :D

Thanks for you help!

---

### Post by flippo on 2010-03-06
Good news :)

Please mark the thread as solved.

---

### Post by oxf on 2010-03-06
> **flippo said:**
> Good news :)

Please mark the thread as solved.
  Yep will do
I'm copying files in at this very moment :D
Thanks for you time....

---

### Post by techvish81 on 2011-10-19
> **scouser73 said:**
> **1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.



thank you very much, it works in 11.10 too,

---

