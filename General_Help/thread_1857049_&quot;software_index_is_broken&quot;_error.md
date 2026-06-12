---
title: "&quot;software index is broken&quot; error?"
date: 2011-10-09
forum: General Help
---

### Post by mozozo4 on 2011-10-09
Hi, i am running ubuntu 11.04 unity 2d and im new to ubuntu.  And when i go to update manager it gives me a message that says 

"software index is broken It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

So i put that command in terminal and it gives me this error message, E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

What do i do?

---

### Post by matt_symes on 2011-10-09
Hi

Open a terminal and type

```
sudo dpkg --configure -a
```

Kind regards

---

### Post by mozozo4 on 2011-10-09
sorry i didnt recognize it was that easy

it worked!!!!!

Thank you so much matt_symes

---

### Post by claire14 on 2011-10-28
hi i'm on ubuntu 10.10 and i got the same message , this fixed it thankyou :)

---

