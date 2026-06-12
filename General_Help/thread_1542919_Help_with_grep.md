---
title: "Help with grep"
date: 2010-07-31
forum: General Help
---

### Post by ambre on 2010-07-31
Hi,

I want to analayse the mail log on my system.  I am only interested in those entries (lines) that begin with the current date in 'Mmm dd' format and contain the character strings 'from:' or 'to:'.

I know grep can filter out these lines for me, but I cannot come up with the correct instruction.

Any offers will be much appreciated.

Thanks.

---

### Post by DaithiF on 2010-07-31
Hi, something like:
grep "^$(date +'%b %d').*To\|From" testfile

---

### Post by jleslie48 on 2010-07-31
> **ambre said:**
> Hi,

I want to analayse the mail log on my system.  I am only interested in those entries (lines) that begin with the current date in 'Mmm dd' format and contain the character strings 'from:' or 'to:'.

I know grep can filter out these lines for me, but I cannot come up with the correct instruction.

Any offers will be much appreciated.

Thanks.


untested:  but use egrep or grep -E  (same thing) combined with a pipe. 

grep -Ei "string1|string2|string3" searchfile


eg: grep-Ei "Jul 31" searchfile.log |  grep -Ei "from:|to:" #first grep pulls todays date lines, and pipe that output to the a grep for either from or to

---

### Post by AlphaLexman on 2010-07-31
> *                                                                  Reason: turned my sytax ito the smiley thing!!  how do I tgurn it off???                                      *Wrap (Code) tags around the text:
```
grep-Ei "Jul 31" searchfile.log |  grep -Ei "from:neutral:to:"
```

---

