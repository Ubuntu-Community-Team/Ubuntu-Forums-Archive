---
title: "Renaming multiple files"
date: 2012-06-13
forum: General Help
---

### Post by sumithar on 2012-06-13
This is really not an Ubuntu specific question, it's just a Linux question.

I have a series of files in a folder named in the following pattern
xxxx1.mp3
xxxx2.mp3
xxxx3.mp3
.
.
.
xxxxn.mp3

How can I rename them all so the number at the end is at the beginning so it looks like this

1xxxx.mp3
2xxxx.mp3
3xxxx.mp3
.
.
.
nxxxx.mp3

I guess this has to be done on the command prompt, right?

---

### Post by d2btoo on 2012-06-13
Did you try **GPRename***

*avail on repo

Here are some suggestions: [http://askubuntu.com/questions/10607/what-mass-file-renaming-tools-are-available](http://askubuntu.com/questions/10607/what-mass-file-renaming-tools-are-available)

---

### Post by sumithar on 2012-06-13
> **d2btoo said:**
> Did you try **GPRename***

*avail on repo

Here are some suggestions: [http://askubuntu.com/questions/10607/what-mass-file-renaming-tools-are-available](http://askubuntu.com/questions/10607/what-mass-file-renaming-tools-are-available)
Excellent, I'm sure I'll find the answer there.  Thank you so much, especially for not getting on my case 'cos I didn't search before I posted!

---

### Post by steeldriver on 2012-06-13
If you *did* want to use the command line then there is 'rename' e.g.

```
$ rename -v 's/([^0-9]+)([0-9]+)(\.mp3)/$2$1$3/' *.mp3
xxxx1.mp3 renamed as 1xxxx.mp3
xxxx289.mp3 renamed as 289xxxx.mp3
xxxx2.mp3 renamed as 2xxxx.mp3
xxxx34.mp3 renamed as 34xxxx.mp3
xxxx3.mp3 renamed as 3xxxx.mp3

```(rename any non-zero sequence of NON digits followed by any non-zero sequence of digits followed by literal .mp3, interchanging the order of the digits and the non digits)

If you want to move just a single digit, and the 'xxxx' may contain digits, then

```
$ rename -nv 's/(.*)([0-9])(.mp3)/$2$1$3/' *.mp3
xxxx1.mp3 renamed as 1xxxx.mp3
xxxx289.mp3 renamed as 9xxxx28.mp3
xxxx2.mp3 renamed as 2xxxx.mp3
xxxx34.mp3 renamed as 4xxxx3.mp3
xxxx3.mp3 renamed as 3xxxx.mp3

```Run it with '-n' to see what it *would* do without actually doing it

```
rename -**n**v 's/.../...' *files*
```

---

