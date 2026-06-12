---
title: "Can't list contents or delete directory.  Corrupt?"
date: 2012-01-27
forum: General Help
---

### Post by jshayden on 2012-01-27
```
# ll | grep corrupt
drwxrwxrwx 2 user group 51372032 Jan 27 10:25 corrupt_dir
```

This hangs indefinitely:
```
# ll corrupt_dir
```

As does this:
```
# rm -rf corrupt_dir
```

As does this:
```
# find currupt_dir
```

Any ideas?  Thanks.

---

### Post by gsgleason on 2012-01-27
Weird.

In your last quote, you misspelled the name.  I am assuming you spelled it correctly with the find command.

I would recommend a filesystem check on whatever filesystem has that directory.

Is it a local filesystem or a network filesystem?

Please show output of 'mount'

---

### Post by jshayden on 2012-01-27
> **gsgleason said:**
> In your last quote, you misspelled the name.  I am assuming you spelled it correctly with the find command.

Ah; yes.  I simply misspelled it here.

> **gsgleason said:**
> 
I would recommend a filesystem check on whatever filesystem has that directory.


That's my next move, but I need to wait till tonight, as people are relying on the machine during the day.  I thought I would ask here and see if anyone had another suggestion in the mean time.

> **gsgleason said:**
> Is it a local filesystem or a network filesystem?

It's local.  This is a virtual machine (Linode).

> **gsgleason said:**
> Please show output of 'mount'

```
# mount
/dev/xvda on / type ext3 (rw,noatime,errors=remount-ro)
```

---

### Post by jshayden on 2012-01-31
The file system check was clean.  Any ideas out there?

Thanks.

---

### Post by Sazhen86 on 2012-01-31
Hi

51,372,032 bytes for the folder's metadata seems pretty big.  If your system is 32 bit, there is a point where tools such as "ls" can't handle a large number of files.

If it is a 32 bit system, can you try a 64 bit live CD and mount that file system.

A long shot, but it's all I can think of.

Hope it helps.

---

