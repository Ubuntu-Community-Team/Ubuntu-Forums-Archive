---
title: "Su return error."
date: 2006-04-06
forum: General Help
---

### Post by Gilligan Zaftig on 2006-04-06
Yea everytime i try to get to adminstator mode i get a pop up saying "Su return error" doesn't describe error or anything.

---

### Post by amohanty on 2006-04-06
1. How do you try to get to administrator mode?
2. Have you enabled the root user?

AM

---

### Post by Gilligan Zaftig on 2006-04-07
[QUOTE=amohanty]1. How do you try to get to administrator mode?
2. Have you enabled the root user?

AM[/QUOTE]

1. In anything that needs me to go into admin mode. Adjust clock, Network settings, etc. Everything that has an admin mode button that i click i don't get a password require message anymore. just a pop up saying Su return with error.
2. Yes

---

### Post by amohanty on 2006-04-07
Can you post the contens of /etc/sudoers?

AM

---

### Post by Neo Ex on 2006-04-07
In the past I enabled the root user and tried to log in with 'su', and I also encountered problems. So, now I don't have the root user enabled, and, if I need to log in as root from the console, I use 'sudo -i': it does almost the same thing, without problems ;)

---

### Post by Gilligan Zaftig on 2006-04-07
[QUOTE=Neo Ex]In the past I enabled the root user and tried to log in with 'su', and I also encountered problems. So, now I don't have the root user enabled, and, if I need to log in as root from the console, I use 'sudo -i': it does almost the same thing, without problems ;)[/QUOTE]
what about when i need to access the admin mode for say stuff like the network settings or manging users.

---

### Post by amohanty on 2006-04-08
> what about when i need to access the admin mode for say stuff like the network settings or manging users.

**sudo -s**

gives you a root shell within yours.

HTH
AM

---

