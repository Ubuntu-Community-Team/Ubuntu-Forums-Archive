---
title: "How do you batch extract multiple archives to their own folders?"
date: 2011-08-29
forum: General Help
---

### Post by Euvius on 2011-08-29
I have a bunch of archives I want to extract, so I select them all, right-click in Nautilus, but there's no option to extract each archive to its own folder.  Instead, the contents of the archives all get extracted loose.  I want to extract each archive into its own folder, with the folder name being the archive name.  Thanks

---

### Post by seawolf167 on 2011-08-29
Maybe a simple bash script to do the job?

```
#!/bin/bash
for file in *.tar.gz
do tar -xzf "$file"
```

---

### Post by Euvius on 2011-08-29
I have various archive types (zip, rar, tar.gz, etc).  Also, is there a way to make that bash script appear as a right-click option?

---

### Post by seawolf167 on 2011-08-29
Perhaps?

```
#!/bin/bash
for file in /source/directory/*
do
case "$file" in
     *.tar) tar -xf "$file" ;;
     *.tar.gz) tar -xzf "$file" ;;
     *.tar.bz2) tar -xjf "$file" ;;
     *.zip) unzip "$file" -d "${file%.*}" ;;
     *) ;;
esac
done
```I'm not sure how to add as a right-click menu item.

---

### Post by Euvius on 2011-08-29
Ok, thanks for the help :)

---

### Post by blueridgedog on 2011-08-29
To access the script via a right click menu:

[https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto)

---

### Post by Euvius on 2011-08-29
Nice, thanks

---

