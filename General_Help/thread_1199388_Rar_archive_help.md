---
title: "Rar archive help"
date: 2009-06-28
forum: General Help
---

### Post by Vikhyath on 2009-06-28
How can i join split .rar files and extract them to another location simultaneously

---

### Post by jerome1232 on 2009-06-28
Using unrar you should be able to just tell it to extract from the first part of the archive and it'll automatically extract from the other parts as well.

---

### Post by michy99 on 2009-06-28
Are these files that were split by rar (file.part1.rar, file.part2.rar. etc) or a single rar file that was split afterwards (file.rar.001, file.rar.002, etc.)?

---

### Post by Vikhyath on 2009-06-28
> Are these files that were split by rar (file.part1.rar, file.part2.rar. etc) or a single rar file that was split afterwards (file.rar.001, file.rar.002, etc.)?
I think its like file.r01,file.r02,etc.

---

### Post by Vikhyath on 2009-06-28
Please note: I want to extract the files into another partition because I've run out of space in the one which contains the rar file

---

### Post by moster on 2009-06-28
Maybe some of rar files have slighty different name and unrar cannot recognize it. Or corrupted archive. I hate to recommend something like this, but I guess you have some specific problem.

If you already have wine, just install winrar in Ubuntu. It will work just fine, but you anyway better next time stick to native apps.

---

### Post by Vikhyath on 2009-06-28
> **moster said:**
> Maybe some of rar files have slighty different name and unrar cannot recognize it. Or corrupted archive. I hate to recommend something like this, but I guess you have some specific problem.

If you already have wine, just install winrar in Ubuntu. It will work just fine, but you anyway better next time stick to native apps.

I tried winrar but it doesn't have the feature to extract split files into a different location

---

### Post by michy99 on 2009-06-28
The archive manager will do this just fine. Right click on the first file. Open with archive manager. When you click on extract, you can choose where you want to extract to.

---

### Post by Vikhyath on 2009-06-28
> **michy99 said:**
> The archive manager will do this just fine. Right click on the first file. Open with archive manager. When you click on extract, you can choose where you want to extract to.

But the archive manager does not seem to recognise the file

---

### Post by moster on 2009-06-28
hehe, you probably have splitted file, probably with hjsplit or something else. Ok, you now need to combine it somehow, I never do that myself on linux but it can be done. Try with this

[http://manpages.ubuntu.com/manpages/jaunty/man1/combine.1.html]("http://manpages.ubuntu.com/manpages/jaunty/man1/combine.1.html")

or this, it has nice GUI

[http://www.freebyte.com/hjsplit/#linux]("http://www.freebyte.com/hjsplit/#linux")

---

### Post by Vikhyath on 2009-06-28
> **moster said:**
> hehe, you probably have splitted file, probably with hjsplit or something else. Ok, you now need to combine it somehow, I never do that myself on linux but it can be done. Try with this

[http://manpages.ubuntu.com/manpages/jaunty/man1/combine.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/combine.1.html)

or this, it has nice GUI

[http://www.freebyte.com/hjsplit/#linux](http://www.freebyte.com/hjsplit/#linux)
Thank you

---

