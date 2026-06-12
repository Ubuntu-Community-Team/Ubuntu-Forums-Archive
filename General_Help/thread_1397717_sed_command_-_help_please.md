---
title: "sed command - help please"
date: 2010-02-03
forum: General Help
---

### Post by Timothy Taylor on 2010-02-03
I have been trying to use the **sed** command to remove lines of what I suspect were Chinese or Japanese translation in text documents.  These lines appear to consist mostly of non-ASCII characters like "Šš¥ß€FŠ"

I was hoping that delete lines containing non-ASCII characters:

sed -e '/^[:ascii:]/d' < test1.txt

but this doesn't appear to do anything.

I tried this:

sed -e '/^[\x00 - \x7F]/d' < test1.txt

but again, no luck.
I realise that this is probably because it is finding *_some_* ASCII characters in the lines I wish to discard?

Any ideas?

---

### Post by Brandon Williams on 2010-02-03
Are you trying to delete all lines that have one or more non-ascii characters in them? In that case, I think you want the '^' symbol inside the '[...]' expression, as in:
```
sed -e '/[^:ascii:]/d'
```
Outside of the character class, the '^' matches on start-of-line. If it's the first character inside, it inverts the specified character class.

---

### Post by Lars Noodén on 2010-02-04
Maybe awk or egrep would be  more appropriate.

Do you want to keep the line, but leave it empty, or eliminate the offending line completely?

---

### Post by bokopperud on 2010-02-04
Try 'tr'... perhaps with the -d option.
Note: It must be *in* the pipeline, it doesn't take file-arguments itself (use 'cat' first).

---

### Post by Timothy Taylor on 2010-02-04
Thanks for the replies.

> **Brandon Williams said:**
> Are you trying to delete all lines that have one or more non-ascii characters in them? Yes.

> **Brandon Williams said:**
> In that case, I think you want the '^' symbol inside the '[...]' expression, as in:
```
sed -e '/[^:ascii:]/d'
```
Outside of the character class, the '^' matches on start-of-line. If it's the first character inside, it inverts the specified character class. I tried

sed -e '/[^:ascii:]/d' < test1.txt

and there is no output - it seems to delete *every* line...

:confused:

[QUOTE=Lars Noodén]Do you want to keep the line, but leave it empty, or eliminate the offending line completely? [/QUOTE] I want to remove it completely.

ETA
I have also tried:

sed -e '/[\x80 - \xFF]/d' < test1.txt

hoping that this would catch "extended" ASCII characters, but this seems to delete all the lines I actually want!

This seems to be a typical "*simple 5-minute job*"!  :)

I'll have a look at awk, egrep and tr.

---

### Post by mobilediesel on 2010-02-04
> **Timothy Taylor said:**
> Thanks for the replies.

 Yes.

 I tried

sed -e '/[^:ascii:]/d' < test1.txt

and there is no output - it seems to delete *every* line...
:confused:

 I want to remove it completely.

You almost have it, try:
```
sed -e '/[^[:print:]]/d' test1.txt
```
[:print:] is for printable characters and there's no need for the **<** character.

---

### Post by Timothy Taylor on 2010-02-04
> **mobilediesel said:**
> You almost have it, try:
```
sed -e '/[^[:print:]]/d' test1.txt
```
[:print:] is for printable characters and there's no need for the **<** character.

No, that doesn't work either - no output.

---

### Post by mobilediesel on 2010-02-04
> **Timothy Taylor said:**
> No, that doesn't work either - no output.

That suggests that the file is all one line or every line contains non-printable characters.

---

### Post by Timothy Taylor on 2010-02-04
Aye, something weird is going on...

I tried

sed -e '/[:ascii:]/d' test1.txt

and was surprised to get a list of *paragraph numbers* and some lines of the garbage text out.

---

