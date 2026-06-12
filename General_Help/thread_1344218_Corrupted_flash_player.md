---
title: "Corrupted flash player"
date: 2009-12-02
forum: General Help
---

### Post by omnoms on 2009-12-02
I just installed 9.10, and tried to install flash player by downloading the .deb package.

Whenever I clicked on the pakage, I got this:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

so I tried just deleting it, and reinstalling. 

I get the same message when: I try opening Synaptic, or when I try to use Update manager.

I tried using sudo apt-get --purge remove in terminal to get rid of it, that didn't work. I can't update anything because of it either, so I'm serious considering reinstalling (i have a /home partition, so this isn't that much of a problem). 


Help!


EDIT:
I just realized something else: I installed Opera last night. Whichever browser I open first can't use flashplayer, but the second browsers uses it just fine. 

So if I open firefox first (today), it can't use flash, but Opera can. If I open Opera first, like last night, it can't use flash, but Firefox can.

---

### Post by omnoms on 2009-12-02
tried redownloading from adobe website. Still get the same error message. :frown:

---

### Post by omnoms on 2009-12-03
bumping my own post. Still in the same fix. I'll try to reinstall this weekend if no one answers.

---

### Post by kristine12 on 2009-12-03
Try Uninstalling it then try this:

```
sudo** aptitude** install flashplugin-nonfree
```

Make sure it is in aptitude to remove dependencies...
I believe that this is much safer than other type of installation...

---

### Post by carloslosgrande on 2010-05-14
[FONT="Comic Sans MS"]I'm running 10.04 and this problem has also hit me.
Its fine to say uninstall the flashplayer, but the problem is that it can't be uninstalled because whatever method I try (synaptic or terminal)comes up with the same error message - [COLOR="Red"]E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it. [/COLOR]
It looks like a reinstall is the only answer.
Anyone else have any ideas on this?[/FONT]

---

### Post by wojox on 2010-05-14
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]I'm running 10.04 and this problem has also hit me.
Its fine to say uninstall the flashplayer, but the problem is that it can't be uninstalled because whatever method I try (synaptic or terminal)comes up with the same error message - [COLOR="Red"]E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it. [/COLOR]
It looks like a reinstall is the only answer.
Anyone else have any ideas on this?[/FONT]


What about:

```
sudo dpkg -- configure -a
```

---

### Post by carloslosgrande on 2010-05-14
[FONT="Century Gothic"]Thank Wojox but that command doesn't do anything by itself.
I added -r to see if that would remove the offending file and I get this - [COLOR="Red"]knot@home:/usr/lib/adobe-flashplugin$ sudo dpkg -r -- configure -a libflashplayer.so 
dpkg: warning: ignoring request to remove configure which isn't installed.[/COLOR][/FONT]

---

### Post by wojox on 2010-05-14
It's late. I guess I left out some switches and the offending application. :oops:

Good thing you were on your toes and caught it.

---

