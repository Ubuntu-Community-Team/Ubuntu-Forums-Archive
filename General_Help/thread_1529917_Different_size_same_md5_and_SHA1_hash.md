---
title: "Different size same md5 and SHA1 hash?"
date: 2010-07-12
forum: General Help
---

### Post by xzased on 2010-07-12
We have a file that we believe may be corrupt. Its a .wim image. We have 4 copies and 3 of them have this size according to du:

```
du image.wim
2317580	
```

On the one it differs it gives this output:

```
du image4.wim
2316820	
```

Is it possible for this image to be different in size and still have the same sum? Could it be corrupt? Thanks in advance.

---

### Post by Sef on 2010-07-12
If the md5sum and the sha1 hash check out the same as the respective numbers that are given, then there is nothing to worry about.

---

### Post by xzased on 2010-07-13
Thanks Sef.

---

### Post by dcstar on 2010-07-14
> **xzased said:**
> We have a file that we believe may be corrupt. Its a .wim image. We have 4 copies and 3 of them have this size according to du:

```
du image.wim
2317580	
```

On the one it differs it gives this output:

```
du image4.wim
2316820	
```

Is it possible for this image to be different in size and still have the same sum? Could it be corrupt? Thanks in advance.

If both files are stored on different filesystems, then if the respective block sizes are different the **disk usage** of the file may well be different.

Disk usage <> file size.

---

