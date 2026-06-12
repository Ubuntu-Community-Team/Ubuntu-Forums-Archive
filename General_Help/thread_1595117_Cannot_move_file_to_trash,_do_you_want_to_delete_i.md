---
title: "Cannot move file to trash, do you want to delete immediately?"
date: 2010-10-12
forum: General Help
---

### Post by Roasted on 2010-10-12
Why is it when I go to /var/www/skynet (skynet is a folder I created and gave myself full ownership + group permission) and when I delete anything within that folder I created it asks me:

Cannot move file to trash, do you want to delete immediately?

Whereas in my home directory if I delete anything, it just goes to the trash bin? Just trying to understand the differences here. Thanks!

---

### Post by raywjohnson on 2012-02-06
Bummping this thread. 

I am also having this ussue. I can send files from /home/USERNAME to the trash (via nautilus), but under /var/www/html I always get the "Cannot move file to trash, do you want to delete immediately?" message.

I suspected that it had something to do with SELinux. I did find SELinux was not running and did a forced reinstall and reset. System is now working fine. Still cannot move /var/www/html to the Trash.

Using Ubuntu version 11.10. This was not an issue on Ubuntu version 10.04.

Permissions for /var/www/html = drwxrwxr-x (and all sub-directories)

SELinux for /var/www/html = system_u:object_r:var_t:s0

I do have my Home directory encrypted (via the built in Ubuntu system).

Any guidance or insight is appreciated!

--RayJ

---

### Post by raywjohnson on 2012-02-06
Figures.

After many attempts to find a solution. I find one right after posting here. :redface:

This worked for me:

Open a terminal:

```
id -u <username>
```

Should be: 1000

```
sudo mkdir /.Trash-<ID>

sudo chown <username>.<groupname> /.Trash-<ID>
```

example:

```
id -u rayj

(returns 1000)

sudo mkdir /.Trash-1000

(enter password)

sudo chown rayj.rayj /.Trash-1000
```

Now I can move /var/www files to the "Trash" via nautilus.

However, nautilus does not show them when viewing the Trash (i.e. Location: trash:///).

Still looking for a good solution.

--RayJ

---

### Post by uRock on 2012-02-06
Thread from 2010 necromanced,

Thread Closed

---

