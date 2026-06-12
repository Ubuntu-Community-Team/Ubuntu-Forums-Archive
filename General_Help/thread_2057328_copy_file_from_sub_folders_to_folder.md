---
title: "copy file from sub folders to folder?"
date: 2012-09-13
forum: General Help
---

### Post by sohlinux on 2012-09-13
How can I copy all files from a folder and all sub folders in to another folder?

example

copy all images from the following folders
folder1 (has 100 images)
folder2 (has 100 images)
folder3 (has 100 images)
folder4 (has 100 images)

copy them to a new folder "folder5 (which will then have 400 images inside "not the folders, only the images)

but if the images have the same name then auto rename them?

thanks

---

### Post by sohlinux on 2012-09-13
I figured out the copy part but I dont know how to do the rename if the same file name exists?

find -iname "*jpg" -exec cp "{}" /new_folder/. \;

---

### Post by sisco311 on 2012-09-13
You need a [glob]("http://mywiki.wooledge.org/glob") which matches all the files. Then you can use the cp command with its --backup option to copy them to the new directory. Something like:

```
cp --backup=numbered -- */*.jpg directory5
```

---

### Post by sohlinux on 2012-09-13
> **sisco311 said:**
> You need a [glob]("http://mywiki.wooledge.org/glob") which matches all the files. Then you can use the cp command with its --backup option to copy them to the new directory. Something like:

```
cp --backup=numbered -- */*.jpg directory5
```

thanks ;)

---

