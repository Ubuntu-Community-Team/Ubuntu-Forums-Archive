---
title: "Grepping a directory"
date: 2006-03-13
forum: General Help
---

### Post by dotancohen on 2006-03-13
How can I run cat | grep on an entire directory to search for a file that contains a known string? I tried:
user@ety:~$ find . -name "*" -exec cat '{}' | grep searchString \;
find: missing argument to `-exec'
grep: ;: No such file or directory

---

### Post by X-Wes on 2006-03-13
First off, *grep* works great on files. *cat foo | grep pattern* does the same as *grep pattern foo*. That having been said, just use *grep pattern ** where "pattern" is your search word(s).

Edit: Cleaned up BBCode a bit

---

### Post by patrixl on 2006-03-13
grep -r pattern *   <---  the -r means recursive, so all files in current dir + all files in all subdirs

---

### Post by thumper on 2006-03-13
find . | xargs grep grepstring

---

