---
title: "Vinagre not working as expected"
date: 2011-01-09
forum: General Help
---

### Post by Mgiacchetti on 2011-01-09
[SIZE=5][COLOR=Red]**I do not wish to install any other vnc client.**[/COLOR][/SIZE]

Problem:
Vinagre will not connect to other ubuntu machine unless I manually login to that machine locally.

Expected outcome:
To be able to login via vinagre WITHOUT having to login to the other machine locally.

Ubuntu 10.10

---

### Post by spiky001 on 2011-01-09
Hi have you set vinagre to accept connections automatically

---

### Post by Mgiacchetti on 2011-01-09
> **spiky001 said:**
> Hi have you set vinagre to accept connections automatically
yes, i have been through all the settings and until i login locally on the machine i wish to remote, i cannot remote into it.

---

### Post by spiky001 on 2011-01-09
I have my remote machine set so no login required System/Administration/Users set it to no password on login

---

### Post by tredegar on 2011-01-09
> Problem:
Vinagre will not connect to other ubuntu machine unless I manually login to that machine locally.

Expected outcome:
To be able to login via vinagre WITHOUT having to login to the other machine locally.

You need to start a **vncserver** on the remote machine. Then you will be able to connect to it.

---

### Post by Mgiacchetti on 2011-01-09
> **spiky001 said:**
> I have my remote machine set so no login required System/Administration/Users set it to no password on login
good idea, but presents a security risk, i have multiple users using the machine i wish to remote into.

---

### Post by spiky001 on 2011-01-09
how about using ssh

---

