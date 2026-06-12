---
title: "recursively rename file extensions?"
date: 2011-02-15
forum: General Help
---

### Post by sohlinux on 2011-02-15
I want to rename some image file extensions from upper case to lower case but renaming all the images in all directories and subdirectories.

the following code works if I am inside the folder but how do I make it work recursively?

```
for f in *.JPG; do mv $f `basename $f .JPG`.jpg; done;
```

---

### Post by TeoBigusGeekus on 2011-02-15
Try
```
for f in $(ls -R / |grep jpg); do mv $f `basename $f .JPG`.jpg; done;
```

---

### Post by sohlinux on 2011-02-15
> **TeoBigusGeekus said:**
> Try

```
for f in $(ls -R / |grep jpg); do mv $f `basename $f .JPG`.jpg; done;
```

thanks but for some reason that didn't work even after adding the directory path /home/user/Pictures however I did manage to do it with the following code while inside the pictures directory...

```
find ./ -type f -name "*.JPG" | while read FILE do newname=`echo $FILE | sed s/.JPG/.jpg/` echo $newname mv "$FILE" "$newname" done
```

---

