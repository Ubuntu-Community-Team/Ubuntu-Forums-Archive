---
title: "Help with error message"
date: 2009-10-04
forum: General Help
---

### Post by raven9613 on 2009-10-04
when ever i try to download/install something (add/remove programs/terminal) i get this error message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

what should i do!?
btw this hasn't always happened its just recently.
thx

---

### Post by ermeyers on 2009-10-04
What are you typing to "add/remove programs/terminal" to get this error message?

---

### Post by Portable_Jim on 2009-10-04
> **raven9613 said:**
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
This is telling you to open up terminal (Applications -> Accessories -> Terminal) and copy and paste the following command.
```
sudo dpkg --configure -a
```Then press enter.

Please note: The keyboard shortcuts for the terminal are not the same as other applications, so right click on the terminal window to access the paste function (or use the menu item)

---

### Post by ermeyers on 2009-10-04
It would still be good to know the command that leads to that.

---

### Post by Portable_Jim on 2009-10-04
> **ermeyers said:**
> It would still be good to know the command that leads to that.
It would.

---

### Post by ermeyers on 2009-10-04
Is that a Jesus-fish wrapped around your tux?

---

### Post by Portable_Jim on 2009-10-05
> **ermeyers said:**
> Is that a Jesus-fish wrapped around your tux?
Yes

---

### Post by MelDJ on 2009-10-05
> **raven9613 said:**
> when ever i try to download/install something (add/remove programs/terminal) i get this error message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

what should i do!?
btw this hasn't always happened its just recently.
thx

did you interrupt an installation or upgrade? for example, did you exit terminal while running apt-get? thats most probably the cause of it. the solution to it is sudo dpkg --configure -a as said above

---

