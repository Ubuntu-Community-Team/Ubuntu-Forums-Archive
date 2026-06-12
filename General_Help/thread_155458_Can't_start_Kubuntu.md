---
title: "Can't start Kubuntu"
date: 2006-04-05
forum: General Help
---

### Post by wcks48 on 2006-04-05
Oh my  godness. after i log in with console with my own user name and password, i changed to root by "sudo -s" then successfully go into the kubuntu desktop by root and delete one lin eof the sources.list to enable my apt-get runs well. ok, everthings fine, as i going back to start up with my own user name and password, the system couldn't go anymore as poping the msg: No write access to /home/user/ICEauthority. 

so, what had happen actually. anybody can tell me bout this.. quite frustated with the kubuntu for days...

---

### Post by gingermark on 2006-04-05
You should just use sudo for terminal commands and kdesu for graphical apps - then you should avoid this problem.

In the failsafe terminal do the following:

sudo chown username ~/.ICEauthority
sudo chmod 777 ./.ICEauthority

should work.

EDIT: And, more generally, keep these commands handy if any ownership issues in your home directory occur again:

sudo chown -R username : username /home/username
sudo chmod -R u+w /home/username

Obviously, in all these cases, username is your username :)

---

### Post by wcks48 on 2006-04-05
i can only sign into the console with my user name, and password. fail to get into desktop. 

but if i use "sudo startx" no problem for me. but of coz, all of the environment inside just not mine but as for root access. and i found all my login files (inside my home folder), changed to the owner as root. i know it should be belongs to "username". and i couldn't change it any. 
is the command u gave can fix thiese.?

---

### Post by gingermark on 2006-04-05
[QUOTE=wcks48]i can only sign into the console with my user name, and password. fail to get into desktop. 

but if i use "sudo startx" no problem for me. but of coz, all of the environment inside just not mine but as for root access. and i found all my login files (inside my home folder), changed to the owner as root. i know it should be belongs to "username". and i couldn't change it any. 
is the command u gave can fix thiese.?[/QUOTE]
The latter commands I gave will change the ownership and modification rights back to your normal username. (The first one just affects .ICEauthority). So yes, they should.

---

### Post by wcks48 on 2006-04-05
still some question bout my firefox. i log in as root just to fix my firefox. after i confirm can open in root mode, sign in problem came. okay, now can use with my own id. but firefox can;t load still. why?
i had check the apt-get, my firefox updated and installed.

---

### Post by gingermark on 2006-04-05
Not sure.

Run Konsole and run Firefox from there (type 'firefox') and post the output (maybe in a new thread) and someone should be able to help.

If you ever need to run Firefox with root priviledges (so as to install some extentions for example) use the command 'kdesu firefox'.

---

