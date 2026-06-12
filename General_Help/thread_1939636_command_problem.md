---
title: "command problem"
date: 2012-03-12
forum: General Help
---

### Post by achuth on 2012-03-12
Sir,
I don't see any difference between ls and ls -A.

The output of both the commands are same.

If there is any difference what is that?

I didn't understand the man page of ls -A

What is ls -A ?

---

### Post by Sazhen86 on 2012-03-12
Hi

The "ls" command by default ignores files where the name starts with a period (.) and they don't appear in the listing.  The "-a" option lists all files, including those with filenames starting with a period.  This includes the filenames for the current directory (.) and the parent directory (..).  The "-A" option lists almost all the files by omitting the (.) and (..) entries.

Hope that helps.

---

### Post by achuth on 2012-03-12
Why the parent directory file is kept in the current directory?

---

### Post by Dave_L on 2012-03-12
".." is a link to the parent directory. The command "cd .." navigates from the current directory to its parent.

---

### Post by achuth on 2012-03-12
No,
It is now shown as a link.
It is still shown as a directory by the ls command.
WHY?

---

### Post by WorMzy on 2012-03-12
What?

. and .. *are* directories. What do you mean ".." is shown as a link?

---

### Post by raja.genupula on 2012-03-12
[http://manpages.ubuntu.com/manpages/hardy/man1/ls.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/ls.1.html)

---

### Post by achuth on 2012-03-13
Why the current directory contains a parent directory?

---

### Post by WorMzy on 2012-03-13
Because if it didn't, how would you navigate? You'd only be able to go one way through the filing system.

---

