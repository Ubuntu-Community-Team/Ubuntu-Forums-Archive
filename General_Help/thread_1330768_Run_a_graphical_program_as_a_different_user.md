---
title: "Run a graphical program as a different user"
date: 2009-11-18
forum: General Help
---

### Post by LordKelvan on 2009-11-18
Hi:

I'm trying to run gedit as a different user in order to create some configuration files.  I used the following command:

```

sudo -u www-data gedit syntax.php

```

but I get the following error message:

```

No protocol specified

(gedit:5152): Gtk-WARNING **: cannot open display: :0.0

```

I can run terminal programs just fine using the above command.  The value of $DISPLAY is ":0.0", which I believe to be correct.  Issuing the command "xhost +" (to turn off authentication) also didn't help.

Cheers,
LK

---

### Post by roboguy on 2009-11-18
Try using gksudo, it may set up the display variables for the application you're trying to start.

---

### Post by ibuclaw on 2009-11-18
[s]EDIT[/s]
```

sudo -u www-data mkdir -p /var/www/.gconf/apps/gedit-2
sudo -u www-data mkdir -p /var/www/.gnome2/gedit
sudo -u www-data mkdir -p /var/www/.gconfd

```
Perhaps making the directories for gedit to run?

Regards
Iain

---

### Post by LordKelvan on 2009-11-18
@tinivole
Entering "export DISPLAY=:0.0" doesn't change anything.

@roboguy
Running with gksudo gives me this error:

```

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-ifuF6mqRDM: Connection refused)

```

@tinivole
Nope, that doesn't work either.

Any other ideas?

Cheers,
LK

---

### Post by LordKelvan on 2009-11-19
Bump.  Surely I can't be the only one who needs to run a graphical program as another user?

---

### Post by LordKelvan on 2010-02-07
Bump

---

### Post by falconindy on 2010-02-07
"gksu -u <user> <program>" is the correct way to do this. You can leave out the '-u <user>' if you're just trying to run as root.

---

### Post by fyo on 2010-12-16
Late to the party, but search results turn up this thread and I wasn't able to get any of the suggestions above to work. I've used xauth before, but the following looks like the best way:

In a terminal do:

```
$ sudo apt-get install sux
$ sux theuseryouwanttorunas

```

You will then be prompted for the password of the other user. Once you type that in, you'll have an xterm with the other user logged in. sux transfers your X credentials, so everything should work as expected (did for me). Just run your app.

---

