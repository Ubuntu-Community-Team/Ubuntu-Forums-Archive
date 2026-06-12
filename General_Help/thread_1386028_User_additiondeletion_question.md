---
title: "User addition/deletion question"
date: 2010-01-20
forum: General Help
---

### Post by chupalo on 2010-01-20
I am new to Linux and just installed Ubuntu 9.10.  I am getting familiar with some of the configurations and am really excited to start using Linux more often.

I am using the GUI and command line to learn how to add/delete users and have come across some interesting results.

When I use the command line to add a new user, I see the user added in the GUI "Users and Groups" section but there is no new folder in /home.  Question #1: why does the command line not create a new folder?  Am I missing something?

When I use the GUI to add a user, it definitely creates a new folder in /home and everything looks great.  But when I delete the user, the folder in /home remains.  Question #2: Is this normal?  Even though I've deleted the user, should the respective folder not be deleted as well?

Thanks in advance for everyones help.

FJ

---

### Post by nothingspecial on 2010-01-20
What command are you using to create the user. It should create a home directory.

```
deluser --remove-home user
```

to delete the user along with their home directory. This is so you don`t go deleting important stuff by mistake.

---

### Post by chupalo on 2010-01-20
I am using:  sudo useradd xxx

I am prompted for my password, then I check the GUI and sure enough a new user is entered but there is absolutely no folder in /home for xxx.  Any thoughts?

---

### Post by nothingspecial on 2010-01-20
Use adduser

```
sudo adduser bob
```

---

### Post by chupalo on 2010-01-20
Okay that worked, does anyone know what the difference is then between useradd and adduser, and why it would not create a folder in /home?

Thanks for your help.

FJ

---

### Post by lordjubblydave on 2010-01-20
Sorry for gatecrashing your topic.
But I'm in the process of adding a new user myself.
The thing is when I attempt to do it using the GUI all is fine except that I can not create a password of my choice.
I am being forced to use one with "a mixture of upper case and lower case letters and numbers"
I don't want to do this I want to pick my own password, it was not a problem on installation for the main account.
I don't understand why it is being picky with a 2nd user account. Is there a way around this ?

---

### Post by nothingspecial on 2010-01-20
Yes, using adduser.

---

