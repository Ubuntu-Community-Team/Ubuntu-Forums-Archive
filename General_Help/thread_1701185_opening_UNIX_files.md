---
title: "opening UNIX files"
date: 2011-03-06
forum: General Help
---

### Post by Spyderkid on 2011-03-06
how would i be able to open a old UNIX file on a floppy? it doesn't work automatically

---

### Post by peculiar penguin on 2011-03-06
Define "UNIX file". Unix is a family/group of operating systems, so your question doesn't make much sense. If you don't know anything about the file, try using "file" on the command line:
```
file your_file_here
```or open it in a text and/or hex editor and look for readable text strings that may give you a clue.

---

### Post by Spyderkid on 2011-03-06
thats the thing it can't read it so i don't know what filetype it is. its a floppy

---

### Post by AlphaLexman on 2011-03-06
Is the floppy formatted?
What filesystem is it?
Can you mount the disk?
Can you open nautilus and see the disk contents?
Can you retrieve the filename?
What is the output of **ls** from a terminal?

---

### Post by Spyderkid on 2011-03-07
its still got the data on it i cannot open it and it doesn't recognise there is a floppy there and doesn't mount

---

### Post by AlphaLexman on 2011-03-07
Your first goal should be to get the floppy drive mounted. You won't be able to do anything until it is mounted.

Not knowing what filesystem the disk is formatted in may cause some problems with me helping you. So check out [https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")

Another option would be to run the program **gparted** and point it to /dev/fd0 or if you have more than one floppy drive, /dev/fd1. It should give you info on partitions and filesystems.

---

### Post by Spyderkid on 2011-03-08
its an external floppy driver plugged into USB does that complicate thing at all?

---

### Post by psusi on 2011-03-08
Post the output of the following command:
```

sudo blkid

```

---

