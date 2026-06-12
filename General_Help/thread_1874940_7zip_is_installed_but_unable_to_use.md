---
title: "7zip is installed but unable to use"
date: 2011-11-04
forum: General Help
---

### Post by aoniumo on 2011-11-04
I have just installed 7zip from software center.  This is the first program I installed after upgrading to 11.10, but it seems to be missing from my application list.  I have the screencap attached.

---

### Post by Telengard C64 on 2011-11-04
> **aoniumo said:**
> it seems to be missing from my application list.

It is a command line tool. Invoke it like this:

```
7z a archive_name.7z files_to_archive
7z x archive_name.7z
7z --help
man 7z
```

HTH

---

### Post by mike555 on 2011-11-04
You should see it as an option when rt. clicking on a file and picking "create archive".

---

### Post by 3rdalbum on 2011-11-04
On Linux, you don't need a different graphical archive manager for each type of file that you want to work with.

The 7zip package that you installed just allows the regular archive manager (File Roller) to work with 7zip archives.

All you need to do is double-click a 7z archive and it will open in the File Roller archive manager.

---

