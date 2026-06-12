---
title: "check the line for your account in /etc/passwd"
date: 2010-11-12
forum: General Help
---

### Post by Konbuntu on 2010-11-12
if you don't know which shell you are using , either check the line for your account in /etc/passwd

what is that suppose to mean? how do i check it? do i check it from the terminal?


thanks in advance

---

### Post by Dave_L on 2010-11-12
Use the following command in a terminal window: 

$ grep USER /etc/passwd

where USER is your username/loginname.

The output should look something like this:

USER:x:1000:100:USER,,,:/home/USER:/bin/bash

The "/bin/bash" at the end means my default shell is "bash".

This gives you the same information (I think):

$ echo $SHELL

---

### Post by matt_symes on 2010-11-12
Hi

BTW, if you want to change your shell, from a terminal, type

chsh

and type your new shell (after the passwd).

To see your shells type

cat /etc/shells

Kind regards

---

### Post by Konbuntu on 2010-11-12
it worked without the $ : grep konlah /etc/passwd

thanks! =)

---

