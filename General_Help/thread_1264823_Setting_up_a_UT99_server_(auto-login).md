---
title: "Setting up a UT99 server (auto-login)"
date: 2009-09-12
forum: General Help
---

### Post by mrbiggbrain on 2009-09-12
So i'm setting up a UT99 dedicated server in my house, and i wanted to just have to turn on the system and have it boot with no need for my intervention, or even a monitor.

For me to pull this off i need to

A) Log in as a general user without entering a password
B) Run the server command after logging in (to start the server and web interface)

Can anyone help me set these two things up. im good with the shell, i just dont know the files to edit, and what to add.

---

### Post by P4man on 2009-09-12
a default ubuntu setup (with gnome or kde) wont boot all the way without a monitor.. It will throw an error message requiring intervention. So you're gonna have to use a server cd, or remove gnome (or at least remove gdm i think). google for "ubuntu headless" and you'll find plenty.

As for autostarting the app. Put it in autoexec.bat heh . j/k
Not too sure to be honest. Im sure someone will chime in.

---

### Post by mrbiggbrain on 2009-09-12
> **P4man said:**
> a default ubuntu setup (with gnome or kde) wont boot all the way without a monitor.. It will throw an error message requiring intervention. So you're gonna have to use a server cd, or remove gnome (or at least remove gdm i think). google for "ubuntu headless" and you'll find plenty.

As for autostarting the app. Put it in autoexec.bat heh . j/k
Not too sure to be honest. Im sure someone will chime in.

Im running off:

ubuntu-9.04 minimal, no desktop manager, just the basics. iv already got everything setup, and i also founf 

mingetty --autologin

[https://lists.ubuntu.com/archives/ubuntu-users/2009-May/182916.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-May/182916.html)

found it there, for autologon

and it works, now i just need to auto run the server command and ill be happy

---

### Post by P4man on 2009-09-12
have a look here:
[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

---

### Post by mrbiggbrain on 2009-09-12
i actualy got it to work using my .bashrc file, everything seems to be running well now, thanks

---

