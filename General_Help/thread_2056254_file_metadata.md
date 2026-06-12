---
title: "file metadata"
date: 2012-09-11
forum: General Help
---

### Post by engine on 2012-09-11
Any way of adding metadata to plain text files via Nautilus? I have hundreds of music scores where I'd like to be able to see/save more than just the filename, and don't really want to go as far as a document management system.

---

### Post by LewisTM on 2012-09-11
You can install package **eiciel**. It will add a couple of tabs in your Nautilus file properties, including extended user attributes. 
In that tab, you can add a number of user fields with names and contents. If you want multiple lines just copy from a text editor and paste into the field.

Two (minor) limitations:
1) There is no way to know that a file has been commented based on its Nautilus icon.
2) You can't do a GUI search of the attributes. 
The command
```
getfattr -Rd <base directory>
```
will print out all file comments.

Cheers!

---

