---
title: "Md5"
date: 2005-02-01
forum: General Help
---

### Post by mariuss on 2005-02-01
Hi,

I downloaded the latest Hoary Live CD from:
```
http://cdimage.ubuntu.com/releases/hoary/array-3.5-live/hoary-live-i386.iso
```

During start up it complains that the CD is corrupted and a CD test fails. Now, I am not sure what went wrong, the download or the burning.

The problem is that there is no MD5 for the iso so I can test the download. Could someone post the MD5 for this file?

Thanks,
Marius

---

### Post by alastair on 2005-02-02
[QUOTE=mariuss]Hi,

I downloaded the latest Hoary Live CD from:
```
http://cdimage.ubuntu.com/releases/hoary/array-3.5-live/hoary-live-i386.iso
```

During start up it complains that the CD is corrupted and a CD test fails. Now, I am not sure what went wrong, the download or the burning.

The problem is that there is no MD5 for the iso so I can test the download. Could someone post the MD5 for this file?

Thanks,
Marius[/QUOTE]
 This file :

[http://cdimage.ubuntu.com/releases/hoary/array-3.5-live/MD5SUMS](http://cdimage.ubuntu.com/releases/hoary/array-3.5-live/MD5SUMS)

has the MD5 sums. Containing :

c4393b51dba477f9b5ddaa81f062111f  hoary-live-amd64.iso
c512b3e1cc389e1309104bf288fb7d85  hoary-live-i386.iso
974f4d42f96d20d26327aa2950dd0ac2  hoary-live-powerpc.iso

I downloaded "hoary-live-i386.iso" from somewhere else (I think) and :

[alastair@persephone ubuntu]$ md5sum hoary-live-i386.iso
c512b3e1cc389e1309104bf288fb7d85  hoary-live-i386.iso
[alastair@persephone ubuntu]$

---

### Post by mariuss on 2005-02-02
Thanks a lot.

---

