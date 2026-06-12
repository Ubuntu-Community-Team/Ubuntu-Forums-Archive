---
title: "Transferring very large files"
date: 2009-09-05
forum: General Help
---

### Post by alan_uk on 2009-09-05
I need to to transfer one single 7.3 GB file to my second storage hard drive. All attempts result in a warning that the file is too big to move. Anybody know of a way of doing this or splitting and copying to DVD? Thanks Alan

---

### Post by Liolikas on 2009-09-05
[http://www.computerhope.com/unix/usplit.htm](http://www.computerhope.com/unix/usplit.htm)

---

### Post by whitethorn on 2009-09-05
Do you know how your second hd is partitioned?  Some filesystems don't allow bigger sized files here's a list

[http://www.nch.com.au/express/kb/1237.html](http://www.nch.com.au/express/kb/1237.html)

---

### Post by amac777 on 2009-09-05
Does rsync report file is too big to copy?????

```
rsync /source_directory/file /target_directory/
```

---

### Post by alan_uk on 2009-09-05
Ah yes that is probably the problem the second hard drive is FAT32 formatted thereby exceeding the 4GB max. Also thanks for the advice on splitting the file, and the rest. Cheers Alan

---

