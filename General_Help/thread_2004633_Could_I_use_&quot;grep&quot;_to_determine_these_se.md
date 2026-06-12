---
title: "Could I use &quot;grep&quot; to determine these settings in dconf and gconf"
date: 2012-06-16
forum: General Help
---

### Post by kansasnoob on 2012-06-16
I've been studying for hours and think I should be able to do this but I'm stumped :confused:

Lets consider two examples of default freshly installed Precise settings, one in dconf and the other in gconf:

```
gsettings set org.gnome.desktop.interface gtk-theme Adwaita
```

```
gconftool-2 -s --type string /apps/metacity/general/theme Ambiance
```

I know those commands work to restore/change those settings but I'll be darned if I can figure out how to use "grep" to determine the existing settings before I begin to change things ;)

It's honestly NOT a big deal because I know I can use "cp -a" to back up the config files first but I'm working towards upgrading a few dozen PC's from 10.04 to 12.04 (hopefully when 12.04.1 is released) and they truly are "personal computers" - no two are identical - so it would be cool if I could "grep" settings like that after the upgrade rather than having to open gconf or dconf and manually click through a menu, and then write things down.

So it's just a matter of saving time, and I'd like to know anyway - inquiring minds and all :D

If I knew how to grep those two settings I'm fairly sure I could figure out the rest and save the output to a .txt file.

Many, many thanks in advance.

---

### Post by dcstar on 2012-06-16
> **kansasnoob said:**
> 
.........
If I knew how to grep those two settings I'm fairly sure I could figure out the rest and save the output to a .txt file.


Use the "Get" function instead of the "Set" function of the respective commands.

Just read the man pages.

---

### Post by kansasnoob on 2012-06-16
I've read so much my eyes feel like they may start bleeding ;)

But based on "Use the "Get" function instead of the "Set" function" I managed to figure out the dconf part, eg:

```
gsettings get org.gnome.desktop.interface gtk-theme
```

But I'm still stuck on the gconf bit :redface:

I've tried both the help and man pages but I'm stuck.

---

### Post by brainwash on 2012-06-16
According to the man page of gconftool-2 you have to use the **-g** option to get the value:
```
gconftool-2 -g /apps/metacity/general/theme
```

---

### Post by kansasnoob on 2012-06-16
> **brainwash said:**
> According to the man page of gconftool-2 you have to use the **-g** option to get the value:
```
gconftool-2 -g /apps/metacity/general/theme
```

Arrgh, I was trying "gconftool-2 -g --type string /apps/metacity/general theme". Seems crazy now ](*,)

Thank you to all very much.

---

