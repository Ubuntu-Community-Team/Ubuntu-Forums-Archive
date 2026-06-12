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

### Post by Vaphell on 2011-01-20
**chmod** not chmond

also forums support [code] tags, use them when you paste some code

---

