---
title: "Hide Filesystem"
date: 2011-05-25
forum: General Help
---

### Post by mantle7717 on 2011-05-25
on my last installation of natty i found a terminal entry on some random forum that allowed me to hide the contents of my file system using chmod. i was wondering if any one knows how to do this

---

### Post by wildmanne39 on 2011-05-26
> **mantle7717 said:**
> on my last installation of natty i found a terminal entry on some random forum that allowed me to hide the contents of my file system using chmod. i was wondering if any one knows how to do this

Hi, any file with a dot in front of it will be hid  you will have to go to your home folder and hit ctrl h to unhide it.

---

### Post by fdrake on 2011-05-26
well u can hide the content of a directory so that it wont list the file that contains to anyone but the owner with

```
chmod go-xwr -R directory
chmod u+rwx -R directory
```

by making a directory -x it will not list any file in it. By making it -r you wont be able to move on it. correct me if i am wrong!

---

### Post by mantle7717 on 2011-05-27
on my last installation of natty i was able to make all the folders in my filesystem hidden, i then created links to all of the folders, reorganized them and renamed them thus creating a moon os style simple filesystem, i just want to know how i can do this again ... any help would be appreciated. :)

---

### Post by Ozymandias_117 on 2011-05-27
The closest thing I can think of to what you're referring to, making files/folders hidden without renaming them, as long as you're only meaning they're hidden in Nautilus (The default file browser in Ubuntu), you can create a file named ".hidden" and put all the files/folders you want hidden one per line in that file.

---

