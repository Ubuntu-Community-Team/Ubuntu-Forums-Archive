---
title: "resetting permissions on folders"
date: 2011-07-26
forum: General Help
---

### Post by Dr.Dupont on 2011-07-26
Hi

I've just installed Xubuntu 11.04 and is looking on a HDD from my old Zentyal server, there are some files on the drive that I forgot to backup, but I can't get into those folders because I don't have permission to view them.

Is there a way to replace or reset owner on the folders so I can get the files???

Best Regards
Dennis Dupont

---

### Post by fdrake on 2011-07-26
> **Dr.Dupont said:**
> Hi

I've just installed Xubuntu 11.04 and is looking on a HDD from my old Zentyal server, there are some files on the drive that I forgot to backup, but I can't get into those folders because I don't have permission to view them.

Is there a way to replace or reset owner on the folders so I can get the files???

Best Regards
Dennis Dupont

[code] sudo chown YOursUserName /path/of/file
sudo chmod 755 /path/of/file [/code|

or you can just change perm of all the drive

[code] sudo chown YOursUserName /media/HD1
sudo chmod 755 /media/HD1 [/code|

---

### Post by Lighthorse01 on 2011-09-01
Well that would be good except in my case it keeps telling me I am not the owner.
I am set as admin with all privileges.
How do I tell it that I am the owner ??

---

### Post by fdrake on 2011-09-04
> **Lighthorse01 said:**
> Well that would be good except in my case it keeps telling me I am not the owner.
I am set as admin with all privileges.
How do I tell it that I am the owner ??
maybe the disk is set for read only for all users!
can you post your fstab/mount
```

mount
less /etc/fstab

```
also try as root:

```

sudo su
sudo chown -R YOursUserName /media/<name of driver>
sudo chmod -R 755 /media/<name of driver>
nautilus /media # or you can simply browse the disk and copy and paste in your
#directory. You doo need to change the permissions to read write to your user like in
#post #2
exit

```
or try 

are you sure the device is mounted?
in case of errors can you please copy and paste from the terminal the messages with the commands

---

### Post by Lighthorse01 on 2011-09-05
I have to send comands as root
didnt know that at first.

---

### Post by fdrake on 2011-09-06
> **Lighthorse01 said:**
> I have to send comands as root
didnt know that at first.

by using root's permissions did it work for you. did you reset your permissions back on you folder?

---

