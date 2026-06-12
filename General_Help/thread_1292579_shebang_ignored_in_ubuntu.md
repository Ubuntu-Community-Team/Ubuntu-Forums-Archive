---
title: "shebang ignored in ubuntu"
date: 2009-10-16
forum: General Help
---

### Post by irdave on 2009-10-16
I have had this problem for a while.  I just reinstalled the latest Ubuntu tonight in an effort to correct it.  When I type #! /usr/bin/perl (with and without the space after the !) in the editor,  I cannot get the shell to recognise the shebang.  I have to type perl filename.pl everytime.

The error is:

bash: filename.pl: command not found

I have searched this and other forums to no avail.  Why is the shebang ignored?  Thanks for any help.

---

### Post by dominiquec on 2009-10-16
Did you change the file permissions for the file.  The execute bit should be on. 

chmod +x filename.pl

---

### Post by irdave on 2009-10-16
Yes.  The file is executable.

---

### Post by mocoloco on 2009-10-16
Remember that in Linux/Unix the current director is not in the path, so you need to give it a relative path with "./" preceeding.  Example ```
./filename.pl
```

---

### Post by irdave on 2009-10-16
mocoloco, Thank you.  I don't know why I overlooked that.  Much frustration relieved

---

### Post by mocoloco on 2009-10-16
We all gotta learn sometime.  Things you learn the hard way after much frustration you will never forget again :P

---

