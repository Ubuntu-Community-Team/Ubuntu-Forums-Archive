---
title: "How to? get the size of a file referenced via a symbolic link"
date: 2011-05-07
forum: General Help
---

### Post by dazz100 on 2011-05-07
Hello

I am writing a Bash script.
I need to compare the size of a file that is accessed via a symbolic link.

The name of the symbolic link remains fixed, but the file it is linked to is constantly changed by another application (Motion).  The Motion application ensures that the symbolic link points to the correct file.  

When using the 
stat -c %s = <filenamelink>
command, it returns the size of the symbolic link, not the size of the file I want.

How do I find the size of a file that a symbolic link is pointed at?

---

### Post by lloyd_b on 2011-05-07
> **dazz100 said:**
> Hello

I am writing a Bash script.
I need to compare the size of a file that is accessed via a symbolic link.

The name of the symbolic link remains fixed, but the file it is linked to is constantly changed by another application (Motion).  The Motion application ensures that the symbolic link points to the correct file.  

When using the 
stat -c %s = <filenamelink>
command, it returns the size of the symbolic link, not the size of the file I want.

How do I find the size of a file that a symbolic link is pointed at?

Use the "-L" option of 'stat' - this tells 'stat' to "dereference" the symbolic link (reporting the information on the file pointed to by the link, rather than the information on the link itself).```
stat -Lc %s <symlink>
```

Lloyd B.

---

### Post by dazz100 on 2011-05-07
Thanks.  That works.

---

