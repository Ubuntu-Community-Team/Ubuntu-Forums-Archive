---
title: "Start up process"
date: 2011-04-19
forum: General Help
---

### Post by conradin on 2011-04-19
Hi all!
I want to start a process (boinc manager) on boot, without logging in. 
I have multiple users, and dont want anyone specific auto-logign in, rather 
I want the user select program (gdm) to display the users, and not log me or anyone else in.

the current set up, I login, the boinc mgr starts, and then I cant log out or it terminates. I want the boinc program to run at night, and i dont want to be logged in for that to have to work. 

What should I do?

---

### Post by sanguinoso on 2011-04-19
If you put the startup command in /etc/rc.local it will start on boot. You could also add an init script. Instructions here:

[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

---

### Post by conradin on 2011-04-19
Cool, Ill check it out in a bit. ( cant reboot just now)

---

### Post by conradin on 2011-04-19
Ah, editing the /etc/rc.local file worked exactly as I wanted it to!
My profuse and utter thanks sanguinoso! :)

---

