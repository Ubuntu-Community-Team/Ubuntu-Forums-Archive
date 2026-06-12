---
title: "replace or delete special characters in file and folder names, recursively?"
date: 2012-03-15
forum: General Help
---

### Post by potiphera on 2012-03-15
I have a Windows computer with some files and folders on it that were created in Ubuntu. Some of the file and folder names have characters that are not allowed in Windows. Using an Ubuntu live CD, how do I recursively replace or delete those special characters?

---

### Post by ofnuts on 2012-03-15
> **potiphera said:**
> I have a Windows computer with some files and folders on it that were created in Ubuntu. Some of the file and folder names have characters that are not allowed in Windows. Using an Ubuntu live CD, how do I recursively replace or delete those special characters?AFAIK you don't need that... in Windows you can use "ren weird*character.txt weird_character.txt" (if you can't enter the character (s) between "weird" and "character").

---

### Post by lrgmmc on 2012-03-15
I've always liked using pyRenamer. It's in the repo's and it allows mass renaming of files. You can replace or remove special characters with it.

---

### Post by garyed on 2012-03-15
I would use the sed command to do it. I don't know the actual syntax but I'm sure if you google it you'll find it easily.

---

### Post by potiphera on 2012-03-15
I ended up taking lrgmmc's suggestion and using pyRenamer because I was already somewhat familiar with it, but wasn't aware that it could rename directories as well as files, or work recursively.

For anyone else who didn't know that, I should note that you can enable those modes in the options sidebar (press F9 to display it, or go to **View>Show options**, or click the icon at the upper right).

Thanks, everyone!

---

