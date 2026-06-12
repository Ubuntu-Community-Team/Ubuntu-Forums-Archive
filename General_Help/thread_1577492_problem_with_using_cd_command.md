---
title: "problem with using cd command"
date: 2010-09-18
forum: General Help
---

### Post by ipey on 2010-09-18
I cannot change directory to a more than three folder tree destination folder from ~ in terminal. I've checked everything. No Typos or misspell. The destination folder was recognized by "ls" command but when I went to it, the terminal said, "no such file or directory." Please help...

regards,
:)

---

### Post by mc4man on 2010-09-19
You might want to post your ls

Otherwise try something simple - 
Browse to your destination dir. in your file manager so you can see it

Then open a terminal, type cd and hit the spacebar.
Drag and drop the dest. dir into the terminal window, click anywhere in the terminal to return focus and press enter.

See what path it shows

( do any of the dir.'s in your tree have a space **after** the name?

---

### Post by neoargon on 2010-09-19
This problem is there with my desktop version of ubuntu too . The problem began at the karmic time

---

### Post by CharlesA on 2010-09-19
> **neoargon said:**
> This problem is there with my desktop version of ubuntu too . The problem began at the karmic time

Have you used tab completion to fill in the names of the directories?

Works for me in Lucid desktop. *shrug*

---

### Post by ipey on 2010-09-19
thank you for your responses

> do any of the dir.'s in your tree have a space **after** the name?

there are two folders with two word phrases as their names if that is what you mean.

this is the ls from ~/Documents$:
 
> acpi4asus-0.41  Back up  Berkas  Bobodoran Kang Ibing  Ebook  kanggo skripsi  Linux   lost+found 
"cd /home/username/Documents/Linux" gave the "no file or directory" thing.
I also tried your suggestion. it created > cd '/home/ipey/Documents/Linux ' and it worked!

so what is actually my mistake?

---

### Post by Old *ix Geek on 2010-09-19
> **ipey said:**
> "cd /home/username/Documents/Linux" gave the "no file or directory" thing.

I also tried your suggestion. it created  
```
cd '/home/ipey/Documents/Linux '
```
and it worked!

so what is actually my mistake?Is the space at the end of the second example intentional? If so, there's your problem--the directory you think is named **Linux** is actually named **Linux **.

If you try:

```
cd /home/ipey/Documents/Linux*
```

what happens?

---

### Post by mc4man on 2010-09-19
> so what is actually my mistake? 
Sometimes when naming a folder you can inadvertently add a space to the end of the name.
In this case the folder's real name was Linux<space>

Just r. click - rename it and if you click in the box - you'll see the cursor is one space away from the x
(you can just backspace the space away...

---

### Post by ipey on 2010-10-20
ah, devil lies in details. thanks a lot.

---

