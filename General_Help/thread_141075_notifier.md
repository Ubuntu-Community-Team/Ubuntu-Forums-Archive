---
title: "notifier"
date: 2006-03-07
forum: General Help
---

### Post by 1oki on 2006-03-07
Does anyone know if there is a way to get a notification either through email or even just a piece of software that will allow you to get notified when your ubuntu box comes back online? I am running a 5.10 PDC, and am accessing it through SSH. I know I can keep trying to connect, but I would like to see if there is an automated system out there! thanks!

-L
:-D

---

### Post by colo on 2006-03-07
Just utilize a custom init-script in your default-runlevel, notifying you via "mail", or maybe some CLI-XMPP-application (Jabber). Another approach would be to have the remote machine connect via ssh2 to your local one, and automatically exec "wall" on your local machine. Should not be a problem with pubkeyauth and "ssh -c".

I don't know any drop-in solutions for this kind of problem, though.

Hth.

---

### Post by 1oki on 2006-03-07
danka! i will check it out!

-L

---

