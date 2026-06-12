---
title: "Folder CHOWN Problem"
date: 2010-07-12
forum: General Help
---

### Post by iNsOmNiOuS on 2010-07-12
Hi,

I have just installed vsftpd onto my VPS, I followed this guide : [http://ubuntuforums.org/showthread.php?t=662784](http://ubuntuforums.org/showthread.php?t=662784)

I used the user lhlinux-ftp

Somehow I cannot delete, rename, upload, create anything on the server, even after chowning the directory.

(chown -R lhlinux-ftp /var/www)

There are no errors during chown. I also chmodded the directory (chmod 775 /var/www)

I still cannot delete, rename, upload or create anything on the server. Why is this, and mainly, how can I solve this problem.

Thanks ;)

---

### Post by iNsOmNiOuS on 2010-07-13
Bummppp

---

### Post by 3rdalbum on 2010-07-13
DON'T chown the folder. Write files to it as root instead.

Either use 'sudo' before the copy command, like this:

```
sudo cp hello.txt /var/www/
```

Or run a file browser as root:

```
gksudo nautilus
```

Chowning the folder is loosening the system's security (that has been designed by the world's best security experts). Copying files across as root leaves the security system intact.

---

### Post by iNsOmNiOuS on 2010-07-13
I can't upload my entire website via the terminal copy command. I only have SSH access to the VPS :s

---

