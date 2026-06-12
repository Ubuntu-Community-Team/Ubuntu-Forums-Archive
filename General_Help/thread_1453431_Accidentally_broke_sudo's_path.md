---
title: "Accidentally broke sudo's path?"
date: 2010-04-13
forum: General Help
---

### Post by gophergun on 2010-04-13
When I try to run almost any command with sudo, it returns sudo: command: command not found. When I run sudo echo $path, it returns a blank line. Is there a command to set its path back to the default?

(UNR 9.10 x86)

---

### Post by philinux on 2010-04-13
This might help.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by gophergun on 2010-04-13
Sorry about the delayed reply. Sudoers still has the line,

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```the permissions on it is 0440 as far as I can tell, and I'm still an admin. I was modifying the root path when this happened I think, I was trying to run a command not found in the usual path as root, but to be honest, I'm not really sure how to put it back. It's not spitting up any real errors besides not finding most commands.`

EDIT: After trying to reverse what I did, it now lists the path correctly, and seems to be finding commands (at least according to tab completion), but when I run, say, sudo cd /, it pulls up sudo: cd: command not found. Am I missing something obvious?

Second edit, noob mistake: upon searching, I now learn that it's because cd isn't an executable, it's builtin.  My mistake! Thank you all for everything you do.

---

