---
title: "error splicing file: fill too large"
date: 2011-08-20
forum: General Help
---

### Post by sdibaja on 2011-08-20
I am trying to copy a 6.8 GB file from a local hard drive to a portable USB drive and it fails. I get "error splicing file: fill too large" message.
This is surprising, maybe I need to reset something.

any ideas?

Thanks, Peter

---

### Post by elgordodude on 2011-08-20
Any chance the USB is formatted with FAT32? If not, how is it formatted, and the drive is at least 8 GB right?

---

### Post by sdibaja on 2011-08-20
> **elgordodude said:**
> Any chance the USB is formatted with FAT32? If not, how is it formatted, and the drive is at least 8 GB right?

Yes, it is formatted to FAT... not being very smart this morning ;)

problem solved

.... how do I delete this thread, or mark it Solved?

---

### Post by AlphaLexman on 2011-08-20
I think elgordodude has identified the problem, certain filesystems have limitations to the maximum file size. See [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits")

---

