---
title: "location of config files for gnome-system-log"
date: 2012-05-05
forum: General Help
---

### Post by Budoc on 2012-05-05
Hi,

I've tried googling for this, as well as searching the forum, but I think that the search terms that I am using are too generic to be helpful.

I am trying to locate the config file(s) for the Ubuntu 12.04 log file viewer. They should be somewhere in my home directory. The problem that I have is that some settings have been carried over from a previous version of Ubuntu where I monitored logs of some scripts that I do not use any more - this results in an error message every time the log file viewer is loaded up. The man entry for gnome-system-log isn't helpful as it only mentions a config file under /etc/ which wouldn't have been preserved through upgrades. So far, I have found entries for gnome-system log under both ~/.gconf/schemas/apps/ and ~/.gconf/apps/ but moving these directories elsewhere has no effect. Running find . -iname "*gnome*system*log*" fails to find anything relevant.

Any ideas?

---

### Post by mc4man on 2012-05-05
Likely in gsettings, though have done no upgrades here
see screen for dconf-editor which is in the package dconf-tools, location is org.gnome.gnome-system-log


Or if wanting to set to default of 'none' from cli either of these, do the same thing

 ```
gsettings set org.gnome.gnome-system-log logfiles  []
```
 ```
gsettings reset org.gnome.gnome-system-log logfiles
```

Note: editing in dconf-editor is easy but may not be intuitive, - 
You highlight a key, then click in the edit area till it goes 'white'. then make your edit(s)
To set keep the cursor in the edit box, press enter on the keyboard, don't click out or no change will be made

---

### Post by Budoc on 2012-05-05
Thank you **mc4man**, that works perfectly!

Edit: I ended up using the terminal commands rather than dconf-editor, but thank you for introducing me to it.

---

### Post by mc4man on 2012-05-05
Settings are being moved over to gsettings/dconf so using dconf-editor to explore when time permits is useful.
Also once you see a few examples gsettings from cli is really alot easier than gconftool
(man gsettings is also quite informative

---

