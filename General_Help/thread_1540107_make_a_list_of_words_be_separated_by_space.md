---
title: "make a list of words be separated by space"
date: 2010-07-27
forum: General Help
---

### Post by aaaaaaq2 on 2010-07-27
examples are the best:

I want to make this:

cat
cow
dog

become this:
cat cow dog

how? thanks

---

### Post by lukeiamyourfather on 2010-07-27
> **aaaaaaq2 said:**
> examples are the best:

I want to make this:

cat
cow
dog

become this:
cat cow dog

how? thanks

Use Gedit to find and replace returns with spaces. If the default interface won't accept returns then use regular expressions to find the returns. Alternatively there's Python, Perl, sed, etc.

---

### Post by prodigy_ on 2010-07-27
[Edit]: found an easier way:
[http://stackoverflow.com/questions/1251999/sed-how-can-i-replace-a-newline-n](http://stackoverflow.com/questions/1251999/sed-how-can-i-replace-a-newline-n)

---

### Post by ThesaurusRex on 2010-07-27
Is this for a coding project? If not, follow the first reply. If so, what language?

---

### Post by rubylaser on 2010-07-27
_prodigy answer would work fine.  You would open a terminal and then type the command he gave you followed by the filename that had your list in it. You'd make a file in this example test.txt and then pipe it to a new file.

```
&#10140;  ~  cat test.txt 
cat
cow
dog
```

```
tr '\n' ' ' < test.txt > text_newlines_removed.txt
```

```
&#10140;  ~  cat text_newlines_removed.txt
cat cow dog 
```

---

### Post by hakermania on 2010-07-27
if you are not familiar with the terminal open this file with Gedit click the FInd and replace button and type to the find box '\n' without the ' and into the replace add a space ( " " without the " )

---

### Post by Deiz on 2010-07-27
> **rubylaser said:**
> _prodigy answer would work fine.  You would open a terminal and then type the command he gave you followed by the filename that had your list in it. You'd make a file in this example test.txt and then pipe it to a new file.

```
&#10140;  ~  cat test.txt 
cat
cow
dog
```

```
tr '\n' ' ' < test.txt > text_newlines_removed.txt
```

```
&#10140;  ~  cat text_newlines_removed.txt
cat cow dog 
```

For simpler, interactive use I'd just recommend running:
```
tr '\n' ' '
```
and then pasting in the input, followed by ^D (Ctrl-D) to terminate and get space-delimited output.

---

