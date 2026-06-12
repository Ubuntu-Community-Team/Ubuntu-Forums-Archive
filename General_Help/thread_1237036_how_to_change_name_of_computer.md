---
title: "how to change name of computer"
date: 2009-08-10
forum: General Help
---

### Post by breephd on 2009-08-10
hi everyone.  due to unforseen circumstances, i have to change the name of my pc to a different one.  how can i do it?  i went into user groups, and while i can add and change usernames... the basic name of the pc is still the same.  it must be the root name or something.  how to change it without reinstalling everything?

---

### Post by lykwydchykyn on 2009-08-10
You just need to edit the file /etc/hostname, but you need to do it with sudo, so try this:

gksudo gedit /etc/hostname

Then just put whatever you want in there and reboot.

---

### Post by jocampo on 2009-08-10
```
hostname NEW_NAME
```

On Ubuntu I think you can also edit /etc/hostname file and change it...

---

### Post by breephd on 2009-08-10
thanks. everyone. i made a mistake. and i need serious help. please help!
 
i was messing around with it, and i deleted the line that had the name of the pc. now, i can't log in at all. 
 
when it boots it says "your home directory is listed as '/home/admin' but it does nto appear to exist. do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session. 
 
then there are two buttons "no" and "yes"
 
if i select no, it takes me to a window and asks for another username and password. i did create two others, but i cant recall the passwords. 
 
 
if i select yes it has another message abotu ignoring soemthing. then it shows a blank screen.
 
Ps.s. : okay i got in using another screen name. wow thank goodness i created another one.... now what? this new user doesn't have the ability to access the user anmes and groups...

---

### Post by merlinus on 2009-08-11
Your problem is that you only changed the name in /etc/hostname and it also needed to be changed in /etc/hosts.

---

