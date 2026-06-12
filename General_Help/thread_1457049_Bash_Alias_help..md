---
title: "Bash Alias help."
date: 2010-04-18
forum: General Help
---

### Post by sparcxl on 2010-04-18
Anyone know why this does not work or have a better idea for creating this alias?

alias rd='rdesktop -g 1200x700 $1 &'

from the terminal I am trying to alias rdesktop using 'rd <server>' without hanging the current terminal session.

I can remove the & and the alias works, but not with it. Should I be doing this another way?

Thanks!

---

### Post by john newbuntu on 2010-04-18
Functions are ideal for this purpose.  You can pass your <server> param as $1 into a function, which then can append the ampersand.

function rd()
{
   rdesk....blabla.. ${1} &
}

---

### Post by sparcxl on 2010-04-18
Excellent. Thank you.. That just opened up a new world for me. Much appreciated!

---

### Post by gmargo on 2010-04-18
> **sparcxl said:**
> Anyone know why this does not work

It does not work in bash because aliases do not take arguments.  And as John pointed out, functions do.

---

