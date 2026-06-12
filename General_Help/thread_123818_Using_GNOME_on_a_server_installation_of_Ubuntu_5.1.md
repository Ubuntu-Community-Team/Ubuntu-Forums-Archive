---
title: "Using GNOME on a server installation of Ubuntu 5.10"
date: 2006-01-31
forum: General Help
---

### Post by Trizik on 2006-01-31
How do I use GNOME on a server installation of Ubuntu 5.10?

---

### Post by RAOF on 2006-01-31
Run "sudo aptitude install ubuntu-desktop".  This will install Gnome, X and friends.  Then run "sudo /etc/init.d/gdm restart" to log in to the GUI.

---

### Post by Trizik on 2006-01-31
thanks, will this auto load the GUI following reboots?

---

### Post by midwinter on 2006-01-31
doesn't that install all the stuff (xchat, serpentine) you probably wouldn't want on a server install? (else, why bother..)

---

### Post by morphodone on 2006-01-31
[QUOTE=Trizik]thanks, will this auto load the GUI following reboots?[/QUOTE]

yep, you should be all set

---

### Post by Trizik on 2006-01-31
you're right, i don't want a bunch of extras... i just want a server install with the GNOME GUI...

should i do what RAOF said?

---

### Post by RAOF on 2006-01-31
[QUOTE=Trizik]you're right, i don't want a bunch of extras... i just want a server install with the GNOME GUI...

should i do what RAOF said?[/QUOTE]
No, that will install all the extra stuff.  You'd probably want to look at "aptitude search gnome" and "aptitude search xserver".  See what packages there are.

---

### Post by morphodone on 2006-01-31
[QUOTE=Trizik]you're right, i don't want a bunch of extras... i just want a server install with the GNOME GUI...

should i do what RAOF said?[/QUOTE]

gnome itself comes with a lot of extra packages...
you might consider using another window manager like fluxbox, twm, etc

---

### Post by Trizik on 2006-01-31
OK, i thought GNOME was just a Windows GUI, i didn't realize it came with a bunch of extras. i don't want GNOME then.

thanks, i will take a look at fluxbox and twm. any other "bare" GUIs you would recommend?

---

### Post by era86 on 2006-01-31
[QUOTE=Trizik]OK, i thought GNOME was just a Windows GUI, i didn't realize it came with a bunch of extras. i don't want GNOME then.

thanks, i will take a look at fluxbox and twm. any other "bare" GUIs you would recommend?[/QUOTE]

I enjoy using openbox. I am about to do the openbox thing with my Gentoo box. BTW, would anyone know how to do this? Is it the same as it would be in Ubuntu?

Anyways, openbox (fluxbox or blackbox ) would be the choice for something bare and without extras.

-ERA

---

