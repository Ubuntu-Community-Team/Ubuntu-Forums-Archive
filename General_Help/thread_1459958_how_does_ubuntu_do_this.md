---
title: "how does ubuntu do this?"
date: 2010-04-22
forum: General Help
---

### Post by sxmaxchine on 2010-04-22
i have noticed that ubuntu does not require you to have file extenions for example i have a mp4 video file and even if i remove the .mp4 it still recognizes it as an mp4 file.

this made me curious so i looked on the internet and read that ubuntu does not require file extensions.

so my question is:
how does ubuntu know what type of file it is

---

### Post by spoon_ on 2010-04-22
It probably checks the header of the file. Most file types have some distinctive pattern in the first few bytes.

---

### Post by unmole on 2010-04-22
Ubuntu like any other UNIX-like operating system comes with a program called file. What file does is, it looks for so called 'magic numbers' in a file and determines what kind of a file it is.

[This]("http://en.wikipedia.org/wiki/File_(command)") might help, just a little.

---

### Post by Dayofswords on 2010-04-22
like he said
[SIZE="6"]**Magic!**[/SIZE]



(but yeah, just reads the header)

---

### Post by sxmaxchine on 2010-04-22
thankyou for the answers

---

