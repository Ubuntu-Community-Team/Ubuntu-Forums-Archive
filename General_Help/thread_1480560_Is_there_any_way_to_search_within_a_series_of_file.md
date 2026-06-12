---
title: "Is there any way to search within a series of files?"
date: 2010-05-11
forum: General Help
---

### Post by ertayone on 2010-05-11
I recently used scalpel to recover .doc files. I only need to find just one file, but scalpel retrieved thousands and thousands of them, all titled after a sequence of numbers. If I could only search within them all for a single word I'd be able to identify the ones to check out vs. the duds immediately. Is such a thing possible? Can you think of any alternative solutions?

---

### Post by nothingspecial on 2010-05-11
There is a way, infact a few ways.

What are you searching for and where, although that is not imortant (but will simplify the process), do they exist on your file system?

---

### Post by ertayone on 2010-05-11
I wrote an essay on Charles Fourier, but some sort of bug came about when I tried to save or email the file--I don't remember what exactly happened, except that I couldn't use my keyboard and had to manually shut down. When I started back up the original file was at 0 bytes, and so was that little backup recovery file openoffice automatically makes. So I searched around for a recovery tool online and found scalpel. I retrieved every file with a .doc header or footer on my computer and now they're all in these folders:

home/myusername/output/doc-0-0
home/myusername/output/doc-0-1
home/myusername/output/doc-0-2
home/myusername/output/doc-0-3
home/myusername/output/doc-0-4
home/myusername/output/doc-0-5
home/myusername/output/doc-0-6
home/myusername/output/doc-0-7
home/myusername/output/doc-1-0
home/myusername/output/doc-1-1
home/myusername/output/doc-1-2
home/myusername/output/doc-1-3
home/myusername/output/doc-1-4
home/myusername/output/doc-1-5
home/myusername/output/doc-1-6
home/myusername/output/doc-1-7

Each folder contains between 7 and 1,001 word documents that are named in sequences of numbers, e.g. doc-0-0 contains 00000000.doc, 00000001.doc, 00000003.doc, etc.

Most of these files are corrupt, the rest are not what I'm looking for.

Ideally I'd like some way to search for the word "fourier" (for example) within all of the word documents inside each of these folders, in order to identify which ones could possibly be my essay.

Thanks

---

### Post by jobix on 2010-05-11
A simple way would be to use grep:

> grep -l fourier */*

You would execute this when you are in the /home/myusername/output directory. This assumes that there is only one level of directories in your output directory. If there are more, you can add more *, i.e., */*/* in the above command, or better else use the "find" command. The -l after the grep is an lowercase "L" and not the digit 1.

---

### Post by nothingspecial on 2010-05-11
cd into the directory of the output files.

Then type

```
grep -r "Fourier" .
```

be aware that linux is case sensitive - ie [COLOR="Red"]f[/COLOR]ourier & [COLOR="Red"]F[/COLOR]ourier are different.

---

### Post by nothingspecial on 2010-05-11
More details could complicate the command, but simplify the results :)

---

### Post by -humanaut- on 2010-05-11
Another simple terminal trick to locate files is to launch a terminal and type: locate filename

---

