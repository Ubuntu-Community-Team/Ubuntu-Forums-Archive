---
title: "Nautilus: how do I get the full path to display?"
date: 2010-12-26
forum: General Help
---

### Post by orange_roughy on 2010-12-26
Hi,

How can I get the full path to display in Nautilus so I can copy it to the clipboard and/or type a path manually?

thanks,
orange_roughy

---

### Post by Swagman on 2010-12-26
ctrl + L

---

### Post by wojox on 2010-12-26
Ctrl+L should do it.

---

### Post by orange_roughy on 2010-12-26
Thanks! Is there any way to make this "sticky" so I don't have to do it everytime I open Nautilus?

---

### Post by Morbius1 on 2010-12-26
To make it permanent open a terminal and type:
```
gconf-editor
```Then go to:
> /apps/nautilus/preferencesAnd check:
> always_use_location_entry

---

### Post by karthick87 on 2010-12-26
+1 on post #5

---

### Post by orange_roughy on 2010-12-26
> **Morbius1 said:**
> To make it permanent open a terminal and type:
```
gconf-editor
```Then go to:
And check:

Perfect... thank you so much.

---

### Post by VastOne on 2010-12-26
> **karthick87 said:**
> +1 on post #5

Ditto!

Thanks Morbius1

---

### Post by orange_roughy on 2011-12-17
This no longer appears to work--gconf-editor is not found. What now?

---

### Post by orange_roughy on 2011-12-17
nvm. i was able to install it.

---

### Post by 73ckn797 on 2011-12-17
If you are using 11.10, that is what I am working with, the option for the setting is only found using dconf-editor under "org/nautilus/preferences. It does not show up using gconf-editor. At least from what I found.

I have uninstalled Unity and use Gnome 3 so your mileage may vary.

---

### Post by orange_roughy on 2011-12-18
> **73ckn797 said:**
> If you are using 11.10, that is what I am working with, the option for the setting is only found using dconf-editor under "org/nautilus/preferences. It does not show up using gconf-editor. At least from what I found.

I have uninstalled Unity and use Gnome 3 so your mileage may vary.

I'm also using Gnome 3 (Linux Mint version 12). How do I install dconf-editor? 

[PHP]sudo apt-get install dconf-editor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dconf-editor[/PHP]

thanks!

---

### Post by Synoc on 2011-12-18
```
sudo apt-get dconf-tools
```I believe
[http://ubuntuforums.org/showthread.php?t=1743646]("http://ubuntuforums.org/showthread.php?t=1743646")

---

### Post by bluexrider on 2011-12-18
> **orange_roughy said:**
> I'm also using Gnome 3 (Linux Mint version 12). How do I install dconf-editor? 

[PHP]sudo apt-get install dconf-editor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dconf-editor[/PHP]thanks!

if you are using Linux Mint 12 w/MATE then it uses a mate-config-editor

---

### Post by 73ckn797 on 2011-12-18
> **Synoc said:**
> ```
sudo apt-get dconf-tools
```I believe
[http://ubuntuforums.org/showthread.php?t=1743646](http://ubuntuforums.org/showthread.php?t=1743646)


My error, dconf-tools is the correct package. In the menu is shows as dconf Editor

---

### Post by hsweet on 2011-12-18
I tried dconf /org/gnome/nautilis/preferences has no setting I can change.  I do have gconf-editor(what is the difference?) and could change it there, but it had no effect.

11.10/Unity

---

### Post by bluexrider on 2011-12-18
> **orange_roughy said:**
> I'm also using Gnome 3 (Linux Mint version 12). How do I install dconf-editor? 

[PHP]sudo apt-get install dconf-editor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dconf-editor[/PHP]thanks!
one other thought. Again if you are using LinuxMint 12 then the default file manager is Caja NOT nautilus.

you may want to read the release notes on the OS you are using. It contains a lot of useful info

---

### Post by orange_roughy on 2011-12-18
yes, i am using Linux Mint 12. I cannot find "caja" in dconf-editor. Any ideas?

---

### Post by stinkeye on 2011-12-18
Try the terminal command
```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```

Works in my mint12 and unity install.

---

### Post by hsweet on 2011-12-18
:)  That did it for me.  But it seems that this being Linux, it should be easier to find..

gsettings set org.gnome.nautilus.preferences always-use-location-entry true

---

### Post by orange_roughy on 2011-12-19
> **stinkeye said:**
> Try the terminal command
```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```

Works in my mint12 and unity install.

Perfect! Thanks!

---

