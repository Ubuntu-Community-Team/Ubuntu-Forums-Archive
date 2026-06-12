---
title: "Ibus inactive with OpenOffice Word"
date: 2010-12-13
forum: General Help
---

### Post by thinhhoang on 2010-12-13
Hi there, I've just installed Kubuntu 10.10 a couple of days a go. I've installed IBUS-UNIKEY and it works perfectly with Kopete and other applications. But I can not "activate" Ibus when working with OpenOffice Word. Please help me out. Sorry about my English. Thanks a lot.
KDEIbus doesn't work with other GTK+ Applications.

---

### Post by thinhhoang on 2010-12-14
Never mind. Install ibus-gtk and add this to ~/.bashrc file:
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
everything would be just fine.

---

### Post by Zorael on 2010-12-21
As a sidenote, the "preferred solution" is to use the **im-switch** tool to set these environment variables.

Example from my netbook, although it's using UIM instead of ibus;
```
$ **im-switch -l**
Your input method setup under en_US locale as below.
=======================================================
No private "/home/zorael/.xinput.d/en_US or /home/zorael/.xinput.d/all_ALL" is defined.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
  link currently points to **uim-toolbar-qt**
default - priority 10
default-xim - priority 0
none - priority 0
th-xim - priority 20
uim - priority 0
uim-systray - priority 0
uim-toolbar - priority 0
uim-toolbar-qt - priority 0
Current 'best' version is 'th-xim'.
=======================================================
The available input method configuration files are:
default default.old default-xim lo-gtk none th-gtk th-xim uim uim-systray uim-toolbar uim-toolbar-qt 
=======================================================

$ cat /etc/X11/xinit/xinput.d/**uim-toolbar-qt**
# uim with Qt toolbar indicator
[B]XIM=uim
XIM_PROGRAM=/usr/bin/uim-xim
XIM_ARGS=
GTK_IM_MODULE=uim
QT_IM_MODULE=uim[/B]
# It seems to me that the system needs to be initialized.
# Folowing trick will wait 10 seconds without slowing down X start up.
XIM_PROGRAM_XTRA="(sleep 10; uim-toolbar-qt4)"
DEPENDS="uim-xim,uim-gtk2.0|uim-qt,uim-anthy|uim-canna|uim-prime|uim-skk|uim-m17nlib"
```

So '**im-switch -s ibus**' would set up your user to read the file at '**/etc/X11/xinit/xinput.d/ibus**' and import the needed values.

---

### Post by thinhhoang on 2011-01-12
Thanks a lot for the sidenotes.

---

