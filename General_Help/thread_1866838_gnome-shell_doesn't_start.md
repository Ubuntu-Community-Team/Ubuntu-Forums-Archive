---
title: "gnome-shell doesn't start"
date: 2011-10-22
forum: General Help
---

### Post by Bazon on 2011-10-22
or OK, it starts, but just with a blank desktop plus a top panel containing the nautilus menu.
So what went wrong?
I installed gnome-shell from the software center and started it started it by selecting "GNOME" in the thing which replaced GDM.

(Maybe it's and old entry for Gnome2? I got to 11.10 by updating, it's not a fresh install..)



PS:
Sorry if this was asked before, but the search function get me tons of threads not helping...
....and I place it here in the community cafe as I suppose the gome-shell-knowers tend to hang out here. ;-)

---

### Post by jeeves on 2011-10-22
Can you post a screenshot?

I was thinking you may have run across the same problem described in the post below.What was happening there was Unity was loading even though Gnome was selected in the lightDM memu.

[http://ubuntuforums.org/showthread.php?t=1856276](http://ubuntuforums.org/showthread.php?t=1856276)

---

### Post by Bazon on 2011-10-22
Thanks, I tried your tip, but that didn't change anything.

Screenshot? Of course, but there's not much to see there:
[http://ubuntuone.com/3yCNvvMAxujg35iPPyz2ki](http://ubuntuone.com/3yCNvvMAxujg35iPPyz2ki)

---

### Post by jeeves on 2011-10-22
Yes, that certainly looks different from the problem I had. 

I'm pretty much out of ideas on this one, but you could try logging into whatever desktop enviroment you were using before and running the **gnome-shell --replace** command in a terminal. Check for any really alarming looking error messages and see if it will replace the running windows manager. 

*Obviously make sure you have some sort of recovery plan before, because this command could leave you in partially functioning desktop.*

good luck

---

### Post by Bazon on 2011-10-22
"gnome-shell --replace" indeed does it, thanks!
(no major error messages displayed btw.)

---

### Post by Bazon on 2011-10-22
PS:

Could someone please compare if something is wrong with my **/usr/share/xsessions/gnome-shell.desktop** file?:

```
[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session --session=gnome
TryExec=gnome-shell
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

---

### Post by ShodanjoDM on 2011-10-22
> **Bazon said:**
> PS:

Could someone please compare if something is wrong with my **/usr/share/xsessions/gnome-shell.desktop** file?:

```
[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session --session=gnome
TryExec=gnome-shell
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

Same here:

```
[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session --session=gnome
TryExec=gnome-shell
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0

```

FYI, I'm running gnome-shell 3.2.1 from oneiric-proposed. No change there.

---

### Post by Bazon on 2011-10-22
Strange.
For now, I'm doing it [that way]("http://askubuntu.com/questions/30938/how-can-i-have-different-startup-programs-for-desktop-edition-and-classic-edi") only starting *gnome-shell --replace* instead of cairo dock. Seems to work for now...

---

### Post by Bazon on 2011-10-22
No, I have to correct myself, login only works every second to forth time that way (else fall back to LightDM), log out doesn't work that way.
Hm.

---

### Post by cariboo on 2011-10-22
Moved to General Help, as this isn't something you'd discuss around the water cooler at work.

---

### Post by Bazon on 2011-10-23
I hope someone reads it here, too. ;-)

So anyway, has someone an idea how to fix this? I really would like to start Gnome-shell from LDM!

---

### Post by fantab on 2011-10-23
> **Bazon said:**
> I hope someone reads it here, too. ;-)

So anyway, has someone an idea how to fix this? I really would like to start Gnome-shell from LDM!

If you haven't already, [check this]("http://askubuntu.com/questions/43808/how-do-i-use-lightdm-with-gnome3") out.

---

### Post by Bazon on 2011-10-23
> **fantab said:**
> If you haven't already, [check this]("http://askubuntu.com/questions/43808/how-do-i-use-lightdm-with-gnome3") out.

Soory, that is not relevant, as it describes how LDM is installed in 11.04. In 11.10, LDM IS installed and default.

---

### Post by Bazon on 2011-10-23
Found out something new:
when I replace 
```
TryExec gnome-shell
```
by 
```
Exec gnome-shell
```
gnome-shell actually starts, but no personal settings are applied. E.g., I got no wallpaper, only a blue screen background. When I try to set a wallpaper, this setting is not applied.

---

### Post by Bazon on 2011-10-26
So, I made a fresh install to get rid of this, still the same problem.
Doesn't anybody have an idea how to solve this? :-(

---

### Post by Bazon on 2011-10-27
OK, since including "sleep" to the start script it works mostly:

```
#! /bin/bash
gnome-session --session=gnome &
sleep 15
gnome-shell --replace
```
*(called by /usr/share/xsessions/gnome-shell.desktop by Exec=)*

the only thing that doesn't work is logout, but that's not so bad as there is still alt+print+k....

---

