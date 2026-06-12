---
title: "missing close, minimize, maximze, and other things"
date: 2009-11-08
forum: General Help
---

### Post by missmoondog on 2009-11-08
help!!

installed xubuntu on my machine last night. do not have/can't see the close, minimize, maximize buttons in any type window.

also, can't drag the window around even though it's so small.

see attachment for what it looks like.

any ideas?

thank you

---

### Post by Somme on 2009-11-08
Have you installed Compiz ( without Emerald ) ?

```
xfwm --replace
```

Also, you can drag your windows around by holding the Alt key :)

---

### Post by missmoondog on 2009-11-08
have seen several threads about compwiz and as far as i know, i haven't installed it. don't even know what it is, let alone install it.

here's a link to the dell site that has the specs on my monitor though. doing more searching around and piecing together stuff.

[http://support.dell.com/support/edocs/monitors/E153FPTc/English/about.htm#Specifications](http://support.dell.com/support/edocs/monitors/E153FPTc/English/about.htm#Specifications)

thanks

edit:
doing the xfvm --replace thing, gets me this, 

No command 'xfvm' found, did you mean:
 Command 'xfm' from package 'xfm' (universe)
 Command 'xpvm' from package 'xpvm' (universe)
xfvm: command not found


no,
can't drag window around holding alt key.

---

### Post by Somme on 2009-11-08
> **missmoondog said:**
> have seen several threads about compwiz and as far as i know, i haven't installed it. don't even know what it is, let alone install it.

here's a link to the dell site that has the specs on my monitor though. doing more searching around and piecing together stuff.

[http://support.dell.com/support/edocs/monitors/E153FPTc/English/about.htm#Specifications](http://support.dell.com/support/edocs/monitors/E153FPTc/English/about.htm#Specifications)

thanks

edit:
doing the xfvm --replace thing, gets me this, 

No command 'xfvm' found, did you mean:
 Command 'xfm' from package 'xfm' (universe)
 Command 'xpvm' from package 'xpvm' (universe)
xfvm: command not found


no,
can't drag window around holding alt key.

Did I said something about xfvm ( instead of xfwm ) ?

---

### Post by missmoondog on 2009-11-08
oops!

sorry. exactly why i think the command line is dumb as ****. if i wanted to be a typist, i'd go to school for it!

anyway,
typing it in correctly get the exact same thing:
No command 'xfwm' found, did you mean:
 Command 'xfm' from package 'xfm' (universe)
xfwm: command not found

edit:
don't have time to screw with this stupid install. already spent 2 days on this junk computer.

about to wipe it out and reinstall.

thanks

---

### Post by missmoondog on 2009-11-08
solved.

reinstalled from disc instead of downloading through wubi!!

now,
to be careful on these stupid nvidia updates!!  :)

---

