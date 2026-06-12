---
title: "Openbox menu"
date: 2009-10-04
forum: General Help
---

### Post by TwinStinger on 2009-10-04
Hi there.

Got excellent help with a question a few minutes ago which solved that problem but then i ran into a new one.
Figured it was best to start a new thread.


This is what i would like to put in my openbox menu.

terminator --command=echo 1 | btv 

the "echo 1 | btv" bit  works like a charm when done from a command line.

The btv-program is started and option #1 selected. 

Why doesn't it work when I put it into my openbox menu editor.

"terminator --command=btv" works fine but 
"terminator --command=echo 1 | btv" doesn't.

Anyone got any idea or a solution to this.

More than happy if this could be solved.

edit:  Figured following out 

When done from terminal    
terminator --command=echo 1 | btv     doesn't work but 

terminator --command="echo 1 | btv"   does 

How ever terminator --command="echo 1 | btv" doesn't work from the openbox menu.

EDIT AGAIN:  
terminator --command="echo 1 | btv"   works very well indeed, at least if you remember to save your openbox menu-file before trying it out... :-)

 



/ Twinned

---

