---
title: "can I print all files in a directory in a single command?"
date: 2010-11-23
forum: General Help
---

### Post by amulet on 2010-11-23
Hello,
I have no great comprehension of scripts, but I do have many files (mostly .pdfs) in a directory and sub directories that I would like to print without opening each file.

Is there a way to do this in the terminal with a magical command or two?

Thank you

---

### Post by lmarmisa on 2010-11-23
> **amulet said:**
> Hello,
I have no great comprehension of scripts, but I do have many files (mostly .pdfs) in a directory and sub directories that I would like to print without opening each file.

Is there a way to do this in the terminal with a magical command or two?

Thank you

I suppose you have installed the package cups.

Check in System -> Administration -> Printing if the printer defined as default is that you wish.

Select a small pdf file (only 1 page is perfect for the test) and type this command:

```

lpr filetoprint.pdf

```

---

### Post by rjaymo on 2010-11-23
u could just dir *.pdf > temp file.
edit the temp file to add the lpr command at the beginning.
may work.

---

### Post by amulet on 2010-11-24
Great!

It really is as easy as that - Change directory and print all pdfs.

cd ~/

lpr *.pdf 


For a Terminal phobic I think I did well!

Many Thanks

---

