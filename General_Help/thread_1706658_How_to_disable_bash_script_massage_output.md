---
title: "How to disable bash script massage output"
date: 2011-03-14
forum: General Help
---

### Post by artishox on 2011-03-14
I want to write a script that searches some directory for specific files and then performs action with it. I managed to write a script, but I cannot find how to disable all but echo messages from script
Lets say my script is:
```

#!/bin/bash
comFiles=(`ls -1 *.com | grep ".com" | sed "s/.com//"`)
for comLine in ${comFiles[@]}
do
   echo $comLine
done

```it searches current directory for .com files and echoes them
problem is that when there is no .com files in this directory I get this message:
```
ls: cannot access *.com: No such file or directory
```Question is what I need to do to disable later, but still keep echo output?

Thanks

p.s.
redirecting output to like this ./script.sh > /dev/null
doesn't work for me as it doesn't echo lines I need to see

---

### Post by nothingspecial on 2011-03-14
You need to redirect only the errors

Input 0
Output 1
Error 2

so ```
2> /dev/null
```

---

### Post by artishox on 2011-03-14
Thanks this works for me.

---

### Post by Telengard C64 on 2011-03-14
nothingspecial was faster than me  :P

> ```
ls: cannot access *.com: No such file or directory
```

If you don't want to see the error message you can redirect stderr to /dev/null

```
foo$ ls nosuchfile
ls: cannot access nosuchfile: No such file or directory
foo$ ls nosuchfile 2> /dev/null
foo$
```

[Parsing the output of **ls** is a bad idea.](http://mywiki.wooledge.org/ParsingLs)

You can use the [find](http://www.linuxcommand.org/man_pages/find1.html) command to perform actions on a set of files which match a pattern.

```
foo$ find -iname '*movie*' -exec grep -i 'cthulhu' '{}' \;
Cthulhu Mansion (1992)
foo$
```

I see you are piping the output of **grep** into **sed**. You can surely do away with the pipeline and use [awk](http://www.linuxcommand.org/man_pages/awk1.html) instead. The basic syntax is **awk 'PATTERN { ACTION }' FILE(S)**.

```
foo$ awk '/Cthulhu/ { print }' movies.txt
Cthulhu Mansion (1992)
foo$
```

I do not fully understand what you expect this script to do. I will make a small attempt at it anyway, using the information above.

```
find -name '*.com' | awk '/[.]com/ { sub(/[.]com/,"") ; print }'
```

---

