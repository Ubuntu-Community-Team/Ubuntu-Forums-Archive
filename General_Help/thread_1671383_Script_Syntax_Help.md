---
title: "Script Syntax Help"
date: 2011-01-19
forum: General Help
---

### Post by ZeroOzzy on 2011-01-19
Hi im new to these forums so Hello!!! =)

Im just starting to learn to script and I need to know what this doesnt work, heres the error I get

"chmond: command not found"
The error goes away when I delete the line with "dirname $NAME" in it. 

please any help, iv been searching the net for about 2 hours now!

----------
#!/bin/sh  

echo "enter file name with extension and path"
read NAME

FULLPATH=`dirname $NAME`
OPENFILE="open "$NAME
OPENPATH="open "$FULLPATH
echo $OPENFILE > /Users/admin/Desktop/tmpLink
echo $OPENPATH >> /Users/admin/Desktop/tmpLink
chmond +x /Users/admin/Desktop/tmpLink
-----------

---

### Post by anglican on 2011-01-20
> **ZeroOzzy said:**
> Hi im new to these forums so Hello!!! =)

Im just starting to learn to script and I need to know what this doesnt work, heres the error I get

"chmond: command not found"
The error goes away when I delete the line with "dirname $NAME" in it. 

please any help, iv been searching the net for about 2 hours now!

----------
#!/bin/sh  

echo "enter file name with extension and path"
read NAME

FULLPATH=`dirname $NAME`
OPENFILE="open "$NAME
OPENPATH="open "$FULLPATH
echo $OPENFILE > /Users/admin/Desktop/tmpLink
echo $OPENPATH >> /Users/admin/Desktop/tmpLink
chmond +x /Users/admin/Desktop/tmpLink
-----------
You've got an extra "n" in there, the line should be:
```
chmod +x /Users/admin/Desktop/tmpLink
```

H

---

### Post by geirha on 2011-01-20
On a pragmatic and semantic note, you should use lowercase variable names, quote the expansions in double-quotes (" ") and use $( ) instead of backquotes, ` `. I strongly recommend reading [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide). It's the only really good guide for bash and POSIX sh scripting; The vast majority of scripting guides and tutorials on the net will teach you malpractice.

---

