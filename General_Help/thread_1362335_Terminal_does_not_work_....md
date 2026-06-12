---
title: "Terminal does not work ..."
date: 2009-12-23
forum: General Help
---

### Post by alexplAnTe on 2009-12-23
Hi !

I have a big problem here! When I click on terminal, it says :

X: user not authorized to run the X server, aborting...

I think I know why it does that, but I just don't know how to resolve it and I need that freeking black little window.

I change something in /etc/passwd because I wanted that startx start automaticely after I log in so I replace 
"user bla bla bla ... /bin/sh "by "/usr/bin/startx" .

Oh almost forgot ! I am using Xubuntu 9.10 :P

---

### Post by lavinog on 2009-12-23
[quote=alexplAnTe]I change something in /etc/passwd because I wanted that startx start automaticely after I log in so I replace
"user bla bla bla ... /bin/sh "by "/usr/bin/startx" .[/quote]
It looks like you already know what you need to do to fix it.

You might need to boot into recovery mode to fix it though.

---

### Post by JoelOl75 on 2009-12-23
Umm editing the passwd file to change your default shell to startx doesn't seem....   right at all.  X should start automatically after log in anyway unless something else is broken as well..

I thought the 'correct' place to start programs would be the /home/user/.bashrc file

---

### Post by renkinjutsu on 2009-12-23
> **JoelOl75 said:**
> Umm editing the passwd file to change your default shell to startx doesn't seem....   right at all.  X should start automatically after log in anyway unless something else is broken as well..

I thought the 'correct' place to start programs would be the /home/user/.bashrc file

He could have a minimal install, like me.

If you put it in .bashrc, it'll try to start X everytime he opens up a terminal or log into one of the consoles

you can try putting a script with "/usr/bin/startx" into the /etc/profile.d


edit: and to fix your current problem, try pressing ALT+F2 and put in ```
gnome-terminal -e /bin/bash
```

---

### Post by alexplAnTe on 2009-12-23
And what would be the script to startx ?

(Yes I have a minimal installation :P)
I am not using a login manger like gdm, xdm, slim ... so that's why I want to startx just after i log in in the console login. 

Thank :P

---

### Post by alexplAnTe on 2009-12-23
Ohh sorry i got it :P

You just have to write "/usr/bin/startx" in a new .sh script and place it in /etc/profile.d to startx just after you log in :P. 

Thank :D

---

