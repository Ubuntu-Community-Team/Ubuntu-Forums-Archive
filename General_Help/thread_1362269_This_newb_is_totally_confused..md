---
title: "This newb is totally confused."
date: 2009-12-22
forum: General Help
---

### Post by colorfulcolleen on 2009-12-22
Okay, so I need some major help.
I was trying to add a new user on terminal, but accidentally added a testuser before finding out that I don't exactly need it. So how to I get rid of it? I looked it up, but it told me only how to get rid of a regular user, and to give a username, which it technically doesn't have. I am majorly stumped.

---

### Post by lavinog on 2009-12-23
Can you use the users and groups application in the system>admin menu?

I am not exactly sure what the problem is...is testuser not a regular user?

```

cat /etc/passwd

```
this will print a list of the users on the system, but keep in mind some users are just for different services so don't try and remove them.

---

### Post by steveneddy on 2009-12-23
Top bar - select

System --> Administration --> Users and Groups

Click the "Unlock" button on the bottom

highlight the user that you want to delete

click the "Delete" button

Close the application

---

