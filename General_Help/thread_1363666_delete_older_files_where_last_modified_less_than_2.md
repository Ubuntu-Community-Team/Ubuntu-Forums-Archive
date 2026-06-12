---
title: "delete older files where last modified less than 24 hours"
date: 2009-12-24
forum: General Help
---

### Post by snake_eyes on 2009-12-24
Hello,

I have a cache directory, /root/cache which is collect more than 1000 file per day, is there any command to delete the old files where last modified last 24 hours (keep the current day only)

I have the following command which will display them
```
find /root/cache -mtime -1 -print
```

How I can purge the rest of files?

Cheers,

---

### Post by lloyd_b on 2009-12-24
> **snake_eyes said:**
> Hello,

I have a cache directory, /root/cache which is collect more than 1000 file per day, is there any command to delete the old files where last modified last 24 hours (keep the current day only)

I have the following command which will display them
```
find /root/cache -mtime -1 -print
```

How I can purge the rest of files?

Cheers,

Just change the "-print" to "-delete":```
find /root/cache -mtime -1 -delete
```

Lloyd B.

---

### Post by snake_eyes on 2009-12-25
Thank you for your advice, but I thing this command was print (Display) the modified last 24 hours, what I need is to delete all the cache directory unless the created and modified files last 24 hours..

---

### Post by lloyd_b on 2009-12-25
> **snake_eyes said:**
> Thank you for your advice, but I thing this command was print (Display) the modified last 24 hours, what I need is to delete all the cache directory unless the created and modified files last 24 hours..

Sorry - I was misunderstanding you.

It's just a matter of changing that "mtime" parameter.  Try this one, to see if it properly finds the files you want to delete:```
find /root/cache -mtime +0 -print
```and if that works, just change the "-print" to "-delete" to remove them.

Lloyd B.

---

### Post by snake_eyes on 2009-12-25
Thank you solved... :)

---

