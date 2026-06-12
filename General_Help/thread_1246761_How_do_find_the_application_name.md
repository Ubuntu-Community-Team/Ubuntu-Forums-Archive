---
title: "How do find the application name"
date: 2009-08-22
forum: General Help
---

### Post by hgraham on 2009-08-22
Devilspie asks to have "Application_Name" listed in the .ds files.

How do I discover the application name.  For example "Mozilla Firefox"  "Firefox"  "Fire Fox"  "Firefox 3.0"  "firefox"

Thanks
Howard

---

### Post by HiImTye on 2009-08-22
if youre using firefox 3.0.x then it is 'firefox'
if you're using firefox 3.5.x (Shiretoko) then it is 'firefox-3.5'

---

### Post by hgraham on 2009-08-22
I only intended firefox as an example, what about other programs?  How do you find application names in general.

Thanks 
Howard

---

### Post by HiImTye on 2009-08-22
theres a few ways
1) if the application is in your menu

[LIST=1]
[*]right click your menu
[*]select edit menus
[*]find the program in the list
[*]right click it
[*]select properties
[*]the program will be listed in 'command' - you can filter out all the extra crap normally (except for WINE programs, some things are required for WINE)
[/LIST]
2) by using TOP/HTOP/Gnome-System-Monitor

[LIST=1]
[*]start the program
[*]open up a system monitoring tool (top/htop/gnome-system-monitor)
[*]for gnome-system-monitor select 'processes' and then sort by CPU ensuring the values above '0' are at the top
[*]make the program do something
[*]look for it in the list, should be near the top
[/LIST]
that's just off the top of my head

---

### Post by VCoolio on 2009-08-22
You can use xprop. In ~/.bashrc, add this line (for your own sake preferably in the alias section):
```
alias xp='xprop | grep "WM_WINDOW_ROLE\|WM_CLASS" && echo "WM_CLASS(STRING) = \"NAME\", \"CLASS\""'
```

Now (re)start your terminal, run "xp" and click the window you need and read the output.

---

### Post by Nepherte on 2009-08-22
xprop is definetely the way to go here.

---

