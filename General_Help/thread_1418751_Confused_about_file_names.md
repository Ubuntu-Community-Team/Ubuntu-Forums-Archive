---
title: "Confused about file names"
date: 2010-03-01
forum: General Help
---

### Post by dln9 on 2010-03-01
Ubuntu 9.10.  

Nautilus 2.28.1.  

Using Nautilus, if I navigate to /etc/share/app-install/desktop/ , I will find, for example, a file with the name of "Yate".  (This is some kind of VoIP program.)  

If I open a terminal, and at /etc/share/app-install/desktop/ I run the "ls" command, I will *NOT* find a file named "Yate"; instead, I will find a file named "yate-gtk2.desktop".  

I am confused.  What is the name of the file?  Why do the two methods tell me two different things?  How do I get Nautilus to display the *entire* name of the file?  

Thanks for clarifications.

---

### Post by geirha on 2010-03-01
Files with .desktop extension are menu entries/launchers, and nautilus will automatically read these files and show them with icon and name. So the name of the file is yate-gtk2.desktop, and if you open it in a text editor, you'll see the line: «Name=Yate» and many «Name[xy]=...»-lines, where xy are 2-3 letter language codes. If there is one for the language you are using, it will display that, if not, it will fall back to the generic Name=.

---

### Post by dln9 on 2010-03-01
Thanks geihra.  

Sorry - I still do not understand.  

"yate-gtk2.desktop" is the NAME of the file; and, 

"Yate" is the - what? - of the file?  

If "yate-gtk2.desktop" is the name of the file, then "Yate" cannot also be the name of the file.  But then I don't know what you call the label "Yate" - what is it, what does it do for the file, what is its function?  

More importantly, what is the reason for Nautilus behaving this way?  Why doesn't Nautilus just display "yate-gtk2.desktop", instead of "Yate"?  

Is this behavior unique to desktop configuration files, or might I stumble across this with other file types?  

Do all file managers act this way, or is this something peculiar about Nautilus?

---

### Post by lisati on 2010-03-01
I'm not sure but think the effect you are observing is roughly analogous to the desktop shortcuts in Windows.

---

### Post by geirha on 2010-03-01
Indeed, it's somewhat the equivalent of a shortcut in windows. And yes, they are special to nautilus, but as far as I know, there are no other filetypes that are special in that way. Which means any other filetype will be displayed with its actual filename.

```
$ cat /usr/share/app-install/desktop/yate-gtk2.desktop
[Desktop Entry]
X-AppInstall-Package=yate-gtk2
X-AppInstall-Popcon=13
X-AppInstall-Section=universe

Encoding=UTF-8
Name=Yate
GenericName=VoIP Phone
Comment=Place phone calls over the Internet
Exec=[COLOR="blue"]yate-gtk2[/COLOR]
TryExec=yate-gtk2
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;Network;GTK
X-Ubuntu-Gettext-Domain=app-install-data

```

It's a "shortcut" that will run the command [COLOR="Blue"]yate-gtk2[/COLOR] when you double-click it.

If you right click the desktop and choose Create launcher, you will create a desktop file like that.

---

