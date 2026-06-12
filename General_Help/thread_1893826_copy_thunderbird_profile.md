---
title: "copy thunderbird profile"
date: 2011-12-11
forum: General Help
---

### Post by qwertyjjj on 2011-12-11
How can I copy the thunderbird profile, all messages, folders, and filters to another computer?
On windows, I used mozbackup but that doesn't exist for linux.

---

### Post by spiky001 on 2011-12-11
Have you looked in ~/thunderbird/profiles

---

### Post by 73ckn797 on 2011-12-11
I always copy the contents of /home/yourname/.thunderbird/*.default into the .thunderbird folder of the new install. The folder may not initially exist until you have started Thunderbird. If that is the case copy the entire /home/yourname/.thunderbird folder. On first start up everything will be as it was on your other computer.

The *.default folder is created when you start T-bird the first time. I use "*" because the folder is radomly named, such as gkcdl609.default. If you have already ran T-bird you can still copy the internal folders from the *.default into the new folder. If you copy the entire *.default folder over there is a "profiles.ini" file that will have to be edited to point to the name of the *.default folder you copied over.

---

### Post by killermist on 2011-12-11
You can store the directory as a tarball and then re-expand it without having to open thunderbird first.

```
cd ~
tar -czvf Thunderbird_backup.tar.gz .thunderbird/
```
That will create the backup.  Copy it to your other home directory and use 
```
cd ~
tar -xzvf Thunderbird_backup.tar.gz
```
to restore it.

---

### Post by Momof9Blessings on 2011-12-20
I just installed linux ubuntu 11.10 / dual boot with vista.... been awhile (2008) since I used ubuntu....  now I have CS3, which should run great in wine!!!

I want to copy my thunderbird profile over (from Vista), is that possible???

---

### Post by 73ckn797 on 2011-12-20
> **Momof9Blessings said:**
> I just installed linux ubuntu 11.10 / dual boot with vista.... been awhile (2008) since I used ubuntu....  now I have CS3, which should run great in wine!!!

I want to copy my thunderbird profile over (from Vista), is that possible???
Yes. Pretty much the same process. Look for the same cryptic folder name mentioned in a previous reply.

---

