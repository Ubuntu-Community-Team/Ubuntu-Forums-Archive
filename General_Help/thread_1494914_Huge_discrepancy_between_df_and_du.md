---
title: "Huge discrepancy between df and du"
date: 2010-05-27
forum: General Help
---

### Post by gamelux on 2010-05-27
Hi all, my root partition has filled up and I am trying to free up some space. To check what is happening I ran df as follows:

```

gamelux@rea:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              28G   28G     0 100% /

```

To check what I could clean up, I ran du as follows 
```

 gamelux@rea:~$ sudo du -smx / --exclude=/mnt/*
6089	/

```
That is, approximately 6Gb, **a 22Gb discrepancy with df !**

Can anyone help me to figure out what is going on?

---

### Post by gamelux on 2010-05-27
Well, I solved it. There was no discrepancy after all, but a failed mount on /mnt. The content of the mount point /mnt/otto was actually storing its files in the hosting filesystem, i.e., /. 


Sorry everybody. Hope it helps someone.

---

