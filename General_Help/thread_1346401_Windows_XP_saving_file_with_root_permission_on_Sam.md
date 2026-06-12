---
title: "Windows XP saving file with root permission on Samba"
date: 2009-12-05
forum: General Help
---

### Post by narsaw on 2009-12-05
I am running the latest desktop version of Ubuntu, its acting as a samba server for my home network.

From windows I map my samba share in My Computer. When I save a file from Windows to my samba share, the ownership are set to

```

-rwxrw----  1 root  users     904704 2006-12-01 22:37 test.file

```

In Ubuntu my username is 'filter1' and my primary group is 'users'. 
On windows XP my username is 'filter1'.

I would like to files to save as:
```

-rwxrw----  1 filter1  users     904704 2006-12-01 22:37 test.file

```


How do I do this?

---

### Post by narsaw on 2009-12-08
bump

---

