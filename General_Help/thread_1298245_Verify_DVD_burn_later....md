---
title: "Verify DVD burn later..."
date: 2009-10-22
forum: General Help
---

### Post by Earl_Maroon on 2009-10-22
Earlier today I burnt an ISO to a DVD using K3b but I didn't verify the write.

How can I verify that the DVD burnt accurately at this point? Is there some sort of checksum I can do? K3b doesn't seem to allow me to do it at this point.

---

### Post by vinutux on 2009-10-22
k3b have an option to verify ........

---

### Post by Earl_Maroon on 2009-10-22
> **vinutux said:**
> k3b have an option to verify ........  k

I know, but only when you burn a disk. I already have the disk and want to check it, which K3b doesn't seem to give me the option to do. It only allows me to verify the written data straight after writing it.

---

### Post by vinutux on 2009-10-22
After burn... i don't think so.........

---

### Post by vinutux on 2009-10-22
Just fond this for creating checksum ...in terminal

```
md5sum -b [COLOR="Red"]/Pathtoyourfileorcondent[/COLOR]
```

and verify checksum and cd with **[COLOR="YellowGreen"][20G Hashgen ]("http://20gp.com/index.php?option=com_jdownloads&Itemid=57&task=view.download&cid=1")[/COLOR]**

i am not tested yet...........

---

### Post by Earl_Maroon on 2009-10-22
Thanks. I'll give that a shot.

---

### Post by alphaniner on 2009-10-22
I usually use **md5deep** to checksum all files (redirecting the output to a file) before burning, then use **md5sum -c** to check the files on disc against the stored checksums.  If you still have the source files, you may be able to do something similar.

---

### Post by vinutux on 2009-10-22
> **alphaniner said:**
> I usually use **md5deep** to checksum all files (redirecting the output to a file) before burning, then use **md5sum -c** to check the files on disc against the stored checksums.  If you still have the source files, you may be able to do something similar.

.........Thanks.................////

---

