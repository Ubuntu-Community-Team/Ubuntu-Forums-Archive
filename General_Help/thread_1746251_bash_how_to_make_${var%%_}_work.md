---
title: "bash: how to make ${var%% *} work?"
date: 2011-05-01
forum: General Help
---

### Post by quadproc on 2011-05-01
A question regarding bash: how do you make the construct ${var%% *} work?

I am trying to select the first word from a variable which contains many space-separated words.  I am running Ubuntu 10.10 with GNU bash, version 4.1.5(1)-release (x86_64-pc-linux-gnu) and when I try to use this construct, the expression returns the complete variable with no removal of trailing anything.

Is this a bug?  Do I have something missing?  Thanks for any help.

quadproc

---

### Post by DaithiF on 2011-05-01
works for me
```
$ x="my name is"
$ echo ${x%% *}
my

```

---

### Post by quadproc on 2011-05-01
Would you please let me know which bash version you are using?  You can get this by doing a
bash --version
on the command line.  Thanks.

quadproc

---

### Post by DaithiF on 2011-05-01
this has been in bash for as long as i can remember, certainly since bash 3.

i'm using 4.2.8 and 4.1.10

---

