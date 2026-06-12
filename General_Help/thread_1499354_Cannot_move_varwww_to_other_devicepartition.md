---
title: "Cannot move /var/www to other device/partition"
date: 2010-06-01
forum: General Help
---

### Post by fridaythe14th on 2010-06-01
I'm trying to move the /var/www dir to another partition (another hard drive even, though I doubt that makes a difference) because my file system partition is rather small. But when I do I get "403 -forbidden" and in the logs "Permission denied: /home/www/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable". If I move it anywhere within the partition (and adjust the conf) I don't get this problem.

Using Ubuntu 10.04 Desktop x64. I haven't had any problems with this in earlier Ubuntu-versions.

---

### Post by Ozymandias_117 on 2010-06-01
Have you tried just mounting the other drive at /var/www? Also, make sure you use ```
sudo chmod +r /var/www
```

---

### Post by fridaythe14th on 2010-06-01
> **Ozymandias_117 said:**
> Have you tried just mounting the other drive at /var/www? Also, make sure you use ```
sudo chmod +r /var/www
```

Thanks! The directory is readable by all users. It appears the problem only occurs on one certain partition (the one I want it on). If I move it anywhere else outside of that partition (and edit the conf) it works, but if I move or symlink it to that partition I get the problem. The partition is not just for /var/www so I don't want to mount it there, however I don't see how it'd make a difference.

---

