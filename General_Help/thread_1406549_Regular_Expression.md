---
title: "Regular Expression"
date: 2010-02-14
forum: General Help
---

### Post by lucasart on 2010-02-14
Hello everyone,

I am looking for some old-school Linux command line gurus out there, to help me with regular expressions. I would like to delete in a given directory tree, all files that are neither *.mp3 or *.wma.

Is it possible to give the find command a regexp that matches that ? The idea would be do do something like that
```

find . -type f -iname $regexp -exec rm {} \;

```

Thank you

---

### Post by sisco311 on 2010-02-14
```
find ./ -type f ! \( -iname "*.mp3" -o -iname "*.wma" \)
```

oh & instead of -exec rm... use -delete to remove the files.

---

### Post by lucasart on 2010-02-14
Thank you so much. It works like a charm !

But for my own understanding, if the regular expression X="\.wma$" and Y="\.mp3$" will match lines that end with ".mp3" and ".wma", how would I build a regexp Z = not(X or Y) ? That would help me a lot as I often need to do some grep and sed stuff, and never understood how to do that. I believe I could also do "find . -type f -iregex Z -delete", once I figure out what the syntax for regexp Z is, right ?

---

