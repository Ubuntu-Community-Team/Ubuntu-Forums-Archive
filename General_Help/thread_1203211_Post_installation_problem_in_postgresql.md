---
title: "Post installation problem in postgresql"
date: 2009-07-03
forum: General Help
---

### Post by babbar.ankit on 2009-07-03
I have installed postgresql and as per the instruction procedure
To enable TCP/IP connections, edit the file /etc/postgresql/8.3/main/postgresql.conf
When I try to edit and save the change with text editor I get this message...
(In the file I have simply uncomment one line and save it)

**[COLOR=DarkGreen]"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."[/COLOR]**
What should I do

---

### Post by masux594 on 2009-07-03
well, you must edit the file with sudo! Try this..
> sudo gedit /etc/postgresql/8.3/main/postgresql.conf

Sysc, A

---

### Post by babbar.ankit on 2009-07-03
Thankyou! IT worked perfectly

---

### Post by masux594 on 2009-07-03
P.s. I work with postgreSQL database since 2 years.. On 26 of June was released postgreSQL 8.4!! Work fine =)

Sysc, A

---

