---
title: "how to create a user crontab, without the need for rood privileges ?"
date: 2011-03-20
forum: General Help
---

### Post by hen770 on 2011-03-20
Hi,

i know the subject is hard to understand but i did my best with it.

the problem:

i have 2 HDs on my Ubuntu OS, the first is 1TB and the other is 500GB, i want to do a backup with rsync from my 1TB HDs (in with the Ubuntu is on it) to the 500GB.

on the 500GB i have a partition called Backup.

what i did:

i have created a user crontab that dose two things:
1. mount the Backup partition from the 500GB to a folder called /~/Backup on my home directory which is on the 1TB HD.

2. i wrote the proper rsync command for the backup to go.


that is my crontab, ('hanan' is the username):


```
SHELL=/bin/bash
MAILTO=hanan
33 3    * * * /bin/mount /dev/sdb2
34 3    * * * /usr/bin/rsync -r -t -v --progress --delete --size-only /home/hanan/Programs/Stuff/Printers/ /home/hanan/Backup/

```

the problem:

when the time for the crontab comes it mounts the Backup partition to the right location on the user's home directory, but it can't do the second step because it needs root privileges in order to write on the mounted HD.

i have tried that manually and still i can't copy any file to the mounted HD unless i do it with the sudo command.

am i missing something ?

i want to that via the CLI and cron just for the study experience.

thanks.

---

### Post by WorMzy on 2011-03-20
The problem is the mount command, right?

You need to add the "users" option to the disk's fstab entry, after that normal users will be able to mount it without sudo.

Firstly, open fstab:

```
gksu gedit /etc/fstab
```

Then look for the disk's fstab entry (I'm assuming it has one, as you haven't specified a mount point in your cron script), and add "users" to the end of the options.

like so:

```
/dev/sdb2   /mnt   ext4 defaults,noauto,**users** 0 0
```

If you've already done this, and cron is ignoring it, then I don't know what's wrong.

---

### Post by hen770 on 2011-03-20
thanks,

i did that already, and i am able to mount it without the sudo command, but i can't write to the mounted HD.

that is:
before i mount the HD, the folder Backup on my home folder had the following permissions:
```
drwxr-xr-x  3 hanan hanan 4096 2011-03-20 03:23 Backup
```

and after i mount it (via the crontab, or manually without sudo), it become like that:
```
drwxr-xr-x  2 root  root  4096 2011-03-20 03:21 Backup
```

here i think the problem is hide, why it is the directory become the root owner ?!

---

### Post by tredegar on 2011-03-20
> why it is the directory become the root owner ?!
Because the filesystem on the backup drive is owned by root.
The solution is first to mount the drive, then **sudo chmod 777 /home/hanan/Backup/**
Result: It is still owned by root, but anyone can write to it.

The next time it is mounted it will be have 777 perms automatically.

---

### Post by hen770 on 2011-03-20
> **tredegar said:**
> 

The next time it is mounted it will be have 777 perms automatically.

Thanks.

is it change the permissions of the filesystem itself? if so can you point me to which device file ?

---

### Post by tredegar on 2011-03-20
> is it change the permissions of the filesystem itself?
Yes
> if so can you point me to which device file ?
I don't understand your question.

---

### Post by hen770 on 2011-03-20
as far as i know in linux every physical device have a file that represent it (like /dev/sdb2, and so on).

my point is, can i change the permissions of the partition without mount it first ?
if no, what would happen when i would mount that partition in other directory, i will need to change the permissions there too ?

thank you so far, i tested it and it works, but my last question is for the general knowledge.

---

### Post by WorMzy on 2011-03-20
Is this backup partition formatted as NTFS?

If so, try adding the following options to fstab:

```
uid=1000,gid=1000,umask=002
```

Assuming that you're user 1000 (the user you created during the installation process). Run
```
echo $UID
```
to check.

---

### Post by hen770 on 2011-03-20
nope, it is ext3, but it is working right now, after i have changed the permissions of the folder i have mounted it on (after i mount the drive on that folder).
as @tredegar has told me above.

---

### Post by tredegar on 2011-03-20
> my point is, can i change the permissions of the partition without mount it first ?
No.

**/dev/sdb2** is just a *block device* which happens to contain a filesystem.
The permissions for **/dev/sdb2** should be **rw-rw---- root:disk**
> what would happen when i would mount that partition in other directory, i will need to change the permissions there too ?
Once you have changed the permissions for the filesystem, it remembers them.

If you mount it somewhere else, the mountpoint will be given the permissions of the filesystem, in this case **rwxrwxrwx root:root**

Try it!

---

### Post by hen770 on 2011-03-20
thank you.

how can i change the title to [SOLVED]?.

---

### Post by The Cog on 2011-03-20
In [COLOR="Red"]**Thread Tools**[/COLOR] - red text at the top of the page just above the first post on the page.

---

