---
title: "Problems with $PATH"
date: 2009-09-25
forum: General Help
---

### Post by v_kambiz on 2009-09-25
I use qt creator a lot, it comes with a script (starting with #!/bin/sh) that starts the actual application after some initializations. Now if I run the script from a terminal, everything works, but if I run it by a double click and choosing run or run in terminal I ran into problems. I found out the the this is because the PATH variable seen by the script differs. My customizations in .bashrc are ignored in the second case. Why? How can I change this behavior?

---

### Post by Liolikas on 2009-09-25
Looks like you encountered bug you have to report it for smashing.

---

### Post by bodhi.zazen on 2009-09-25
> **v_kambiz said:**
> I use qt creator a lot, it comes with a script (starting with #!/bin/sh) that starts the actual application after some initializations. Now if I run the script from a terminal, everything works, but if I run it by a double click and choosing run or run in terminal I ran into problems. I found out the the this is because the PATH variable seen by the script differs. My customizations in .bashrc are ignored in the second case. Why? How can I change this behavior?

In you script add a line

```
PATH="your_custom_path_here
```

Or better, IMO, use the full path in your scripts.

/bin/foo rather then foo

If you use a command more then once

FOO=/bin/boo

$FOO first 
$FOO second

etc

---

### Post by v_kambiz on 2009-09-25
Thank You both for the replies.
I'm trying to setup the Intel compiler, it requires me to call 
source /opt/intel/Compiler/11.1/056/bin/iccvars.sh intel64
in addition to the modifications I have done to PATH variable.

the command was in .bashrc and the compiler was found in the PATH (from terminal), now I have solves the problem by adding that line to startup script and changing sh to bash.. But I really expect no difference between running an application from terminal or by a double click.

---

