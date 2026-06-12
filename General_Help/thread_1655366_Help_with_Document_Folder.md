---
title: "Help with Document Folder"
date: 2010-12-29
forum: General Help
---

### Post by Metungkp on 2010-12-29
Third day with ubuntu and loving it so far.  Well, I hope to continue to love it, I am unable to open "Documents".  It says, unable to open document and can't open directory.  Okay, I have a year worth of work in that folder.  Please help me fix this issue?


Thanks!
KP

---

### Post by requeth on 2010-12-29
Where did the directory come from? A different Linux box? Windows? Do you know if the filesystem was encrypted? Does your user own the files? Try running:

sudo chown -R username /Documents

I've subscribed to this thread so post back and I'll respond.

---

### Post by nothingspecial on 2010-12-29
> **requeth said:**
> Where did the directory come from? A different Linux box? Windows? Do you know if the filesystem was encrypted? Does your user own the files? Try running:

sudo chown -R username /Documents

I've subscribed to this thread so post back and I'll respond.

That should be 

```
sudo chown -R username ~/Documents
```

In most cases.

And I repeat, what have you done?

---

### Post by gordintoronto on 2010-12-29
One of the adjustments in using Linux is that "Documents" and "documents" are different!

---

### Post by bhgrove on 2010-12-30
a quick work around when you get that message just click on file and open

---

