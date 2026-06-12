---
title: "Is there a better way?"
date: 2011-07-15
forum: General Help
---

### Post by conradin on 2011-07-15
Hi Everyone!,
 I have 600 some tcl files that I would like to append with a read line at the end of the file. 
I came up with a method to do it, but I'm not a big fan of it. Additionaly, bash warns that the input file is the output file. The code is below, Can anyone come up with a more elegant way to append  all the files in a directory?
```
       
 #!/bin/bash
        for i in $( ls *.tcl ); do
           cat $i "read" >> $i 
        done

```

---

### Post by squaregoldfish on 2011-07-16
The >> directive tells bash to add things to the end of the file instead of overwriting it. So, instead of using cat, you can just do
```

echo "read" >> $i
```

Steve.

PS I hope you have a backup of all these files - it's very easy to accidentally destroy them when doing stuff like this!

---

### Post by conradin on 2011-07-16
Oh yeah I have back ups. 
these are example scritps from a book Im reading. Practical Programing in TCL & Tk by brent Welch
The book is great(!!!!!!!), but the examples, they are made to be interactive. 
I just want them to run. So I made a script to at "#!/usr/bin/expect" to all of them at the top. Then I went out for pizza, And after that It was like I couldnt think straight. Dam You Pat's Pizza!!! 

Thanks for the help! :guitar:

---

### Post by nothingspecial on 2011-07-16
> **conradin said:**
> Hi Everyone!,
 I have 600 some tcl files that I would like to append with a read line at the end of the file. 
I came up with a method to do it, but I'm not a big fan of it. Additionaly, bash warns that the input file is the output file. The code is below, Can anyone come up with a more elegant way to append  all the files in a directory?
```
       
 #!/bin/bash
        for i in $( ls *.tcl ); do
           cat $i "read" >> $i 
        done

```

You don't need ls

```
for i in *.tcl
```

Always quote your variables

```
cat "$i" "read" >> "$i"
```

So

```
for i in *.tcl; do echo "read" >> "$i"; done
```

---

