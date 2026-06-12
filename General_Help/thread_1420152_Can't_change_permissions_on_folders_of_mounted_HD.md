---
title: "Can't change permissions on folders of mounted HD"
date: 2010-03-02
forum: General Help
---

### Post by play_ on 2010-03-02
Hi.

I have a second hard drive(named 'Shared') that gets mounted when I go to menu -> places -> Shared.

Inside Shared I have a folder 'www' where i keep web projects i make.
However, when I install apache and change its config to use /media/Shared/sites/www/ as root and then go to [http://localhost](http://localhost), i get access denied. (You do not have permission to access / on this server)


I was told in #httpd that this is due to folder permissions, and was asked to change folders permission to 755. However, it doesn't seem to work.

For example,
```

lyrae@localhost:/media/Shared/sites/www$ ls -la
drwx------ 1 lyrae lyrae 4096 2010-03-02 01:14 .
drwx------ 1 lyrae lyrae    0 2009-11-04 22:02 ..
drwx------ 1 lyrae lyrae 4096 2010-02-24 21:05 technocherry

```

I then try to chmod it

```

lyrae@localhost:/media/Shared/sites/www$ sudo chmod 755 technocherry
[sudo] password for lyrae: 
lyrae@localhost:/media/Shared/sites/www$ ls -la
drwx------ 1 lyrae lyrae 4096 2010-03-02 01:14 .
drwx------ 1 lyrae lyrae    0 2009-11-04 22:02 ..
drwx------ 1 lyrae lyrae 4096 2010-02-24 21:05 technocherry

```


Also, just throwing this out there, because maybe it has something to do with the way /media/Shared is mounted....but One way to fix this access denied problem is changing
```

export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data

```

to

```
export APACHE_RUN_USER=lyrae
export APACHE_RUN_GROUP=lyrae
```

in envars. however, this doesnt feel right and makes phpmyadmin not work.

---

### Post by dcstar on 2010-03-02
> **play_ said:**
> Hi.

I have a second hard drive(named 'Shared') that gets mounted when I go to menu -> places -> Shared.
........

And **exactly** what filesystem is this "Shared" drive?

---

### Post by play_ on 2010-03-02
> **dcstar said:**
> And **exactly** what filesystem is this "Shared" drive?

Good point!
it's NTFS so i guess this is why i can't change permissions....but this problem has never happened before though.

---

### Post by blueridgedog on 2010-03-02
FS appears to not support permissions?

---

### Post by play_ on 2010-03-02
how can i fix this?

---

### Post by MooPi on 2010-03-02
```
sudo chown -R  "username" /media/Shared/sites/www
```This will change ownership. Not certain if this holds true to NTFS

---

### Post by blueridgedog on 2010-03-02
You have to put your files on a drive/partition formated in a user and permission aware type when operating under Linux.  For now that is ext2, ext3 and ext4.  Otherwise, it mounts the partition (fat32, ntfs) as a single user.  

I recommend an ext4 formated drive/partition for your web development needs.

---

