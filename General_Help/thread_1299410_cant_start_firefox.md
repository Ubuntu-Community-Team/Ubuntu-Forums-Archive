---
title: "cant start firefox"
date: 2009-10-23
forum: General Help
---

### Post by Switch08 on 2009-10-23
When I try to start firefox 3.5 I get the following error.

The application has been updated, but your version of SQLite is too old and the application cannot run.

can someone please help me.

---

### Post by collinp on 2009-10-23
Little more information needed:

Did you recently install updates?
If so, do you remember Firefox being listed as one?

---

### Post by Switch08 on 2009-10-24
I have Ubuntu 9.10 and Firefox 3.5 was working.

Both sqlite3 and libsqlite3-0 are installed and I tryed deleting all .sqlite endings in .mozilla/firefox's profile folder and I tried renaming the .ini file and have tottaly deleted everything in .mozilla/firefox folder.

This made Firefox ask a question about importing plugins and then the following pops up from there.

The application has been updated, but your version of SQLite is too old and the application cannot run.

thank you

---

### Post by Switch08 on 2009-10-25
anyone?

---

### Post by Knapweed on 2009-10-30
> **Switch08 said:**
> anyone?

I had a similar issue. The problem turned out to be an old version of a sqlite library that I had built from source and installed in /usr/local/lib and then long since forgotten about. 

The fix was simple:

```
sudo rm /usr/local/lib/libsqlite*
```

-tk

---

### Post by Switch08 on 2009-10-31
Thankyou for the reply i still have the issue but been getting by downloading firefox 3.ob3

every entry in /usr/local/lib

is libsglite3 is it save to remove these entries since thiis is the current version?

---

### Post by tjk on 2009-11-10
> **Knapweed said:**
> I had a similar issue. The problem turned out to be an old version of a sqlite library that I had built from source and installed in /usr/local/lib and then long since forgotten about. 

The fix was simple:

```
sudo rm /usr/local/lib/libsqlite*
```-tk

Thanks for this fix, Knapweed.  I upgraded to 9.10, and then couldn't open FF3.5 because of this error... now it's running fine again.

---

### Post by lyzby on 2009-11-11
Same problem after upgrade to 9.10.  Fixed as suggested above by:

sudo rm /usr/local/lib/libsqlite*

Thanks.

---

