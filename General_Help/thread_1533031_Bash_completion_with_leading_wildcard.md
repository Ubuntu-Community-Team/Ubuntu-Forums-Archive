---
title: "Bash completion with leading wildcard?"
date: 2010-07-17
forum: General Help
---

### Post by colinmb on 2010-07-17
Out of the box, Bash in 10.04 is configured such that it won't expand/complete parameters when there's a single match for a parameter with a leading wildcard. For example, if I have the following files in a directory:
```
ABC.bin
DEF.bin
GHI.bin
```
...and I type **cp *E***, I expect to be able to press TAB and have Bash expand ***E*** to **DEF.bin**, since that's the only file in the directory with a capital E in its name. (Note: if I actually submit the command with the wildcards in place, the correct file will be used then, but I don't get to see it beforehand.)

I imagine there's something in /etc/bash_completion that's preventing this from working properly. Does anyone know what it is?

--Colin

---

### Post by colinmb on 2010-10-19
Anyone? This still hasn't been fixed in 10.10.

--Colin

---

