---
title: "can't access any admin tools"
date: 2006-01-27
forum: General Help
---

### Post by dknoppix on 2006-01-27
Hey,

I had this problem before, but I can't access any admin tools :(

I click on one (ie networking), and it says "Starting Networking" then dissapears. It does it for everything.

Also, it only does this on my computer....when I install it on other ones it works....

Thanks,

dk

---

### Post by dknoppix on 2006-01-27
Also,

In another thread they tell me to do this under visudo:

%admin ALL=(ALL) ALL

But I don't know If I'm admin

Also I'm used to get to the terminal screen by pressing "Ctrl-Alt-F5 (or #...)

but it doesn't show up

dk

---

### Post by Ocxic on 2006-01-27
[QUOTE=dknoppix]Also,
In another thread they tell me to do this under visudo:
%admin ALL=(ALL) ALL
But I don't know If I'm admin
Also I'm used to get to the terminal screen by pressing "Ctrl-Alt-F5 (or #...)
but it doesn't show up
dk[/QUOTE]


replace admin with your username or add
%your_username ALL=(ALL) ALL
to the end of the file

this file tells the computer who is allowed to use the sudo command

---

### Post by dknoppix on 2006-01-27
[QUOTE=Ocxic]replace admin with your username or add
%your_username ALL=(ALL) ALL
to the end of the file

this file tells the computer who is allowed to use the sudo command[/QUOTE]

Ok thanks :)

I'll try it in a few hours...right now I'm in windowz :mad: 

Also, why would ubuntu do this?

dk :)

---

### Post by dknoppix on 2006-01-28
Nope...still didn't work :(

Also there wasn't "%admin ALL=(ALL) ALL" so I just added that and my username...

dk

---

### Post by dknoppix on 2006-01-31
Bump?

---

