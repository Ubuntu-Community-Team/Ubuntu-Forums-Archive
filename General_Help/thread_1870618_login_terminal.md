---
title: "login terminal"
date: 2011-10-27
forum: General Help
---

### Post by orrymr on 2011-10-27
Hi all

I was just wondering about the login terminal (when I hit ctrl-alt-F(1->6)). I read somewhere that for login shells, .bash_profile gets executed, and for non-login .bashrc does. My first question is regarding the login shell. In my home directory I have no .bash_profile, so what gets executed when I log in? Where do those greeting messages come from?
Secondly, my $ENV variable doesn't seem to exist. I thought this was where the path to my environment initialization file (ie .bashrc) was kept?

---

### Post by cryptotheslow on 2011-10-27
Once logged into one of those tty's (terminals).

Type:
```
ls -al
```

The files starting with . are hidden unless you use the a flag to show "all" files.

Sorry if you already knew that - but it is the simplest thing not to know :D

---

### Post by dave01945 on 2011-10-27
the file .profile in your home gets run when you log in and .bashrc runs when you open a terminal

---

### Post by orrymr on 2011-10-27
I tried the following:
```

orrymr@orrymr-desktop:~$ ls -a | grep .bash
.bash_history
.bash_logout
.bashrc

```No .bash_profile/.bash_login :confused:

Edit: ooooh, .profile exists, and in the comments it says:
```

# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.

```
Still unsure about the ENV variable though

---

