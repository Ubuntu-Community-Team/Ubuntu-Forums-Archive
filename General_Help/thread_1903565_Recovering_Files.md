---
title: "Recovering Files"
date: 2012-01-02
forum: General Help
---

### Post by Jimstehrman on 2012-01-02
Hi all,

I recently had my system refuse to start (in Ubuntu), with an error about inconsistent file system.
I'm trying to recover a few files from my old ubuntu file system. I have booted ubuntu from a usb key and I'm trying to extract the files, but I have run into a file permissions issue. I can't access or do anything with the files from the key. Anyone know how to access locked files? I know the root password for my old system.

Thanks!

---

### Post by 73ckn797 on 2012-01-02
Try testdisk, from the repositories. I was able to recover some pictures from a flash drive using photorec. It can be used while booting from a live CDD.
Check this: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Try [www.googlubuntu.com]("http://www.googlubuntu.com") to search for more information.

---

### Post by Jimstehrman on 2012-01-02
I get the following response when I try to install test disk while booted from the liveUSB
"E: Unable to locate package testdisk"

---

### Post by bluexrider on 2012-01-02
You should be able to use the Live CD to access the files on the HDD then move or copy to external HDD using rsync

---

### Post by Jimstehrman on 2012-01-02
I don't have permission to copy or access these files

---

### Post by fdrake on 2012-01-02
try with:
```

sudo nautilus 

```
and browse to the folders/files you need.
you should be using gksu/do but i am not sure it comes by default in a live cd.

after you have copied your files you need to chenge their permissions to all users with.
```

sudo chmod 777 myfile 

```

---

### Post by 73ckn797 on 2012-01-03
> **Jimstehrman said:**
> I get the following response when I try to install test disk while booted from the liveUSB
"E: Unable to locate package testdisk"
I believe you can enable the additional sources in the repositories via Software Sources.

---

