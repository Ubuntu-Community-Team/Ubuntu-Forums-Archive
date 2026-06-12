---
title: "search  archive files"
date: 2012-05-08
forum: General Help
---

### Post by winzip on 2012-05-08
_My Objective_

I have a lib folder.   /home/user/lib

It contains JAR archives.

example:    abc.jar ,  dgfh.jar , benr.jar etc


I  want to decompile all these JAR files into  source java files  and want to search for a text "Environment" in these  files.


Whats  the solution ?


_Input/output:_

input:  /home/user/lib       

output:  "Environment"  text match found in  pqrs.java  in  benr.jar


System:  Ubuntu Server OS 10.04 (no GUI)

---

### Post by steeldriver on 2012-05-08
wasn't this already answered in your previous thread?

[http://ubuntuforums.org/showthread.php?t=1975377](http://ubuntuforums.org/showthread.php?t=1975377)

if you want too search subdirectories as well, you could use the find command instead - with -exec {} argument to do the unzip / grep part

---

### Post by winzip on 2012-05-08
> **steeldriver said:**
> wasn't this already answered in your previous thread?

[http://ubuntuforums.org/showthread.php?t=1975377](http://ubuntuforums.org/showthread.php?t=1975377)



No . You misunderstood.

This is a different question. Here first  de-compilation and   then text  search  involved.

This is a completely different  question.

---

