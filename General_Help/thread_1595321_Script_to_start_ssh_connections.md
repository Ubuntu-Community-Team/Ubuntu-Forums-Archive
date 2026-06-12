---
title: "Script to start ssh connections"
date: 2010-10-13
forum: General Help
---

### Post by andypi on 2010-10-13
I have recently installed MATLAB on my computer, which I have access to licenses from the engineering department license server at my university.

This means, that in order to run MATLAB I have to open two SSH connections first:

ssh -q -n -x -L 1711:matlab-lmserv.eng.myuni.ac.uk:1711 [email]usrname@gate.eng.myuni.ac.uk[/email]

ssh -q -n -x -L 20001:matlab-lmserv.eng.myuni.ac.uk:20001 [email]usrname@gate.eng.myuni.ac.uk[/email]

Each of these commands will prompt me for my department password.

What I'd like to do is have a script which opens both these connections and then starts MATLAB, without any other input. How would that be done?

---

### Post by SlugSlug on 2010-10-13
firstly you'd want to setup SSH keys so you don't need a password 
[http://pkeck.myweb.uga.edu/ssh/](http://pkeck.myweb.uga.edu/ssh/)

and then some starup script to launch the above commands

---

