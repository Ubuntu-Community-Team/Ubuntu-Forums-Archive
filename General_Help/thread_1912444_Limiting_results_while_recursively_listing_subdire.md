---
title: "Limiting results while recursively listing subdirectories"
date: 2012-01-20
forum: General Help
---

### Post by kd7swh on 2012-01-20
I would like to exclude sub-directories whose file names are just numbers from a recursive list.

```
ls -R
```

Is too verbose listing all sub-directories and 

```
ls -R | egrep "regex"
```

is too slow for suppressing all these numbered sub-directories. 

Ideally I need the exclusion to occur in the "ls" step, so I can freely grep the output which omits the numbered sub-directories.

Any ideas?

---

### Post by erind on 2012-01-21
You can use *extglob *feature of bash:** shopt -s extglob** then **ls -R !(+([0-9]))**, but still this would be useful only for one level of subdirectories (maxdepth=1) - *ls* pattern-matching is valid only for the content of the current directory. 
When dealing with recursive searches, **find** is more appropriate, but it doesn't understand extended globbing and its search patterns need to be *quoted*, so I'm afraid you still need to use another external tool, such as egrep in this case.

---

### Post by sisco311 on 2012-01-21
> **erind said:**
> You can use *extglob *feature of bash:** shopt -s extglob** then **ls -R !(+([0-9]))**, but still this would be useful only for one level of subdirectories (maxdepth=1) - *ls* pattern-matching is valid only for the content of the current directory. 
When dealing with recursive searches, **find** is more appropriate, but it doesn't understand extended globbing and its search patterns need to be *quoted*, so I'm afraid you still need to use another external tool, such as egrep in this case.

+1 for find
GNU/find has a -regex and a -regextype option. So, in GNU/find you can use emacs, posix-awk, posix-basic, posix-egrep and posix-extended regular expressions.

@OP: Don't get me wrong, but this sounds like an [XY problem]("http://mywiki.wooledge.org/XyProblem"). :evil:

What exactly are you trying to accomplish? X=? :)

NOTE: ls shows you a representation of files. They are NOT file names (for simple names, they mostly happen to be equivalent). Do NOT try to parse it. [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

