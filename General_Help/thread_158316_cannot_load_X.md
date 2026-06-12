---
title: "cannot load X"
date: 2006-04-10
forum: General Help
---

### Post by groggyboy on 2006-04-10
the title says it all.  when i boot up, i get this error in GNOME before the splash screen even appears:> Your $HOME/.dmrc file has incorrect permissions and is being ignored.  This prevents the default session and language from being saved.  File could be owned by user and 644 permissions.
From this screen, pressing OK does nothing but give me the gnome splash screen which hangs loading metacity.  i can press ctrl-alt-backspace, but instead of taking me to gdm, i get a console.  from the console, i can try typing "startx" but the same thing happens.  i have KDE installed on my machine as well, but i can't try loading it because i can't get to gdm/kdm!

anyone know why it might be doing this?

cheers, groggyboy

---

### Post by taurus on 2006-04-10
Hold down <Ctrl><Alt>F2 at the same time and that would put you to a console.  Log in with your username and password.  At the prompt, do
```

sudo chown groggyboy /home/groggyboy/.dmrc
sudo chmod 644 /home/groppyboy/.dmrc
(assuming that groggyboy is your userID!  If not, replace it with the right one for the two lines above...)

```
Now, log out and <Ctrl><Alt>F7 to get back to GUI login screen.  See if you can log in to Gnome now...

---

### Post by groggyboy on 2006-04-10
hmmm, still get the error message.  i've messing around with my /home directory lately, i've been trying to set it up on its own partiton.  i've tried all kinds of stuff.  its possible that in the process of all this, i've done something to corrupt my /home directory.

---

### Post by taurus on 2006-04-10
Could be!  What is the output of this command from a terminal anyway?
```

ls -la /home

```

---

### Post by groggyboy on 2006-04-11
here it is:> total 12
drwxr-xr-x   3 root      root      4096 2006-04-09 22:28 .
drwxr-xr-x  23 root      root      4096 2006-04-09 21:41 ..
drwxrwxr-x  91 groggyboy groggyboy 4096 2006-04-10 23:04 groggyboy


p.s. - the problem with gnome hanging while loading metacity is unrelated - i just have to wait a long time.  kde and failsafe gnome work, but i get the same error message.  and i can't set kde as default because of this stupid permissions error!

---

### Post by taurus on 2006-04-11
How about the output of
```

ls -la ~
(remove whatever you don't want the public to see...)

```

---

### Post by nazish on 2006-04-11
did u try to change the entries in the /etc/fstab file

if so then modify it to the previous state 
                         or
probably you are trying to mount your home folder onto a partition onto which only the root has R/W access, try changing 
the permissions for that partition.

---

### Post by groggyboy on 2006-04-11
here it is.  its really long (EDIT-removed all but the pertinent file):> total 696
-rw-r--r--   1 groggyboy groggyboy    58 2006-04-10 14:42 .dmrc

---

### Post by groggyboy on 2006-04-15
solved it - thought i'd post my solution in case anyone else has the same problem.

it was as simple as deleting the file in question:> sudo rm ~/.dmrc

cheers!
groggyboy

p.s. - this was my fiftieth post :cool:

---

### Post by LordMerlin on 2006-04-18
This seems to be a common problem. Does anyone know what creates this file, and why? Why does it cause problems?

---

