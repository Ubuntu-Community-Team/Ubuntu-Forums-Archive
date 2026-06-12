---
title: "How to go for ROOT directory"
date: 2010-07-12
forum: General Help
---

### Post by karumudi7 on 2010-07-12
hi may be a silly question, but I dont know this.

I installed Ubuntu by Selecting "Install inside windows" options.

Now by default when I login, and goto Terminal, it will be:

nani@ubuntu:~$

I want to go to Roor directory. What is the command for that?

---

### Post by QLee on 2010-07-12
> **karumudi7 said:**
> hi may be a silly question, but I dont know this.

I installed Ubuntu by Selecting "Install inside windows" options.

Now by default when I login, and goto Terminal, it will be:

nani@ubuntu:~$

I want to go to Roor directory. What is the command for that?

enter the command, CD /, into the terminal.

[Edit] Sorry, I wasn't paying attention, those aren't supposed to be capitols, cd /, is the command

---

### Post by WorMzy on 2010-07-12
That should be a lowercase 'cd', but yes, / is the root directory. If you're used to Windows, then / is the equivalent of "C:\".

---

### Post by karumudi7 on 2010-07-12
Thanx,
I ran cd /  in terminal

Now it changed to nani@ubuntu:~$ 

It is Root ? Ok?

nani@ubuntu:~$ is Home
nani@ubuntu:/$ is Root

Is it correct..?

---

### Post by QLee on 2010-07-12
Ya WorMzy, normally I proof read after posting, but this time I was doing something else and by the time I got back to edit, you had already made the correction. Good, you probably saved the OP some confusion.

---

### Post by QLee on 2010-07-12
> **karumudi7 said:**
> Thanx,
I ran cd /  in terminal

Now it changed to nani@ubuntu:~$ 

It is Root ? Ok?

nani@ubuntu:~$ is Home
nani@ubuntu:/$ is Root

Is it correct..?

I don't really understand your question as you have written it but your prompt should be nani@ubuntu:/$, if you cd (change directory) from your home folder to /, the root folder.

---

### Post by WorMzy on 2010-07-12
> **karumudi7 said:**
> Thanx,
I ran cd /  in terminal

Now it changed to nani@ubuntu:~$ 

It is Root ? Ok?

nani@ubuntu:~$ is Home
nani@ubuntu:/$ is Root

Is it correct..?

I think you miswrote the first part of your message, cd / should give you "nani@ubuntu:/$", not "nani@ubuntu:~$", but yes, / is root, ~ is home.

---

### Post by karumudi7 on 2010-07-12
Guys a Small Mistake,
Now I was writing Clearly:

nani@ubuntu:~$  is Home
nani@ubuntu:/$  is Root

Is it Right now? ;)

---

### Post by karumudi7 on 2010-07-12
I was trying to add a Group bharath

Got the Error:

nani@ubuntu:/$ groupadd bharath
groupadd: cannot lock /etc/group; try again later.


How to solve?

---

### Post by audiomick on 2010-07-12
According to the previous posts, that is right.

If you do
```
ls
```
at the prompt, you will get a list of the files and directories where you are. That should show you where you are for sure, i.e. if you see directories like "boot", "dev" and so on, you are in the root directory. In /home, you will see, for instance, your personal folder, and in that, your files.

---

### Post by QLee on 2010-07-12
> **karumudi7 said:**
> I was trying to add a Group bharath

Got the Error:

nani@ubuntu:/$ groupadd bharath
groupadd: cannot lock /etc/group; try again later.


How to solve?

Aha! I think I understand you now, you don't want to get to the root folder, you want to do a command as root. In order to do that put, sudo, in front (prepend) of the command.

Maybe you want to use sudo groupadd. (that sudo lets you run the command as "root" (superuser).

---

