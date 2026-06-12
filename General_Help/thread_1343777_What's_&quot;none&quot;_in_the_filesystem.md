---
title: "What's &quot;none&quot; in the filesystem ?"
date: 2009-12-02
forum: General Help
---

### Post by lostinxlation on 2009-12-02
Hi,
Running df command, I got the following output. There are "none" and "udev" other than /dev/sda*.
Could anyone please tell me what "none" actually is ?
During installation, I manually mounted /dev/sda9 to /var and I thought all the file/directory below /var should be under /dev/sda9, but some came under "none".
I have other ext4 partitions that I set "don't use" during installation(they are reserved for other linux distribution), and they might be causing this issues but I'm not sure.
 
 
lifebook:~$ df -k
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sda3 1541712 187092 1276304 13% /
udev 117248 288 116960 1% /dev
none 117248 0 117248 0% /dev/shm
none 117248 88 117160 1% /var/run
none 117248 0 117248 0% /var/lock
none 117248 0 117248 0% /lib/init/rw
/dev/sda5 6443584 1453204 4663060 24% /usr
/dev/sda8 3842376 77636 3569552 3% /home
/dev/sda9 3802816 213304 3396332 6% /var

---

### Post by john newbuntu on 2009-12-02
If I am right, the none there says it is a temporarily mounted filesystem storage by the kernel.  The storage does not happen in your hard disk drive but happens in memory (or in swap space). If you type

cat /proc/mounts

you can see these are mounted on to temporarily mounted storage like tmpfs.  System programs that need /var/lock or /var/run or /dev/shm will write to memory and not to /dev/sda9 as you have specified.  But if you use mail, then mail stuff goes I think into some place under /var like /var/mail.  This is when the /dev/sda9 will get used.  Any admins here who can correct me if I am wrong.

---

### Post by lostinxlation on 2009-12-02
Thanks!!

---

### Post by Don0918 on 2011-04-16
Sorry to bring this up again.

I did **df -h** in my system and came up with the following:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             906G  2.7G  858G   1% /
none                  1.9G  228K  1.9G   1% /dev
none                  1.9G     0  1.9G   0% /dev/shm
none                  1.9G  312K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock


Now, looking at all filesystems with **none**, isn't the 1.9G each are using too big? I have 1Tb of disk space but 4 temporarily mounted storage costing about 8Gig in total is a bit too much in my opinion.

And what are these /dev, /dev/shm, /var/run and /var/lock mounts? 

Do you recommend that we minimize this? How?

Thanks!

---

### Post by mcduck on 2011-04-16
Like the above explanation said, they are virtual filesystems and don't exist on your disk. Their size is completely irrelevant.

And if you check the *used* space values they are together using 540KB of RAM (not hard drive space, they don't exist on any hard drive)

---

### Post by Don0918 on 2011-04-16
Oh... sorry about that. I completely missed that one regarding it being a virtual filesystem. Thanks about that!

Now I'm curious about all the temporarily mounted filesystems. What are these used for:

a. /dev
b. /dev/shm
c. /var/run
d. /var/lock


Thanks for clarification! :)

---

### Post by mcduck on 2011-04-16
Everything is a file in Linux, meaning that every device, every process and so on will appear as a file somewhere in the filesystem. As it would make no sense to store running processes and such stuff on your actual hard drive, they appear on these virtual filesystems.

For example all the devices and components in your computer appear as files inside /dev. 

/var/run contains runtime variables.

/dev/shm is shared memory, allowing easy way for programs to share data between each other.

/var/lock contains lock files, used when a process needs explicit access to some device or file, making sure no other process accesses it at the same time.

---

### Post by Don0918 on 2011-04-16
thanks for that! :)

---

