---
title: "split shell window"
date: 2010-11-18
forum: General Help
---

### Post by fantastic on 2010-11-18
Is there a shell window where it can be split vertically and have 2 consoles going in one window side-by-side?

I didn't see where I could configure the GNOME Terminal for it.

---

### Post by Hippytaff on 2010-11-18
> **fantastic said:**
> Is there a shell window where it can be split vertically and have 2 consoles going in one window side-by-side?
 
I didn't see where I could configure the GNOME Terminal for it.
 
Don't know...but you can open two terminals!? :-)

---

### Post by fantastic on 2010-11-18
> **Hippytaff said:**
> Don't know...but you can open two terminals!? :-)

Already do that, but thank you.

---

### Post by chaanakya_chiraag on 2010-11-18
I'm not sure, but the program screen may do the trick...

---

### Post by chaanakya_chiraag on 2010-11-18
Actually, the terminal emulator terminator is JUST what you are looking for!! :)  It's in the repos.

---

### Post by Hippytaff on 2010-11-18
Emacs terminal emulator might be another solution
 
[http://www.gnu.org/software/emacs/manual/html_node/emacs/Terminal-emulator.html](http://www.gnu.org/software/emacs/manual/html_node/emacs/Terminal-emulator.html)

---

### Post by nothingspecial on 2010-11-18
type ```
byobu
```

You already have it

Then Ctrl - A (together)

Then Shift - S (together)

Switch between them by pressing Ctrl - A then Tab

Create a new session by pressing F2, switch between them using F3 and F4


or..........



```
sudo apt-get install dvtm
```

```
dvtm
```

Ctrl - G then C

repeat another 2 times if you like then Ctrl - G then G and you will have a nice 4 window grid.

Or terminator

---

### Post by fantastic on 2010-11-18
> **chaanakya_chiraag said:**
> Actually, the terminal emulator terminator is JUST what you are looking for!! :)  It's in the repos.

Thanks chaanakya_chiraag and nothingspecial. Terminator works for me.

And thank you all. Learned something new today.

---

### Post by celldweller1591 on 2010-11-19
try ctrl+shft+t for a new tab window inside your bash. it will work. :)

---

