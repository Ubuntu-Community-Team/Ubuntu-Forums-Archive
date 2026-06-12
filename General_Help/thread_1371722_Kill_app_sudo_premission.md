---
title: "Kill app sudo premission"
date: 2010-01-03
forum: General Help
---

### Post by pieguy on 2010-01-03
How do you kill permission to an app that you have just accessed.  Say you have run SPM(synaptic package manager) and enter your password to run it.  You close the app, but for a default amount of time the program can be run without password prompt.

I will give an example of how to kill permission in the terminal, you have sudo'ed and given password.  Now do kill permission you would sudo -k and you are prompted immediately if you sudo again before the default time from the previous sudo is up because you killed permission.

How do you kill permission outside the terminal shell that has been give to app/s before the permission time expires? because sudo -k in terminal does not kill permission to app/s you passworded to run.

---

### Post by todak on 2010-01-03
This page will show you what you need to know: [https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout) :)

---

### Post by pieguy on 2010-01-03
Thats one why of doing it and I suppose if there isnt a one time use way to kill permission like sudo -k does in terminal, then thats the way you'd do it.

---

### Post by todak on 2010-01-04
There should be a key icon that appears in the tray when you launch a sudo app. Just click on that to kill the elevated priveleges.

---

