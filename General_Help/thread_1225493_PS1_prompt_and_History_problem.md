---
title: "PS1 prompt and History problem"
date: 2009-07-28
forum: General Help
---

### Post by dld on 2009-07-28
If I have recently used a command line of 24 or more characters, and back over that command with the up arrow, and then back down, my prompt has an extra 8 characters, the first 8 characters of the long command line.  For example:
 509  zzzzzzzzzzzzzzzzzzzzzzzzzz
 510  aaa
 511  history
DLD3:~$

Now I do 3 up arrows, and 2 down arrow:

DLD3:~$ zzzzzzzzaaa
bash: aaa: command not found
DLD3:~$ 

Note that the z's are not taken as part of the command.  They are part of the prompt?

Its a real nuisance!!  Any help would be appreciated, and thanks in advance.

---

