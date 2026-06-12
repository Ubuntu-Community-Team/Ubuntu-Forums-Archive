---
title: "Cant Delete This Folder."
date: 2010-03-27
forum: General Help
---

### Post by soryu on 2010-03-27
I Have A Folder On My Desktop With A Lock Icon On It. I've Tried To Delete It But I Get A Message Saying Cant Delete. I Look At Details And It Say's  Permission Denied.
I Didn't Lock It.
How Do I Delete It?

---

### Post by Directive 4 on 2010-03-27
sudo nautilus

---

### Post by soryu on 2010-03-27
folder Isn't there??

---

### Post by linuxuser21 on 2010-03-27
In the command prompt: ```
sudo rmdir <path/to/file>
```
Drag the file to the command prompt to have the file path put in automatically.

---

### Post by quadproc on 2010-03-27
> **soryu said:**
> I Have A Folder On My Desktop With A Lock Icon On It. I've Tried To Delete It But I Get A Message Saying Cant Delete. I Look At Details And It Say's  Permission Denied.
I Didn't Lock It.
How Do I Delete It?
The particular folder is probably either read-only or a link.  You might succeed by changing the folder's permissions to 777, or follow the link and change or remove the parent file/folder.  The file command might also give some useful info:```
file <the locked directory>
```

quadproc

---

### Post by linuxuser21 on 2010-03-27
If that doesn't work, try changing the permissions and owner by:
```
sudo chown -R <username>:<username> <path/to/file>

sudo chmod -R 777 <path/to/file>
```

EDIT: Sorry quadproc, didn't see your post. :(

---

### Post by soryu on 2010-03-27
got it . went to folder properties>permissions- folder access and changed it to create and delete files. it was access only.

---

