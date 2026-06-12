---
title: "Downloaded files do not show ... ???"
date: 2011-01-24
forum: General Help
---

### Post by lubigbright on 2011-01-24
Hi, Ubuntu Gurus !

I got a tricky problem. Some of my downloaded files do not show in the window but can be shown in Terminal by 'ls'. Can somebody explain this? 

Please refer to the image below. There are 11 files and 1 folder shown in the Terminal while only 4 files can be displayed in the window. 

Thanks!!! ;)

[URL="http://www-scf.usc.edu/%7Edaminglu/cs571/Screenshot.png"]
[/URL]

---

### Post by Wtower on 2011-01-24
Hi, could you post the output of 

```
ls -al
```

in code tags please.

---

### Post by AlphaLexman on 2011-01-24
There seems to be some weird characters in the ****part01.rar file, maybe that is messing something else up?

Try ctrl-h in nautilus and ls -la in a terminal, post results.

---

### Post by lubigbright on 2011-01-24
Hey, Wtower, AlphaLexman and everybody else !
Ctrl + h doesn't show any difference. "ls -al" shows as follows:

daming@dl408c-1:~/Learning/Math_Stat$ ls -al
total 33812
drwxr-xr-x 3 daming daming     4096 2011-01-24 03:05 .
drwxr-xr-x 7 daming daming     4096 2011-01-24 02:44 ..
-rw-r--r-- 1 daming daming 11749667 2003-08-29 08:00 1-6.pdf (invalid encoding)
-rw-r--r-- 1 daming daming   456957 2011-01-24 02:56 An Introduction to Probability Theory.pdf
-rw-r--r-- 1 daming daming  1876680 2011-01-24 02:53 attachment.rar
drwxr-xr-x 2 daming daming     4096 2007-03-27 18:38 Casella
-rw-r--r-- 1 daming daming  2050674 2008-06-08 01:29 David A Santos - Elementary Probability.pdf
-rw-r--r-- 1 daming daming  1876680 2011-01-24 02:55 David A Santos - Elementary Probability.rar
-rw-r--r-- 1 daming daming  1457664 2011-01-24 03:05 Í³¼ÆÑ§Ô*Àí.part01.rar
-rw-r--r-- 1 daming daming  2194848 2008-07-04 23:02 Rachel Fewster - Statistical Theory.pdf
-rw-r--r-- 1 daming daming   336715 2011-01-24 02:56 Richard F Bass - Probability Theory.pdf
-rw-r--r-- 1 daming daming   212033 2011-01-24 02:56 Richard F Bass - Undergraduate probability.pdf
-rw-r--r-- 1 daming daming   294444 2011-01-24 02:56 William G Faris - Lectures on Elementary Probability.pdf
-rw-r--r-- 1 daming daming   531631 2011-01-24 01:55 William G Faris - Theory of Statistics.pdf
-rw-r--r-- 1 daming daming 11550737 2006-06-01 04:58 ZhongKaiLai.pdf (invalid encoding)
daming@dl408c-1:~/Learning/Math_Stat$

---

### Post by Wtower on 2011-01-25
Yes, as AlphaLexMan suggests maybe that filename messes things up - also, that invalid encoding note indicates what it says for that particular filename; again this may mess things up. If I were you I would try renaming the peculiar filenames to something more appropriate from the console using the mv command:

```
mv oldfilename newfilename
```

---

