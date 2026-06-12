---
title: "Is there a line break command for terminal?"
date: 2006-03-18
forum: General Help
---

### Post by mandrakethepenguin on 2006-03-18
Hi!

     I'm trying to set up a command for my session to autostart my LAMPP server in my ubuntu session.  My command is: gnome-terminal -x sudo /opt/lampp/lampp start
I want to bypass entering the password when the terminal comes up. I know that this is a security risk, but my workstation is locked after this happens and no one else in my family knows how to operate linux.  Is there a command that indicates a line break and it would type my password?  Ive already tried: gnome-terminal -x sudo /opt/lampp/lampp start && echo (my password).


Any Help is apreciated

---

### Post by Ramses de Norre on 2006-03-18
I'm not that familiar with init scripts, but can't you change the permissions on it so you can execute it as regular user?
```
sudo chown your_username /opt/lampp/lampp
```

---

### Post by aysiu on 2006-03-18
Go to Applications > Accessories > Terminal and type ```
sudo nano /etc/sudoers
``` Some people say "use visudo," but I don't know how to "use visudo." In that file add a new line ```
mandrakethepenguin ALL = NOPASSWD: /opt/lampp/lampp start
``` Then save (control-x), confirm (y), and exit (Enter).

Then ```
sudo gedit /usr/local/bin/lampstart.sh
``` and paste in ```
#!/bin/sh
gnome-terminal -x sudo /opt/lampp/lampp start
``` Save and exit then ```
sudo chmod +x /usr/local/bin/lampstart.sh
```

Finally, go to System > Preferences > Sessions and add the command /usr/local/bin/lampstart.sh to the startup programs list.

---

### Post by jerrykenny on 2006-03-18
alternately put a launcher on every users toolbar, with the command

gksudo /opt/lampp/lampp

Then they''ll all be able to start lamp (after verifying with their own password) and maybe slightly less of a security risk ?

---

### Post by kabus on 2006-03-18
You can do what you want like this :

```
echo "password" | sudo -S *command*
```

Aysiu's suggestion is probably the better solution, though.

---

### Post by mandrakethepenguin on 2006-03-18
[COLOR=black]Wow!

Thanks for the help everybody!  [/COLOR]aysiu's method works.

---

### Post by aysiu on 2006-03-18
[QUOTE=mandrakethepenguin][COLOR=black]Wow!

Thanks for the help everybody!  [/COLOR]aysiu's method works.[/QUOTE] Phew! I'm glad I didn't type that all out for nothing. That's great.

---

### Post by DoktorSeven on 2006-03-19
[QUOTE=aysiu]Go to Applications > Accessories > Terminal and type ```
sudo nano /etc/sudoers
``` Some people say "use visudo," but I don't know how to "use visudo." [/QUOTE]

For reference:

```
EDITOR=gedit sudo visudo
```

will let you edit sudoers with gedit.  Replace gedit with any other editor to use it instead.

---

### Post by aysiu on 2006-03-19
[QUOTE=DoktorSeven]For reference:

```
EDITOR=gedit sudo visudo
```

will let you edit sudoers with gedit.  Replace gedit with any other editor to use it instead.[/QUOTE] So if I like Nano, I would do ```
EDITOR=nano sudo visudo
```? Why have I never seen anyone explain that? Every time people say to edit the sudoers file all they say is, "Just use visudo to edit your /etc/sudoers file."

---

### Post by DoktorSeven on 2006-03-19
Because no one actually likes to explain things :).  **man visudo** also gives you some information, as it does with virtually every other command (**man *commandname*** is your  best friend in Linux.)

Ideally, you can set your EDITOR command by adding the following line in ~/.bashrc at the end:

```

export EDITOR=nano

```

(Of course, replace EDITOR with your favorite editor.  Mine's vim. :) )  Then (you'll have to start a new terminal to make it take effect) you can just do a **sudo visudo** and be done with it.

---

### Post by aysiu on 2006-03-19
Thanks for the explanation. I tried doing *man visudo*, but those man pages never make any sense to me.

---

### Post by jerrykenny on 2006-03-19
Reckon its just cos if you actually leave a syntax error in the /etc/sudoers file, then sudo will be broken . . . . 

and vi has the sense to check your finished edited file for syntax errors before it commits the changes. . . . though I agree that nano is far more convenient

sudo nano /etc/sudoers

---

