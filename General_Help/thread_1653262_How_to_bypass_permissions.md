---
title: "How to bypass permissions"
date: 2010-12-26
forum: General Help
---

### Post by Ramy89 on 2010-12-26
Hello,for many reasons now I have the usr directory not present in my ubuntu 10.10 file system.I cancelled it for mistake.
Now what I'm trying to do is to run a live cd and copy the usr directory from the cd to the disk's file system,but the problem is that I don't have permissions.
How to bypass the permissions?

---

### Post by akand074 on 2010-12-26
Type this in the terminal:

```
gksudo nautilus
```

This will open a file browser with root privileges.

---

### Post by coffeecat on 2010-12-26
You have deleted the whole of your /usr directory with contents? Your /usr directory contains large parts of all your installed applications - that is stuff that you have installed or updated since you first installed Ubuntu. If you simply copy the live CD /usr you will have all that missing. Moreover, you will probably have libraries out of sync in /lib with the older system stuff you copy from the live CD /usr. Even if the system boots up after you do the copy, you are going to have major problems such as apps appearing in the menus but not working.

It will probably be quicker to use the live CD to backup all your personal files and then reinstall.

---

### Post by Ramy89 on 2010-12-26
Now my doubt is that the usr directory was there but I cancelled trying to recover it.
For mistake the usr directory was in var directory.
I used this comand:
```

mv /var/usr ./

```
Possible that now the directory is cancelled or where should be?

---

### Post by lisati on 2010-12-26
> **Ramy89 said:**
> Now my doubt is that the usr directory was there but I cancelled trying to recover it.
For mistake the usr directory was in var directory.
I used this comand:
```

mv /var/usr ./

```
Possible that now the directory is cancelled or where should be?

If you are running from a Live CD, the location of /var/usr will be in a different place to what it would be if you are running from your regular installation. Chances are that a simple copy from the LiveCD's copy to your hard drive won't be enough to get your computer working again.

As someone else suggested, it will probably be easier to make a backup of your important files, and then reinstall Ubuntu.

---

### Post by wojox on 2010-12-26
> **Ramy89 said:**
> Now my doubt is that the usr directory was there but I cancelled trying to recover it.
For mistake the usr directory was in var directory.
I used this comand:
```

mv /var/usr ./

```
Possible that now the directory is cancelled or where should be?

There's no such thing as /var/usr/. Try again.

---

### Post by Ramy89 on 2010-12-27
I was executing this command not from live cd,but from the recovery mode,logged as root.
Ok that there isn't such directory,but in my disk there was because for mistake usr folder was in var folder.
Now my doubt is that witht his comand I cancelled the file.May this be possible?
Since I used it the directory isn't there,but I also may been wrong checking.
Ok then,I had it from a week only,there's not all this pain in reinstalling it :P

---

### Post by wojox on 2010-12-27
Read this [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

Open a terminal and rum these commands and check. You can copy and paste your answer back here if you'd like.

```
cd /.
```

```
ls -al
```

---

### Post by Ramy89 on 2010-12-27
It gives me the entire screen full of data.Is there a way to take a screenshot from the recovery mode and save it into a usb drive?
If not I'll write all on a paper and post here.

---

