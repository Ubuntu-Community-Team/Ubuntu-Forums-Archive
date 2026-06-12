---
title: "List Folder Contents"
date: 2011-07-20
forum: General Help
---

### Post by kexus on 2011-07-20
I know that you can use *ls* to list the files in a folder, but is there anyway to list the contents of the other folder?  Like, say I have a folder labelled "Records", and inside is 12 folders, one for each month.  Is there any way to list the contents of the 12 subfolders without just going into each one with *cd *and using *ls*?

---

### Post by TeoBigusGeekus on 2011-07-20
```
du -ha
```

---

### Post by mcduck on 2011-07-20
> **kexus said:**
> I know that you can use *ls* to list the files in a folder, but is there anyway to list the contents of the other folder?  Like, say I have a folder labelled "Records", and inside is 12 folders, one for each month.  Is there any way to list the contents of the 12 subfolders without just going into each one with *cd *and using *ls*?

Sure, that's what the "-R" option for *ls* is for.

For example:
```
ls -R ~/Music/Records
```

---

### Post by seawolf167 on 2011-07-20
As previously stated, you can either use the recursive option to list all subdirectories and their contents

```
ls -R
```you can also type the location of the folder you want to list the contents of

```
ls /path/to/your/folder
```or use them together

```
ls -R /path/to/your/folder
```

For commands, you can view their man pages for more help

```
man *commandname*
```

---

