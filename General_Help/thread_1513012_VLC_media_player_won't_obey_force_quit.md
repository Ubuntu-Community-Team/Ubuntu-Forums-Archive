---
title: "VLC media player won't obey force quit"
date: 2010-06-18
forum: General Help
---

### Post by ChubbySauce on 2010-06-18
VLC media player freezes so often, Ive tried reinstalling it, nothing

so I tried force quit alt+F2 click nothing

tried the force quit panel add on still nothing TT____TT.

:U it functions to the point where it can do most things but not play any musical media

any ideas?

---

### Post by Smart Viking on 2010-06-18
Here is a way to force quit it with the terminal.

First do this:

```
ps -e | grep -i VLC
```Then you will hopefully see it, eventually there is more than one.

The first 4 numbers you see is the process "ID" number or whatever, you are gona refer to that when you kill it. (it might be only 3 numbers or 5 numbers.)

```
kill -9 <insert the number here>
```The "-9" in the code means that it is "overkill" of the process. you can also do it without the "-9".

I hope this helped. :)

EDIT: I understand this will only help you with killing VLC, not actually help you solve the problem with VLC freezing... But there are many other great players, mplayer and exaile are two i like. :)

---

