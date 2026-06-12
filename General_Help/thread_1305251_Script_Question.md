---
title: "Script Question"
date: 2009-10-29
forum: General Help
---

### Post by Snow986 on 2009-10-29
Hi All,

   I am trying to run a simple scrip that goes to a directory, runs a command line program (ROOT for those familiar) and executes a particular command in ROOT while it is running.  I am not sure if this is even possible, so my question is what can I try to get this to work?

Here is my script:

#!/bin/bash
cd /path/to/dir
root 
echo ".x Grades.C"


'root' runs ROOT and '.x Grades.C' is what I want to show up when ROOT loads. So far it gets to running ROOT and then nothing shows up  until after I close ROOT. Again I am not sure it is possible to get a script to run a command while another program is running. All it needs to do is print to the command line and then I can press enter to execute it. 

Thanks.

---

### Post by Snow986 on 2009-10-30
bump

---

### Post by philippe_carlo on 2009-10-30
> **Snow986 said:**
> Hi All,

   I am trying to run a simple scrip that goes to a directory, runs a command line program (ROOT for those familiar) and executes a particular command in ROOT while it is running.  I am not sure if this is even possible, so my question is what can I try to get this to work?

Here is my script:

#!/bin/bash
cd /path/to/dir
root 
echo ".x Grades.C"


'root' runs ROOT and '.x Grades.C' is what I want to show up when ROOT loads. So far it gets to running ROOT and then nothing shows up  until after I close ROOT. Again I am not sure it is possible to get a script to run a command while another program is running. All it needs to do is print to the command line and then I can press enter to execute it. 

Thanks.

Have you tried
```

#!/bin/bash
cd /path/to/dir
root && echo ".x Grades.C"

```
?

---

### Post by Snow986 on 2009-10-30
> **philippe_carlo said:**
> Have you tried
```

#!/bin/bash
cd /path/to/dir
root && echo ".x Grades.C"

```
?

Yep, no luck with it this way, however I was able to figure out that with ROOT if you use the command 'root Grades.C', it will run the macro upon entering so problem solved.  I would still like to know if it is possible for a shell script to input into running programs though. Thanks.

---

