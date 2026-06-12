---
title: "Bash scripting help. Global variables issue"
date: 2011-04-05
forum: General Help
---

### Post by FunkyAndroid on 2011-04-05
Hey everybody,

I'm trying to write a bash script that will automatically generate a simple template for LaTeX that I'll be using to aid in starting my written homeworks. The only problem is that my variable $filename only has the value that I want inside the block.  Once bash exits the IF statement, the variable $filename returns to being "nowork".  This seems like something super simple, but I can't find anything to show me how to edit the variable inside of a code block.

Thanks for any help,
-Jack

```

#!/bin/bash
#echo $filename
export filename="nowork"
if [ $# -gt 0 ]
then
  courseNum=$1
  hwNum=$2
  filename="ecs"$courseNum"_hw"$hwNum

#Bunch of echos here that I edited out to save space...

else #proper number of inputs not received
  echo "Course Number and Homework Number required." >&2
  echo "usage: genhw.sh course_number hw_number" >&2
fi > $filename

```

---

### Post by DaithiF on 2011-04-05
when you redirect the output of a command using > bash sets up the redirection before executing the command, ie. it first opens the file $filename for writing, then executes the contents of the if command and writes the output to the opened file.

So changing the value of $filename within the if command has no effect.

I would suggest you redirect the output to a temp file, then rename it to $filename, something like:

```
tempfile=$(mktemp)
if etc...
  snip...
fi > $tempfile && mv $tempfile $filename

```

---

### Post by FunkyAndroid on 2011-04-10
Sorry for the delayed response, got hung up on some other projects.  This worked perfectly! Thanks for the help and for explaining why my previous script didn't work.

---

