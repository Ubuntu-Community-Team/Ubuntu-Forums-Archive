---
title: "installing Euphoria"
date: 2006-03-27
forum: General Help
---

### Post by neoginn on 2006-03-27
so i want to try out this new programming language. I only hear good things :) about it so i am trying to install it, so i un tar it and nothing:-k ... i dont know what the heck to do next](*,) . this is the link for the download. [http://www.rapideuphoria.com/v20.htm](http://www.rapideuphoria.com/v20.htm)

any help would be great otherwise i may have to use windows:cry: :cry: ...please help this ubuntu user!

---

### Post by nanotube on 2006-03-28
from the website you linked to:

> On Linux type:
tar -xvz -f euphor25.tar

A euphoria subdirectory will be created in the current directory. See readme.doc and install.doc located inside the euphoria subdirectory.

so... read the readme.doc, and the install.doc. :)

---

### Post by uli on 2006-08-26
I have installed Euphoria 2.5 (a free download from [www.rapideuphoria.com](www.rapideuphoria.com)) and I have put the instructions as suggested in the intall.htm file to the .bash_profile file in my /home dir. as well as in the /root dir (I created the .bash_profile file there). I also put it in the /etc profile file - to no avail. Euphoria will not perform as I am used to from the Red Hat Linux (shrike) on my desktop. 
When I try to run a Euphoria file on the terminal, I get the message:"Error opening terminal:xterm". When I run the same command in the xterminal, I get the same message. When I drop as su to a lower runlevel,I get the message: "bash:exu:command not found".

Is there a "true" Linux terminal that I can download into Ubuntu?

P.S.I am running Ubuntu 6.06 on an Averatec 3200 laptop.

I hope that someone can help.
Thanks!
Uli

---

### Post by uli on 2006-08-26
Alexander Toressen (EU-Forum) pointed out to me that in addition to following the instructiions in the "install.htm" file it might be necessary to give the
command >export TERM=ansi< in some linux distributions and Ubunto is one of them.
In addition, Robert Craig, the author of EUPHORIA points out that this command (export TERM=ansi) should be added in the .bashrc file of the home directory.
Hope that helps!
Uli

---

