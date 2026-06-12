---
title: "file permission"
date: 2006-05-09
forum: General Help
---

### Post by RajivNair on 2006-05-09
whenever i copy paste anything frm my cd onto my hdd,it appears with a lock sign on it.its a sign to indicate that i dont have write access to the copied file or directory.can i change it by default,so that i have write permissions to the files and folder i copy.

---

### Post by GNUrag on 2006-05-09
[QUOTE=RajivNair]whenever i copy paste anything frm my cd onto my hdd,it appears with a lock sign on it.its a sign to indicate that i dont have write access to the copied file or directory.can i change it by default,so that i have write permissions to the files and folder i copy.[/QUOTE]

Since CD/DVD is a read only medium, all the files you copy from CD/DVD will not have any write permission. What you can do is manually add write permission to the directory.  In Konqueror you can go to properties, add write permission and apply it to all the subdirectories. 

If you are comfortable with command line then something like this can be done. 

**$ find ~/music/ -name "*.wmv" -exec chmod u=rw,go=r {} \;**

Here,
1) Find command searches for filenames ending with *.wmv..
2) On every successful match, it executes chmod 644 ...
3) {} is translated to the current filename being traversed.
4) \; signifies that -exec command has ended.

Here we assume that you have copied the files from your CD/DVD to ~/music directory.

---

### Post by RajivNair on 2006-05-09
im using ubuntu,so no konqueror.do u know anything similar that can be done in nautilus.also the pain is,if i give a write permission to a folder all its sub folders and files then show the lock sign.so is there anyway i can make the content of a whole directory have write permission by changing the permission of the parent folder.

---

### Post by Sutekh on 2006-05-09
Sure, use the **-R** recursive option
```
chmod +w **-R** /<some folder>
```
 - the +w adds write permissions
 - the **-R **option changes all files and subfolders underneath /<some folder>

---

### Post by RajivNair on 2006-05-09
thnx a lot guys for ur help.

---

