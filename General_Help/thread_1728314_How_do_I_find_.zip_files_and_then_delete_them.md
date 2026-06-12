---
title: "How do I find .zip files and then delete them"
date: 2011-04-13
forum: General Help
---

### Post by mashedbear on 2011-04-13
Hi I want to use the shell to find .zip files in my music directory and all sub directories and then delete only these files. 

The following will find the files I want to delete

```
find /home/me/Music/ -name *.zip -ls
```

What is the next step to delete *only* these files. 

Would it be a good idea to move them to another directory before doing the final rm - how would I do this?

Thanks

---

### Post by rubylaser on 2011-04-13
Just pipe it to xargs.
```
find /home/me/Music/ -name "*.zip" | xargs rm
```

---

### Post by ~Plue on 2011-04-13
execute rm -r along with the command
```
find /home/me/Music/ -name *.zip -exec rm -r {} \;
```

---

### Post by danjahner on 2011-04-13
If you want to be extra cautious, you could do :

```

find /home/me/Music/ -name *.zip -print0 | xargs -0 -I{} mv {} /home/me/Music/zip-files

```This will move them to a folder that you can double-check before deleting.

---

### Post by rubylaser on 2011-04-13
> find /home/me/Music/ -name *.zip -exec rm -r {} \;

Why would you use exec over xargs? xargs is more efficient in that when you use "-exec" with 'find', it starts a new process for each file that is found.  This can be very expensive for a large number of files.

And, no need to pass the recursive flag to rm, as find is recursive by default.

---

### Post by ~Plue on 2011-04-13
> **rubylaser said:**
> Why would you use exec over xargs? xargs is more efficient in that when you use "-exec" with 'find', it starts a new process for each file that is found.  This can be very expensive for a large number of files.

And, no need to pass the recursive flag to rm, as find is recursive by default.
i thought the difference would be minimal. thanx for letting me know that.

---

### Post by mashedbear on 2011-04-14
Thanks All

---

