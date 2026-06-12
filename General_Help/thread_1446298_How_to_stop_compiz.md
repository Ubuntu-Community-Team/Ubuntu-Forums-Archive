---
title: "How to stop compiz"
date: 2010-04-03
forum: General Help
---

### Post by satimis on 2010-04-03
Hi folks,


Ubuntu 9.10 64bit

Compiz is installed and running on this OS

$ apt-cache policy compiz```

compiz:
  Installed: 1:0.8.4-0ubuntu2
  Candidate: 1:0.8.4-0ubuntu2
  Version table:
 *** 1:0.8.4-0ubuntu2 0
        500 http://hk.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```


$ which compiz```

/usr/bin/compiz

```


How to disable compiz temporarily and re-enable it?

I can't find
System>Preferences>Compizconfig Settings Manager

TIA


B.R.
satimis

---

### Post by 3rdalbum on 2010-04-03
System, Preferences, appearance. Go to the Visual Effects tab and set it to 'None'.

Or hit Alt-F2 and type 'metacity --replace'

---

### Post by dacoolio on 2010-04-03
To switch to metacity:

$ metacity --replace &

To switch to compiz:

$ compiz --replace &


Hope that was what you were looking for

---

### Post by lidex on 2010-04-04
> I can't find
System>Preferences>Compizconfig Settings Manager

Use this command:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by satimis on 2010-04-04
> **dacoolio said:**
> To switch to metacity:

$ metacity --replace &

To switch to compiz:

$ compiz --replace &


Hope that was what you were looking for

Hi dacoolio,

Thanks for your advice.  If I need turning off both which command shall I run?

B.R.
satimis

---

### Post by mikewhatever on 2010-04-04
If you don't need both, which means no gui, stopping xserver is the way.

---

### Post by satimis on 2010-04-04
> **lidex said:**
> Use this command:
```
sudo apt-get install compizconfig-settings-manager
```
Hi lidex,

Thanks for your advice.

To stop compiz whether uncheck;
General - commands
General - Gnome compatibility

I'm running Gnome here.


B.R.
satimis

---

### Post by satimis on 2010-04-05
> **mikewhatever said:**
> If you don't need both, which means no gui, stopping xserver is the way.
Hi,

Thanks for your advice

Whether press [Ctrl]+[Alt]+5

OR

[Ctrl]+[Alt]+2 (single user mode) ?


satimis

---

### Post by 3rdalbum on 2010-04-05
> **satimis said:**
> Hi dacoolio,

Thanks for your advice.  If I need turning off both which command shall I run?

B.R.
satimis

You need a window manager running at all times. Metacity is a plain-old basic window manager, Compiz is a window manager with visual effects. If you didn't have a window manager running, you wouldn't be able to move, resize, minimise, maximise, close windows, use workspaces etc.

If you wanted to get back to the command-line at the heart of Linux, then first you'd save all open documents and quit all applications, and you'd type:

```
sudo service gdm stop
```

To start the GUI again, type:

```
sudo service gdm start
```

---

