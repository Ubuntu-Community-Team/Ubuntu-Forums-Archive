---
title: "autostart script, deleting files. doesn't work."
date: 2009-08-12
forum: General Help
---

### Post by monkman on 2009-08-12
[http://a.imagehost.org/view/0824/RM](http://a.imagehost.org/view/0824/RM)

[http://a.imagehost.org/view/0009/FCL](http://a.imagehost.org/view/0009/FCL)

what is wrong here?

the rm.desktop file is located in ~/.config/autostart

thx!

---

### Post by DaithiF on 2009-08-12
Hi,
'~' gets expanded to your home directory by your shell.  When rm is run outside of a shell that expansion won't happen, so rm will be trying to remove a non-existing path.

You can either specify your home directory fully (/home/you/.macromedia/etc), or you could put your rm command into a wrapper script which gets run by the shell:
cleanup.sh
```
#!/bin/bash
rm -rf ~/.macromedia/etc...

```
and execute cleanup.sh in your .desktop file instead.

cheers
D

---

### Post by monkman on 2009-08-12
expanding the path shows no effekt. strange... using it in the shell, it works. 

the second thing with the wrapper script i don't understand. where can i find a nice newbee howto for start scripts?

i tried : /home/me/.config/autostart/cleanup.sh after chmod a+x cleanup.sh 

(in the "startprogramms" thing in the system menü, sorry i'm using the german gui, don't know the exact english matches)

but this didn't work either

thx!

---

### Post by DaithiF on 2009-08-12
Hi, expanding the path should indeed work, and does for me.  Can you post the contents of your rm.desktop file here please?
thanks

---

### Post by monkman on 2009-08-12
.config/autostart/rm.desktop 

```
[Desktop Entry]
Type=Application
Name=Flash Cookies löschen
Exec=/home/monkman/.config/autostart/cleanup.sh
Icon=system-run
Comment=
Name[de_DE]=Flash Cookies löschen
Comment[de_DE]=
X-GNOME-Autostart-enabled=true
```

---

### Post by DaithiF on 2009-08-12
actually i meant the version where you try the rm command directly, rather than the wrapper script.  i just wanted to check exactly what you were running ... but looking back at your earlier screenshots I see the problem now ... again its due to shell expansion, (or the lack of) ... when you run
```
rm -rf /home/monkman/.macromedia/Flash_Player/*

```
in a shell, the shell expands the '*' into whatever files/dirs exist, and passes those explicitly to the rm command.  The rm command itself doesn't know how to expand wildcards.  And when you run this command outside a shell, the wildcard expansion doesn't happen and so rm doesn't have a valid list of files/dirs to operate on.

You can just delete the Flash_Player directory itself, so your Exec line becomes:
```
Exec=rm -rf /home/monkman/.macromedia/Flash_Player

```

cheers
D

---

### Post by monkman on 2009-08-12
thx!

putting this into the start script menü

```
rm -rf /home/monkman/.macromedia/Flash_Player
```

solved the problem...

---

### Post by czarbali on 2009-08-13
i have a script lets say "test.sh" 
[B]test.sh
#!/bin/bash
xxxx service start[/B]
and I have placed it inside the ~/.config/autostart/ directory but its nt working. Any Hints what I am missing....

---

### Post by DaithiF on 2009-08-13
Hi,
the ~/.config/autostart directory is for application launcher files (*.desktop) rather than actual scripts themselves.  Put the script somewhere else (e.g. often a bin directory below your home directory, but it doesn't really matter).  In the autostart directory you need a .desktop file similar to the examples you see there -- so easiest to copy on of those files, then edit it to change the Exec= line to run your script.

cheers
d

---

