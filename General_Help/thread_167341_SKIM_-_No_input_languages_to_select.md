---
title: "SKIM - No input languages to select"
date: 2006-04-28
forum: General Help
---

### Post by Baka Dasai on 2006-04-28
I've installed skim, and selected English and Japanese as the IM engine options in the skim configuration.

I have a nice-looking skim icon in my system tray.  But when I click that icon the list of languages is empty.

I have the following packages installed:

[LIST]
[*]skim
[*]libskim0
[*]libscim8c2a
[*]scim
[*]scim-anthy
[*]scim-gtk2-immodule
[*]scim-m17n
[*]scim-modules-socket
[*]scim-modules-table
[*]scim-qtimm
[*]scim-tables-ja
[*]scim-uim
[/LIST]

How can I get some languages (specifically Japanese) to select?

---

### Post by njf on 2006-04-28
Try this is konsole:
```
QT_IM_MODULE=scim kate
```
See if u can press ctrl-space to invoke skim and type japanese in kate.

---

### Post by idjut on 2006-04-28
I have the same problem. I cant invoke scim. I did this: 

# apt-get install uim anthy scim-gtk2-immodule scim-uim scim-chinese scim-hangul scim-tables-zh scim-tables-ja scim-tables-ko

as per Ubuntu CJK ([http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)) 

When I type scim in terminal i get: 

$ scim
Smart Common Input Method 1.0.2

Launching a SCIM daemon with Socket FrontEnd...
Launching a SCIM process with x11...
SCIM has exited abnormally.


I did try to add scim to startup for X11 also as described in Ub. CJK (above), but got an error here: 

$ echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup

I didnt know 'export XMODIFIERS="@im=SCIM"'  or something, cant remember exactly. Anyway I pasted the echos into the file to see if that helped. :-?

---

### Post by Baka Dasai on 2006-04-28
[QUOTE=njf]Try this is konsole:
```
QT_IM_MODULE=scim kate
```
See if u can press ctrl-space to invoke skim and type japanese in kate.[/QUOTE]

Thank you, this works - I can choose the input language and type in Japanese.

What I'm hoping to achieve is to be able to switch input languages for any app without having to start that app in a special way.  How can I have "QT_IM_MODULE=scim" apply for all apps?

---

### Post by njf on 2006-04-28
[QUOTE=Baka Dasai]Thank you, this works - I can choose the input language and type in Japanese.

What I'm hoping to achieve is to be able to switch input languages for any app without having to start that app in a special way.  How can I have "QT_IM_MODULE=scim" apply for all apps?[/QUOTE]

Add this to your /etc/environment
```
QT_IM_MODULE=scim
```

Then reboot.

---

### Post by Baka Dasai on 2006-04-29
[QUOTE=njf]Add this to your /etc/environment
```
QT_IM_MODULE=scim
```

Then reboot.[/QUOTE]

Thanks, this worked perfectly for KDE apps.  

But skim didn't work in GTK/Gnome apps.  So I added "GTK_IM_MODULE=scim" to /etc/environment and now I have skim working perfectly in everything.

Happy happy :D :D :D

---

### Post by pizzat104 on 2006-07-05
I have the same problem described here (ie. I can't choose an input language when I use skim). I am running Kubuntu 6.06. I've installed skim through Adept and installed the Chinese language support. I start up Kate and skim, but can't choose the language.

I've tried modifying the etc/environment file and rebooting, but still the same problem. 

Anybody have any ideas as to what could be wrong? Thanks in advance.

---

