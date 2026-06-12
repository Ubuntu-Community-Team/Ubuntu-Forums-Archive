---
title: "Search multiple word/phrases in a file"
date: 2009-07-06
forum: General Help
---

### Post by Lifyre on 2009-07-06
Is there a way to search for multiple words or multiple phrases in the contents of a file using a single command?

I have a list of words I need to find in file contents on multiple computers and want to avoid having to do multiple searches on each computer due to performance and time issues.

---

### Post by earthpigg on 2009-07-06
i think....

grep -nir test1 /*


replace test1 with the text you are looking for

---

### Post by Lifyre on 2009-07-06
That will get me one word/phrase I need to do multiple words/phrases unless I'm missing something.

---

### Post by earthpigg on 2009-07-06
make a text file that contains the words or phrases you are looking for. in my example, its called 'info'.

```
grep -nirf info /*
```

im learning this as we go, btw, i dont have any of this memmorized or anything.... typing

```
man grep
```

will show you the manual for grep, which is how im putting that command together :P

other useful commands in this genre of stuff would be:

```
cat
ls
```

---

### Post by Lifyre on 2009-07-06
Sweet.  You sir are a gentleman and a scholar!

---

### Post by loomsen on 2009-07-06
egrep -i "foo|bar|foo_bar|whatever" <from>

---

### Post by Lifyre on 2009-07-06
Awesome, I never thought to pipe it.

---

