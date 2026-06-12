---
title: "Xcopy, I know somebody here knows this goody"
date: 2010-11-30
forum: General Help
---

### Post by ibootindos on 2010-11-30
I know this is a Ubuntu forum, but there's some damn smart people here, and I was hoping somebody could help me out. 

I'm in recovery manager trying to move files off the computer onto a thumb drive, yes I only have a thumb drive so I don't want to use the backup Utility. I'm using the command prompt and have a ton of picture folders and sub folders that I'd like to copy before resetting the computer to factory settings, I know that Xcopy will help me do it, I just don't know how. I want to copy every single document from the pictures folder. anybody have any idea how?

---

### Post by c2tarun on 2010-11-30
> **ibootindos said:**
> I know this is a Ubuntu forum, but there's some damn smart people here, and I was hoping somebody could help me out. 

I'm in recovery manager trying to move files off the computer onto a thumb drive, yes I only have a thumb drive so I don't want to use the backup Utility. I'm using the command prompt and have a ton of picture folders and sub folders that I'd like to copy before resetting the computer to factory settings, I know that Xcopy will help me do it, I just don't know how. I want to copy every single document from the pictures folder. anybody have any idea how?


try
```

xcopy <source folder name> <destination folder name> /s

```

omit the tags

---

