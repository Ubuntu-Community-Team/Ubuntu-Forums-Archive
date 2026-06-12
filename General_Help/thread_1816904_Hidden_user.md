---
title: "Hidden user?"
date: 2011-08-02
forum: General Help
---

### Post by Burillo on 2011-08-02
Is it possible to set up a user in such a way that other users wouldn't be aware of his existence?

---

### Post by haqking on 2011-08-02
> **Burillo said:**
> Is it possible to set up a user in such a way that other users wouldn't be aware of his existence?

create a user then from terminal give them a UID below 1000 so....

create bob then

sudo usermod -u 800 bob

or whatever UID is unused, anything below 1000 is treated as a sysem account

---

### Post by WorMzy on 2011-08-02
Depends on the user's level of expertise. Anyone can read /etc/passwd, so if they know about it, they can see a list of all the users.

---

### Post by AlphaLexman on 2011-08-02
> **haqking said:**
> create a user then from terminal give them a UID below 1000 so....

create bob then

sudo usermod -u 800 bob

or whatever UID is unused, anything below 1000 is treated as a sysem account
Wouldn't 
```
ls -l /home
```
still show the user ??

**EDIT:** Wormzy beat me to it.

---

### Post by haqking on 2011-08-02
> **AlphaLexman said:**
> Wouldn't 
```
ls -l /home
```still show the user ??

**EDIT:** Wormzy beat me to it.


yeah as would the etc/passwd entry.

anyone one with a little knowledge could find the presence of a user for sure.

just providing a possible solution for something that isnt really possible depending on what the OP really wants to achieve

the question really is why ?

---

### Post by haqking on 2011-08-02
Do you want to just hide them from the login screen ?

---

### Post by Burillo on 2011-08-02
I want it to be there but:
a) not showing up on login screen
b) not showing up on kdesudo and the like but still being able to administer the machine
c) (optionally) not being visible as a user account under control panel (i'm using KDE)

of course, someone knowledgeable enough can see the user straight away, i just want him not being seen by another logged in user in "everyday" use cases.

Is it also possible to have a login screen where i can both click on a username and enter it manually? because otherwise i'd have to login through terminal.

---

### Post by haqking on 2011-08-02
> **Burillo said:**
> I want it to be there but:
a) not showing up on login screen
b) not showing up on kdesudo and the like but still being able to administer the machine
c) (optionally) not being visible as a user account under control panel (i'm using KDE)

of course, someone knowledgeable enough can see the user straight away, i just want him not being seen by another logged in user in "everyday" use cases.

Is it also possible to have a login screen where i can both click on a username and enter it manually? because otherwise i'd have to login through terminal.


well if you follow my UID suggestion earlier that will stop them appearing from login and everyday use.  However like as been said it is easy ti find if the user exists.

choose a valid UID below 1000.

like i say though it is still relatively easy to see if this user exists.

and not sure about control panel in KDE, i would need to check it but i will leave that for you to see by doing some testing.

peace

---

