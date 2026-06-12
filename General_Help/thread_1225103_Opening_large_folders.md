---
title: "Opening large folders"
date: 2009-07-28
forum: General Help
---

### Post by dwally89 on 2009-07-28
Hi,

I have a folder with a lot of files in it, and consequently every time I try to open the folder in nautilus, nautilus crashes.

How can I open this folder?

Thanks

---

### Post by wojox on 2009-07-28
The Terminal

Move to the directory it is and type:

```
ls
```

---

### Post by dwally89 on 2009-07-28
Can I make it sort out the output via size? (Descending)

---

### Post by wojox on 2009-07-28
```
ls -ltu
```

---

### Post by nikhilk on 2009-07-28
> **wojox said:**
> ```
ls -u
```

The man page for ls says
"-S     sort by file size"

So the command should be```
ls -S
```

Although beware that the directory order has nothing to do with the size of its contents. So you are seeing real size of files only in that output.

---

### Post by coffeecat on 2009-07-28
> **dwally89 said:**
> I have a folder with a lot of files in it, and consequently every time I try to open the folder in nautilus, nautilus crashes.

Opening a folder with a lot of files in Nautilus can be slow - for example, if I open my /usr/bin with 2028 items, I get the little spinning wheel for a few seconds before the contents display - but if Nautilus is crashing I would have thought something is wrong. 

How many files are in this folder?

---

### Post by pmlxuser on 2009-07-28
sometimes when am really frustrated all i do is open command prompt and then

```

$ nautilus /specific_folder_within_that_folder

```

works well if you know which folder you want, but since the command prompt also give auto completes if you start a folder name it still works if you have an idea of the starting letters.

---

