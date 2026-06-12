---
title: "file system problem"
date: 2010-08-26
forum: General Help
---

### Post by arjun07 on 2010-08-26
Hi 
I am arjun i am new to Linux, i don't know the basics my problem is in windows we are using like this C: D: E: F: Drives in windows it is taken default OS Drive is (C:) remaining the D: E: etc,, drives are our using private data purpose this is windows file system structure. come to Linux /boot / /usr /var /home and swap this is all partitions which one is the os part which one is the our part i didn't under stand this is my problem can you help me 

arjun
Thanks in advance

---

### Post by cgroza on 2010-08-26
Almost everything is a OS part except /home. In home you keep your data. In others the applications are installed. In /mnt the parttions are mounted. You can read documentation about the linux file system structure on google.

[http://www.basicconfig.com/linux/filesystem](http://www.basicconfig.com/linux/filesystem)

---

### Post by weeman7007 on 2010-08-26
Hi, most people don't really need more than three partitions, swap, /home and /

[http://wiki.archlinux.org/index.php/Beginners%27_Guide#Partition_Info](http://wiki.archlinux.org/index.php/Beginners%27_Guide#Partition_Info)

This link will tell you what each partition is actually used for. Having a separate /home partition is useful if you need to reinstall your OS, because you can keep all of your data and just mount it again for your new installation. It will keep your personal settings such as themes and preferences, as well as your data such as music and videos.

Hope this helps.

---

