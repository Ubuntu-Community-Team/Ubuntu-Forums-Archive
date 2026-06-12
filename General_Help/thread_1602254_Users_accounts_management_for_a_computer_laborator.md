---
title: "Users accounts management for a computer laboratory"
date: 2010-10-21
forum: General Help
---

### Post by krige on 2010-10-21
Hello,

I am looking for a system to manage the users accounts of a computer laboratory in a centralized way, storing all them in one computer acting as server.

How are these systems called? Is there any one in particular suggested for Ubuntu systems?

---

### Post by P4man on 2010-10-21
Its generally called "Directory Services", and you can achieve that through (open)LDAP.

---

### Post by irv on 2010-10-21
If you want to learn about LDAP just go to the package manager and install the ldaptor-doc, it covers:
* An introduction to LDAP
 * The Ldaptor library API
 * Slides for a talk "Creating a simple LDAP application"
It would be a place to start

---

### Post by krige on 2010-10-21
Thank you guys!!! Very much appreciated :)

---

### Post by krige on 2010-10-21
Wait a second... application? API? What I wanted actually is an application like the "User Settings" found in System / Administration / Users and Groups, which I would install in a server 'A' and create my user accounts once for all. I would then install a client application in 'B', 'C' and all the other computers of the laboratory, setting them to get the users from the server 'A'.

---

### Post by krige on 2010-12-02
Sorry, wrong message.

---

