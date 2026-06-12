---
title: "install rar 2.71"
date: 2010-02-08
forum: General Help
---

### Post by isee on 2010-02-08
Hi all,

I'm trying to install rar 2.71 instead of 3.80 using this post as a guide

[http://ubuntuforums.org/showthread.php?t=519758](http://ubuntuforums.org/showthread.php?t=519758)

```
sudo chown -R root:root rar
sudo mv rar /usr/local/rar2.71
cd /usr/local/bin
ln -s /usr/local/rar2.71/rar .
ln -s /usr/local/rar2.71/unrar .
```
When I run the ln commands I get this error
ln: creating symbolic link `./rar': Permission denied

How can I get the last two commands to work?

Thanks!

---

### Post by Satoru-san on 2010-02-10
/usr/local/bin requires root access even though it does say user and local.

So all you have to do is use sudo with those symbolic links.

Hope this helps.

---

### Post by isee on 2010-02-10
Awesome!  Thanks very much Satoru-san! It worked :D

---

