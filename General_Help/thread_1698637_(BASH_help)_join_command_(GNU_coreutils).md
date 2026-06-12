---
title: "(BASH help) join command (GNU coreutils)"
date: 2011-03-02
forum: General Help
---

### Post by lbthrice on 2011-03-02
Hi,
I am trying to understand the join command.
I wish to join two files:

```

$ cat test1
a 0
b 2.51
c 19.85

$ cat test2
a 0
b 2.51

$ join -a 1 -a 2 -e FOO test1 test2
a 0 0
b 2.51 2.51
c 19.85

```

this is great but I do not understand why join ignores the -e flag and fails to insert FOO in the empty field.

thanks for any help from gnu gurus lurking around here.

-Lee

---

### Post by DaithiF on 2011-03-02
> **lbthrice said:**
> 
this is great but I do not understand why join ignores the -e flag and fails to insert FOO in the empty field.


Hi
its not ignoring -e, but it only applies -e to lines that it is joining.  ie. when it can successfully join a line based on the key field, but where one or other of the files has an empty field.  When a line is not matched the -a param tells join to output that line, but its not going to do any replacing on the other file since there was no line in the first place.

to illustrate, if you amend test1 as follows to introduce a missing field, then you get the -e replace behaviour:
```
$ cat test1
a 
b 2.51
c 19.85

$ join -a 1 -a 2 -e foo test{1,2}
a foo 0
b 2.51 2.51
c 19.85


```

---

