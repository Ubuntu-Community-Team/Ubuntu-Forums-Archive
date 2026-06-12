---
title: "Sym Link / Terminal Argument help"
date: 2009-12-08
forum: General Help
---

### Post by mwmsje on 2009-12-08
Suppose I have Eclipse 3.5 in ~/Desktop/temp/eclipse3.5 and I want to create a link to this file.

I assume I need to create a symbolic link of the path and then 'drop' this link in some bin directory somewhere? 

Forgive me for my ignorance but I'm failing to understand the concept still. Could some please tell me if my idea is correct and possible a brief explanation of what a symbolic link actually 'does'.

Cheers.

P.S. I use Ubuntu 9.04 Jaunty.

EDIT: I wrongly put this in the 'general' forum, should this be moved to the 'Absolute Beginner Talk', as I would confidentally describe myself as this.

---

### Post by lloyd_b on 2009-12-08
A "symlink" is a pointer to a file located elsewhere.  For example:```
lloyd@dell:/usr/bin$ ll firefox
lrwxrwxrwx 1 root root 11 2009-11-12 04:54 firefox -> firefox-3.5
lloyd@dell:/usr/bin$ ll firefox-3.5
lrwxrwxrwx 1 root root 31 2009-11-12 04:54 firefox-3.5 -> ../lib/firefox-3.5.5/firefox.sh 

``` 'firefox' is the common name for the program.  "firefox-3.5" is the "proper" name (including the version number).  But the actual program is located at "/usr/lib/firefox-3.5.5/firefox.sh".

The syntax for creating a symlink is "ln -s {real file} {link name}"

As to where to create it - if it's strictly for the use of a single account, put the link in that account's "~/bin" directory (creating it if necessary).

If it's for the use of multiple accounts, then I'd recommend putting the link in "/usr/local/bin".  Note that you'll need a "sudo" to create the link there.

Lloyd B.

---

