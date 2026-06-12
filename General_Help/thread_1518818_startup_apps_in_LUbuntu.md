---
title: "startup apps in LUbuntu?"
date: 2010-06-27
forum: General Help
---

### Post by JC Cheloven on 2010-06-27
Hi, trying out LUbuntu in an old laptop. Really nice. But I'm hitting a wall with this:

I want a program (conky) to be started after the window manager (OpenBox) is loaded. This is usually accomplished in openbox environments by creating the file [COLOR="Blue"]~/.config/openbox/autostart.sh[/COLOR] , where you include lines for programs you want to be run at startup.

Problem is: this file is only read when openbox is invoked by the "[COLOR="Blue"]openbox-session[/COLOR]" command. It is not read if openbox is launched by the "[COLOR="Blue"]openbox[/COLOR]" command on its own.

In the LUbuntu startup window, there are options to choose the "desktop" you want. The default is (obviously) "Lubuntu", which seems to call "openbox" on its own :( . If I choose "Openbox Session", then my autostart.sh script is read as expected (seems that openbox-session is invoked), but all my panel, menu, etc don't appear, so this is not an option.

So: how to launch programs at startup in LUbuntu?

---

### Post by JC Cheloven on 2010-06-28
Bump.

---

### Post by kerry_s on 2010-06-28
/etc/xdg/lxsession/Lubuntu/autostart

---

### Post by JC Cheloven on 2010-06-28
> **kerry_s said:**
> /etc/xdg/lxsession/Lubuntu/autostart

Thanks, that was it!
Why everyone changes the placement of files when ellaborating whatever thing? (openbox has a place for that, lxde a different one, now lubuntu still a different one... it gets on my nerves!)

Marking as solved.

---

### Post by kerry_s on 2010-06-29
> **JC Cheloven said:**
> Thanks, that was it!
Why everyone changes the placement of files when ellaborating whatever thing? (openbox has a place for that, lxde a different one, now lubuntu still a different one... it gets on my nerves!)

Marking as solved.

:lolflag:

well now you know where it is, you can create a startup script anywhere you want & just run that.
example:
@/path/to/autostart.sh

just remember your startup script needs to be standard bash.
example:
#!/bin/bash
command1 &
command2 &

---

### Post by JC Cheloven on 2010-06-29
Thanks, Kerry, much appreciated.

And sorry, more calmed now :lolflag:
JC
_________

---

### Post by kerry_s on 2010-06-29
no problem.
if you stick with it you'll get use to it. 
you can setup some scripts to make things easier. 
for example:

i have a script for the editor that checks if the file is owned by root & if it is opens it as root, so i can easily edit any files.

first add the editor to sudoers:
sudo visudo
```
%admin ALL=NOPASSWD: /usr/bin/pcmanfm,/usr/bin/leafpad
```

that will allow you to run those programs with out a password.

the script goes in /usr/local/bin, it replaces the leafpad command, so it needs to be named "leafpad". don't forget to right click-> properties-> permissions & check the "make the file executable.

```
#!/bin/bash

test=`stat -c %U "$@"`
if [ "$test" == "root" ]; then
	gksudo /usr/bin/leafpad "$@"
else
	/usr/bin/leafpad "$@"
fi
exit 0

```

another script i made, you'll need to install zenity.

```
#!/bin/bash
name=$(zenity --entry)
lxshortcut -o ~/.local/share/applications/$name.desktop &
exit 0

```

this 1 i use to create launchers, you can click on it after you make it to make a launcher for it. just put the name for the command.

i got mine setup netbook style on this old laptop. 
vaio 450mhz 256mb ram

pics:

---

### Post by JC Cheloven on 2010-06-30
Sweet, thanks. May I also offer something potentially useful:

It seems to be a little bug in the ~/.config/openbox/lubuntu-rc.xml file.
The key bind A-Print should execute ```
scrot -u
```instead of what it comes with. 
This makes the Alt-PrintScreen keying to work as expected.

BTW, it wasn't enough the usual rc.xml file, either... ;-)
JC

---

### Post by kerry_s on 2010-06-30
> **JC Cheloven said:**
> Sweet, thanks. May I also offer something potentially useful:

It seems to be a little bug in the ~/.config/openbox/lubuntu-rc.xml file.
The key bind A-Print should execute ```
scrot -u
```instead of what it comes with. 
This makes the Alt-PrintScreen keying to work as expected.

BTW, it wasn't enough the usual rc.xml file, either... ;-)
JC

yeah, i go in there a change things to.
theres a extra section for the print command that i remove, the command i use is "scrot %T.png" so it just uses the time.

i also change the run command to "grun"(needs to be installed) as i don't like it being tied to the panel, i've had to many times the panel has gone wonky.

i also set up programs to be maximized with no decor.

lubuntu is easy enough to learn, you can also apply the many openbox tricks out there. anyways have fun, it's all that matters.

---

