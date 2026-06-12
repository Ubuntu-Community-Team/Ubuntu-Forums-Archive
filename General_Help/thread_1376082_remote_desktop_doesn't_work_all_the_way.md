---
title: "remote desktop doesn't work all the way"
date: 2010-01-08
forum: General Help
---

### Post by itachisxeyes on 2010-01-08
i have set up a remote connection between two ubuntu 9.10 desktops connected on my LAN here. and i can manipulate the other desktop, i can see it around the corner opening menus and what not, but on the remote desktop, all it shows is the mouse moving, it doesn't show menus i'm opening or even a right click. 
what is the deal?

---

### Post by JimmyK377 on 2010-01-23
I've encountered this problem trying to use remote desktop viewer on UNR 9.10 to view the desktop on a regular 9.10 laptop

I'm not sure if there is any better solution than disabling compiz, like:

```
$ metacity --replace
```

---

### Post by itachisxeyes on 2010-01-23
> **JimmyK377 said:**
> I've encountered this problem trying to use remote desktop viewer on UNR 9.10 to view the desktop on a regular 9.10 laptop

I'm not sure if there is any better solution than disabling compiz, like:

```
$ metacity --replace
```

now should that be done do both machines or just one or the other? and btw thanks for answering XD i though this thread was dead!

---

### Post by nerxgas on 2010-02-07
i just ran into the same problem
all i had to do to fix it was:

just do this on your host machine
go to System>Appearance
click the Visual Effects tab
then select the "None" radio button

---

