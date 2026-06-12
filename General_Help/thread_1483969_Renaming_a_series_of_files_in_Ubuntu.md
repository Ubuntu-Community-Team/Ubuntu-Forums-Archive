---
title: "Renaming a series of files in Ubuntu"
date: 2010-05-15
forum: General Help
---

### Post by nandugopan on 2010-05-15
Hi all,

I want to use Ubuntu to rename a series of files. All my files are in a single folder. And there name follows the pattern: out.cu.#####, where #### denotes a number.

E.g: out.cu.10000 
       out.cu.11000
............................

I want to rename each of these files as the number alone. That is out.cu.3500 should get renamed to 3500.

How can one do this? I Googled 'renaming a series of files' and scripts came up. They didnt  work for me.

---

### Post by sarang on 2010-05-15
Try this:

[FONT="Courier New"]cd[/FONT] to the directory with the files and run:

```

for i in out.cu.*; do newname=$(echo $i | sed 's/.*\.//'); mv $i $newname; done

```

---

### Post by StuartN on 2010-05-15
> **nandugopan said:**
> I want to use Ubuntu to rename a series of files. All my files are in a single folder.

```
rename 's/out.cu//' out.cu*
```

Try **man rename** for more information or search for "batch rename" for alternative solutions - for instance a lot of image browser applications have good batch file renaming utilities.

---

### Post by nandugopan on 2010-05-15
Thank you guys for the prompt replies

@StuartN: well, the code you suggested, does nothing. I enter it, and everything is same as before..Thanks for the help anyway.

@sarang : yes..thats exactly what I wanted..Thanks a lot !
:P:P:P

---

### Post by StuartN on 2010-05-15
> **nandugopan said:**
> @StuartN: well, the code you suggested, does nothing. I enter it, and everything is same as before..Thanks for the help anyway.

You can use rename -n to see what would happen with a batch rename, without changing any filenames, which should indicate why the command you used failed.

---

