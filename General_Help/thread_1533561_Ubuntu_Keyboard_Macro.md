---
title: "Ubuntu Keyboard Macro?"
date: 2010-07-18
forum: General Help
---

### Post by Jake007g on 2010-07-18
Is there any application which can fulfil keybaord macros which I set?

I need something which can press DOWN, DOWN, DOWN, DOWN, SHIFT+UP, SHIFT+UP, SHIFT+UP, BACKSPACE. And then repeat that cycle for a long period of time.

I'm using Ubuntu (GNOME) 10.04.

Many thanks to those who can help.

---

### Post by Zorgoth on 2010-07-18
You could use xvkbd -xsendevent -text I believe, although that in my expereience is a little buggy.  There is something called autokey, but I don't know if that simulates any keypress or just text entry.

If you are trying to delete all but every fourth line of a file, you could also do a regexp search and replace using sed, or if that is scary, emacs.

---

### Post by Zorgoth on 2010-07-18
To delete three out of every four lines in a plain text file you could run this command:

```

sed '1~4p;d' /path/to/file > /path/to/modified/file

```
To start from the nth line, change "1~4p" to "n~4p".

If you are not dealing with a plain text format, you could copy it to a plain text file or pipe it in somehow to standard input; either is fine.

---

