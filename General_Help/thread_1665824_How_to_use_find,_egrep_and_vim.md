---
title: "How to use find, egrep and vim"
date: 2011-01-12
forum: General Help
---

### Post by denarced on 2011-01-12
Hello,

I've been using this command lately:
```

find . -type f -iregex '.*\.java' -exec egrep --color 'new Runnable' '{}' \+

```
The iregex and egrep pattern of course are not important. The point is that at some point I find what I'm looking for and it could be a few files as match.

How could I then easily start vim with those files ?

A workaround by the way is to just open the file list in vim and then use the command 'gf' (go file). Like this:
```

find . -type f -iregex '.*\.java' -exec egrep --color -h 'new Runnable' '{}' \+ | vim -

```

---

### Post by denarced on 2011-01-13
Not sure if this is legit but here goes, the solution:
[http://www.linuxforums.org/forum/programming-scripting/174005-how-find-files-then-edit-em-find-grep-vim.html#post824207]("http://www.linuxforums.org/forum/programming-scripting/174005-how-find-files-then-edit-em-find-grep-vim.html#post824207")

---

