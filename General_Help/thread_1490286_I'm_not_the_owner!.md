---
title: "I'm not the owner?!"
date: 2010-05-22
forum: General Help
---

### Post by pr0t3g3 on 2010-05-22
I'm using a laptop that is solely owned and used by me, however Ubuntu doesn't seem to feel the same-_-;.. no really... When I tried to access lost+found and root in file browser it says:  


[SIZE=2][B]The folder contents could not be displayed.

[SIZE=1]You do not have the permissions necessary to view the contents of "lost+found".[/SIZE][/B][SIZE=1]


and then the root as well... I'm the flipping admin.. why can't I access it?


It doesn't even ask for any passwords.



Edit:  Another thing is, when I right click and select properties and then permissions it says that:"Your not the owner" ... o.O   then who is?  
[/SIZE][/SIZE]

---

### Post by wojox on 2010-05-22
Read up on [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by pr0t3g3 on 2010-05-22
and the lost+found?

---

### Post by wojox on 2010-05-22
Alt+F2

```
gksudo nautilus
```

---

### Post by pr0t3g3 on 2010-05-22
> **wojox said:**
> Alt+F2

```
gksudo nautilus
```

oh ... I see... thanks

The reason I asked was because I wanted to find the folder my epsxe folder; a game folder with the savestates bios and other fun stuff... =_= I'm starting to think I'm not going to ... I downloaded it via the terminal ... but I never saw a folder...

Edit:  meh I found it in

places>computer>file system>opt

---

