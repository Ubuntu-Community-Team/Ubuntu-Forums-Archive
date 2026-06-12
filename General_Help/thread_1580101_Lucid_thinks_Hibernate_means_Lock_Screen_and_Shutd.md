---
title: "Lucid thinks Hibernate means Lock Screen and Shutdown means Logout"
date: 2010-09-22
forum: General Help
---

### Post by evanct on 2010-09-22
The latter only happens sometimes, like today, but the former has been happening ever since my install of Lucid a couple months ago.

---

### Post by JC Cheloven on 2010-09-22
It could be about this: The logout window shows the highlighted option in quite a stange way for me, depending on the computer. It usually highlights the option below the mouse, but in fact, if you hit enter the first option (shutdown) is performed. 

So, try clicking on the hibernate option (not press enter), and try Ctrl-Alt-L  and see if the lock screen action is performed.

A very simple thing, but perhaps ...

---

### Post by evanct on 2010-09-22
I'm not really sure what you mean... I'm using the Shut Down Menu(the one called "Shut Down..." in Add to Panel). I click Hibernate, the screen immediately goes black for a few moments, and then the mouse cursor is visible again and when I move it I get the password prompt for unlocking the screen.

---

### Post by JC Cheloven on 2010-09-23
> **evanct said:**
> I'm not really sure what you mean... I'm using the Shut Down Menu(the one called "Shut Down..." in Add to Panel). I click Hibernate, the screen immediately goes black for a few moments, and then the mouse cursor is visible again and when I move it I get the password prompt for unlocking the screen.

If you are CLICKING hibernate (don't selecting it pressing enter at keyboard), then what I said doesn't apply. 

Then, simply your computer cannot hibernate, for some reason. It is necessary to have at least as much swap disck space as RAM, and it's generally adviced to have even twice. Do you have that? If unsure, please post the output of this at terminal:
```
free -m
```
And, does Ctrl-Alt-L work properly for locking the screen?

---

### Post by Irony on 2010-09-23
> **evanct said:**
> I'm not really sure what you mean... I'm using the Shut Down Menu(the one called "Shut Down..." in Add to Panel). I click Hibernate, the screen immediately goes black for a few moments, and then the mouse cursor is visible again and when I move it I get the password prompt for unlocking the screen.
You will have to wait a little time for it to actually hibernate - if you move the mouse before it has hibernated it goes to an unlocking the screen... same with suspend, don't touch the mouse.

---

