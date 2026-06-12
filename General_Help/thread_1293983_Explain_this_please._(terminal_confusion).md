---
title: "Explain this please. (terminal confusion)"
date: 2009-10-17
forum: General Help
---

### Post by Bu7753x on 2009-10-17
```
buttsex@comp2:~/trip$ mkdir trip
mkdir: cannot create directory `trip': No such file or directory

```I don't get it.  I can't create it because it doesn't exist?

---

### Post by diesch on 2009-10-17
I guess you deleted ~/trip after you get there. What does
```
ls ~/trip
``` say?

---

### Post by Bu7753x on 2009-10-17
> **diesch said:**
> I guess you deleted ~/trip after you get there. What does
```
ls ~/trip
``` say?
```
buttsex@comp2:~$ ls ~/trip
testing

```

---

### Post by diesch on 2009-10-17
Maybe it has been removed and then created again. Does
```
cd ../trip
``` help?



```
/tmp/foo$ mkdir test
/tmp/foo$ cd test
/tmp/foo/test$ rmdir $PWD
/tmp/foo/test$ ls ../test
ls: cannot access ../test: No such file or directory
/tmp/foo/test$ mkdir bla
mkdir: cannot create directory `bla': No such file or directory
/tmp/foo/test$ mkdir ../test
/tmp/foo/test$ ls ../test
/tmp/foo/test$ mkdir bla
mkdir: cannot create directory `bla': No such file or directory
/tmp/foo/test$ cd ../test
/tmp/foo/test$ mkdir bla
/tmp/foo/test$ ls ../test
bla
```

---

### Post by Bu7753x on 2009-10-17
> **diesch said:**
> Maybe it has been removed and then created again. Does
```
cd ../trip
``` help?

Well that seemed to work.  So it got deleted somehow and created again?

I have no clue how that happened.

---

