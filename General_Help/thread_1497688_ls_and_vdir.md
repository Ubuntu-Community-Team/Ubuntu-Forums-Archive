---
title: "ls and vdir"
date: 2010-05-30
forum: General Help
---

### Post by COKEDUDE on 2010-05-30
I'm curious if the man pages on ls and vdir are complete. They both look the same. I used the diff command to compare the man pages and they were the same. I know they should be different since the actions are different. 
Also the "ls -ld" command is not working the way I expect it to work. I would expect it to list all the information of the subdirectories, but it only gives the current directory information. So I added the recursive option and that isn't changing my output at all. Can anyone explain its not showing all subdirectories? 
```
ls -ld
drwx------ 49 bob bob 12288 2010-05-30 21:54 
ls -ldR
drwx------ 49 bob bob 12288 2010-05-30 21:54 
```

---

### Post by sdennie on 2010-05-30
I'd never heard of a vdir before but, a "diff -a" between the two binaries shows that they are basically the same binary.

It sounds like the command you want to run is either:

```

ls -ld *

```

Or, for a recursive listing:

```

ls -ld `find . -type d`

```

---

### Post by COKEDUDE on 2010-06-03
I discovered from reading around that vdir is on some distros of Linux and only if you add it to Unix.

---

