---
title: "calling a script"
date: 2010-03-25
forum: General Help
---

### Post by ub007 on 2010-03-25
Hi,

I'm trying to call a shell script from within another scipt, but returns with a
`command not found` error msg.

> script_name=$1
./$script_name &; exit 0

I think its something to no with the "./" bit.

i also tried 
"./"$script_name &; and
"./$script_name" &
no luck. 


Cheers
David

---

### Post by jobix on 2010-03-25
In your script, insert these lines after the "script_name=$1" line:

> pwd
echo $script_name

That will tell you two things - 1) where the script thinks it is, and 2) what it is trying to execute.

---

