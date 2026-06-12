---
title: "bash text/plain"
date: 2012-05-04
forum: General Help
---

### Post by oklokl on 2012-05-04
./1.sh 1234txt > test2
(Is complicated)
Result=
[COLOR=Red]test2[/COLOR]


[COLOR=Red]How I want to ...[/COLOR]
./1.sh 1234txt       or ./1.sh *.txt

Result=
 [COLOR=Red]1234txt[/COLOR][COLOR=Red]    .. [/COLOR]The original name for himself as
 

 How do I modify? ..
 I do not need to print the screen.
 Need only to convert ..

Only text / plain I'd like to convert ..
It is difficult
 Please help me.
](*,)


[http://www.yolinux.com/TUTORIALS/LinuxTutorialCgiShellScript.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCgiShellScript.html)


1.sh


#!/bin/bash
CAT=/bin/cat
COLCRT=/usr/bin/colcrt

echo Content-type: text/plain
echo ""

if [[ -x $CAT && -x $COLCRT ]]
then
        $CAT $1 | $COLCRT
else
        echo Cannot find command on this system.
fi

---

### Post by codemaniac on 2012-05-04
FIRST OF ALL PLEASE PLEASE USE CODE TAGS .
Please convey your message clearly so that we can help you out .

If you dont want to print anything on the console then you need to redirect your scripts output to a file as you did in your first line or comment the echo lines .
Still i am in dark about what you actually want to do .

---

### Post by oklokl on 2012-05-04
[ATTACH]217272[/ATTACH]

to

12345txt[COLOR=Red]Glade project (application/x-glade)[/COLOR]  > 12345txt[COLOR=Red]**[B]text/plain**[/B][/COLOR]

[ATTACH]217273[/ATTACH]

I want to change file attributes.
 Automatic Properties. Is specified is inconvenient.

how to should be changed.?

Please explain BASH Shell Script

Thank you.

---

