---
title: "(Probably Easy) LS Question"
date: 2009-08-07
forum: General Help
---

### Post by IAmNotAUser on 2009-08-07
I've tried looking online extensively for this, and can't seem to find an answer. In the man page for ls it says: "-F, --classify             Append indicator (one of */=@|) to entries", however I cannot seem to find any definition as to what each of the indicators actually means.

Can anyone please help?

---

### Post by IAmNotAUser on 2009-08-08
Anyone?

---

### Post by dcstar on 2009-08-08
> **IAmNotAUser said:**
> Anyone?

If you run the command you can quickly see the "/" means a folder, and the others will mean whatever applies to the entry.

---

### Post by abhilashm86 on 2009-08-08
actually * means a metacharacter, if you have done lot of c++ programs in your home directory /home/username, then
```

ls *.cpp -l

```
this would list all c++ files along with the basic attributes.......

---

### Post by IAmNotAUser on 2009-08-09
After a long hunt around the net I finally found the answer:

/ File is a directory.
* File is executable.
@ File is a symbolic link.
| File is a FIFO (also called a named pipe), a special file that processes use for reading from and writing to.
= File is a socket, a special file that provides a connecting point through which processes may communicate.

Posting here in case others come to the thread looking for the answer.

---

