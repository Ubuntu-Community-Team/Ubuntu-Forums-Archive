---
title: "word count"
date: 2010-01-28
forum: General Help
---

### Post by siuchi on 2010-01-28
Hi,

Is there a way or application that can count how many word I have been type?

Thanks.

---

### Post by audiomick on 2010-01-28
In Open Office, in the menu "extras" when you have a text document open there is a word counter.

---

### Post by falconindy on 2010-01-28
If this isn't a formatted file (like openoffice) you can use the command line program 'wc':

```
$ wc -l squashfu                                                                                       
481 squashfu

```

---

### Post by llamabr on 2010-01-28
Yes, depending on what sort of file it is, use wc.  It also returns characters, and lines:

```
brock@hops:~$ cat game.txt | wc
   1060    8751   57539
brock@hops:~$ 
```

---

### Post by x33a on 2010-01-28
for word docs,

you can try
```
strings <filename> | wc
```
or
```
antiword <filename> | wc
```

---

### Post by siuchi on 2010-01-28
Sorry for not making it clear enough,

I mean the word count for the whole system. not only a application or a file

Is it possible to do so?

---

### Post by x33a on 2010-01-28
what exactly do you mean by whole system?

all the text, doc. etc files on the system?

if that's the case, why do you want to do this (just curious).

---

### Post by siuchi on 2010-01-29
> **x33a said:**
> what exactly do you mean by whole system?

all the text, doc. etc files on the system?

if that's the case, why do you want to do this (just curious).

Yes, everything(include text, doc , command), I just want to count how many word i have typed per day

---

### Post by rnerwein on 2010-01-29
hi
that's a joke - isn't it ???

---

### Post by x33a on 2010-01-29
> **siuchi said:**
> Yes, everything(include text, doc , command), I just want to count how many word i have typed per day
i think a better option would be to use a keylogger of sorts. i don't know if one exists for linux. maybe a shell script to record the number of keystrokes you enter.

---

### Post by siuchi on 2010-02-01
> **x33a said:**
> i think a better option would be to use a keylogger of sorts. i don't know if one exists for linux. maybe a shell script to record the number of keystrokes you enter.


That's the one i want, but i couldn't find any keylogger application or shell script

---

### Post by x33a on 2010-02-01
did a google search, and found a few:

[http://sourceforge.net/apps/mediawiki/pykeylogger/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/pykeylogger/index.php?title=Main_Page)

[http://www.securiteam.com/tools/6B00L0U95Q.html](http://www.securiteam.com/tools/6B00L0U95Q.html)

[http://code.google.com/p/logkeys/](http://code.google.com/p/logkeys/)

Try them out, and see which one suits your needs.

---

