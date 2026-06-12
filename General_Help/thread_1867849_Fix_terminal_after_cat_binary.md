---
title: "Fix terminal after cat binary"
date: 2011-10-23
forum: General Help
---

### Post by erixnow on 2011-10-23
In Ubuntu how do you reset the terminal to a "sane" state.  

After cat'ing a binary the usual problem with garbled text happened.  




-THX
Eric Peyser

---

### Post by xaronic on 2011-10-23
Just reload the bash terminal.
This happens when you SSH with putty too.

---

### Post by nothingspecial on 2011-10-23
Ctrl-C 

Ctrl-L

---

### Post by erixnow on 2011-10-23
reloaded bash via a hard kill  in another terminal session forcing a reload.... NO GO.  Also tried Ctrl -L.
The standard terminal resets that work on other *NIX.  I had found a way a while back that worked perfect......  In a rush I didnt put it in my cliffs notes.


Still Stuck garbled land ! :(

I agree that linux thinks you know exactly what you are doing.... kinda like C.  That is why it is nice.  I dont know why they dont alias "strings" as "cat".  

-THX
Eric Peyser

---

### Post by erixnow on 2011-10-24
No one has come across such a common problem?  I think this is probablyone of the top mistakes that can be made on a *NIX box.  Any thoughts would be greatly appreciated !!!!



Thx
Eric Peyser

---

### Post by dcstar on 2011-10-25
> **erixnow said:**
> No one has come across such a common problem?  I think this is probablyone of the top mistakes that can be made on a *NIX box.  Any thoughts would be greatly appreciated !!!!


Old problem, old solutions:

[http://docstore.mik.ua/orelly/unix/upt/ch42_04.htm](http://docstore.mik.ua/orelly/unix/upt/ch42_04.htm)

---

### Post by gmargo on 2011-10-25
I normally use the **reset** command, followed by a Control-J (instead of Enter).  That will work 99% of the time.

Why Control-J?  The Control-J is a Newline.  Enter is a Carriage Return (aka Control-M).  In normal "cooked" mode, the line discipline translates the Control-M into Control-J.  Dumping a binary often leaves the terminal in "raw" mode instead, which means that Enter will not be translated and will not terminate the entered command.  Hence you enter the Control-J manually to terminate the command.

---

