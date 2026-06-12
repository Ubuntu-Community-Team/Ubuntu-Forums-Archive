---
title: "is ther any way to have a startup folder that i can throw scripts in?"
date: 2009-08-07
forum: General Help
---

### Post by cosmoshell on 2009-08-07
is there any way to have a startup folder that i can throw scripts in? like there is in windows?

---

### Post by kerry_s on 2009-08-07
like what kind of scripts?
you can already add commands to the session using the gui, so i suppose you could put a command in there to start scripts in a folder, for example: ~/startup/*
then just create a folder named startup & put the scripts in.

if your talking scripts that need root access, best you use /etc/rc.local for those.

---

### Post by cosmoshell on 2009-08-07
k thanks

---

### Post by Simian Man on 2009-08-07
You can do the following:
[LIST=1]
[*]Make a directory, we'll call it ~/startup to put your scripts in
[*]Write a script to execute all of the scripts in this directory.  It should go somewhere in your $PATH and can consist of "source ~/startup/*
[*]Add the script you wrote in step 2 to your gnome session
[*]Add whatever you want to the startup directory
[/LIST]

I didn't test that, but it should work.

<edit>Weird, Kerry even used the same name as me...

---

### Post by llemm on 2009-08-07
you can throw it in the

~/.profile or sometimes ~./bashrc

HTH

---

### Post by rainwalker on 2009-08-07
Check out System > Preferences > Startup Applications

---

