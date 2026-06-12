---
title: "Rhythmbox not detecting song path"
date: 2012-04-10
forum: General Help
---

### Post by Pyrrotech on 2012-04-10
After I installed ubuntu, I told rhythmbox to look at my second hdd (with nothing but song files). It automatically pulled the files and for the past two days has been working flawlessly. Today, however, I updated my computer via the update manager and now when I open rhythmbox it says that there are 0 artists with 0 albums. (basically its not seeing my second Hdd). When I go to my Home Folder, it sees the second drive, and after attempting to open it and see my individual music files, rhythmbox magically decides that it remembers where the songs were. What do I change to prevent me having to open the drive after every reboot?

---

### Post by papibe on 2012-04-10
Hi Pyrrotech.

My guess is that your 2nd drive is not being mounted automatically at boot time.

If that's the case, you need to add an entry to your /etc/fstab so it gets mounted automatically at boot. Although the entry itself is very simple, you need to know some details about the disk.

Could you double click your drive (so it gets mounted), and then post the result of these commands?
```
sudo blkid

df -h
```
Regards.

---

### Post by Pyrrotech on 2012-04-10
Thanks for the quick reply!

robert@ubuntu:~$ sudo blkid

/dev/sda1: UUID="2bf9a895-1507-4ca9-b5e4-decb9e888247" TYPE="ext4" 
/dev/sda5: UUID="5e65e99f-ce6e-41bc-9349-d3751c39b39c" TYPE="swap" 
/dev/sr0: LABEL="UDF Volume" TYPE="udf" 
/dev/sdb1: UUID="0A90942290941673" TYPE="ntfs" 
robert@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       461G   14G  424G   4% /
udev            2.4G  8.0K  2.4G   1% /dev
tmpfs           992M  852K  992M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.5G  188K  2.5G   1% /run/shm
/dev/sr0        2.2G  2.2G     0 100% /media/UDF Volume
robert@ubuntu:~$

---

### Post by papibe on 2012-04-10
I'm a little confused. Is your 2nd drive /dev/sr0 or /dev/sdb1 ?

Did you double click on the 2nd driver? Where is it being mounted?

Regards.

---

### Post by Pyrrotech on 2012-04-10
I believe its the second one

/dev/sdb1

---

### Post by papibe on 2012-04-10
Thanks. That make more sense ;)

I see that is not mounted (is not being list on the df command). In order to preserve your Rhythbox library, we need to know exactly where it's mounted when you double click on it on nautilus (file manager).

Regards.

---

