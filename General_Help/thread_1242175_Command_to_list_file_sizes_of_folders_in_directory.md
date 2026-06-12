---
title: "Command to list file sizes of folders in directory non recursively."
date: 2009-08-16
forum: General Help
---

### Post by Databit on 2009-08-16
I know that the du command will list folder sizes but I want to list all of the folders in /home and their file sizes without listing the file size for each subdirectory so that I can easily spot which users have big home folders.
Anyone know how to do this?

---

### Post by drs305 on 2009-08-16
I am not exactly sure I understand what you want. If this isn't it, would you please elaborate?
```
du -h --max-depth=1 /home
```

---

### Post by geirha on 2009-08-16
Try one of these
```

du -x -s /home/* | sort -n
du -x --max-depth=1 /home | sort -n

```

---

### Post by dssr on 2009-08-16
i think this will work

```
ls -l /home|cut -d " " -f 5,8
```

---

### Post by dssr on 2009-08-16
> **dssr said:**
> i think this will work

```
ls -l /home|cut -d " " -f 5,8
```


no sorry that does not work it should be
#ls -l /home|tr -s " "|cut -d " " -f 5,8
still it does not work

above 2 are okay

---

### Post by Databit on 2009-08-17
> **drs305 said:**
> I am not exactly sure I understand what you want. If this isn't it, would you please elaborate?
```
du -h --max-depth=1 /home
```

This was perfect! Thanks

---

