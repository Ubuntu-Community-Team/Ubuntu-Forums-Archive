---
title: "Converting line endings from the command line"
date: 2010-03-22
forum: General Help
---

### Post by Alex Farber on 2010-03-22
I am looking for a way to convert text file line endings from the command line, something like this:

convert --windows-to-unix text-file

or:

convert --windows-to-unix input-file output-file

---

### Post by DaithiF on 2010-03-22
Hi, install tofrodos, then use unix2dos and dos2unix

---

### Post by n0dix on 2010-03-22
Or use [Flip]("http://www.debianadmin.com/flip-convert-text-file-line-endings-between-unix-and-dos-formats.html").

---

### Post by kaibob on 2010-03-22
The above solutions are easiest and best. Just for the sake of completeness, you can use sed and awk. For example, 

Convert DOS/Windows newlines (CRLF) to Unix newlines (LF).

```
sed -i 's/.$//' file
```

Convert Unix newlines (LF) to DOS/Windows newlines (CRLF).

```
sed -i "s/$/`echo -e \\\r`/" file
```

REFERENCES:

[http://www.catonmat.net/blog/sed-one-liners-explained-part-one/](http://www.catonmat.net/blog/sed-one-liners-explained-part-one/)

[http://www.catonmat.net/blog/awk-one-liners-explained-part-two/](http://www.catonmat.net/blog/awk-one-liners-explained-part-two/)

---

### Post by Alex Farber on 2010-03-22
Thank you, the problem is solved.

---

### Post by angrygreenfrogs on 2011-09-19
Be very careful using that sed one-liner above.

It doesn't just remove line endings, it remove the last character of ANY file

So, yeah, I accidentally ran it on a bunch of source code that had unix line endings and will be spending the next 2 hours retyping the last character of each line. 

Wish I had made a backup first, but that's a different story.

---

