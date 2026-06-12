---
title: "Deleting files - Overwriting the actual physical disk space"
date: 2010-07-12
forum: General Help
---

### Post by irlforum on 2010-07-12
Hi,
When I delete some files off my machine I want to delete them properly and not just make the space available to be reused by the OS.

Does the rm command do this or what is the handiest way to do it?

Thank you.

---

### Post by audiomick on 2010-07-12
In order to make sure the file is not recoverable, you need to use a tool that physically writes into the space, thereby actively overwriting the data.

One tool is shred. You can read how to use it in the manual page. Open the manual page with
```
man shred
```

---

### Post by irlforum on 2010-07-12
That's very handy. Thanks for the quick response and hello aswell as I'm new here.

---

### Post by TheForumTroll on 2010-07-12
If you want a GUI and some extra cleaning options BleachBit is worth a look.

---

### Post by DaveHi on 2010-07-12
Hi iriforum

Don't know what data you are trying to protect, or how sensitive it is, but, please be aware that the chances are you are using a journalling file system. This means that even when you over-write the file itself some information will be retained in the journal, not to mention any indexing search programs you may have installed .

For most of us BleachBit or shred are more than adequate for our needs, but, if you have more serious requirements I would suggest looking for some more expert help.

---

