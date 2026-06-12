---
title: "Permanently change console font"
date: 2010-10-20
forum: General Help
---

### Post by miromiro on 2010-10-20
I want to have Terminus as my console font. Unfortunately, I see no way to set it permanently.

I have edited /etc/default/console-setup and entered:
```
CODESET="Lat15"
FONTFACE="Terminus"
FONTSIZE="16"

```

and then issued: sudo setupcon -v

which changes the font to Terminus for this session, but as soon as I reboot, it is back to the default (and barely legible) font.

I have also tried setfont, as described here:
[http://ubuntuforums.org/showthread.php?t=1030040](http://ubuntuforums.org/showthread.php?t=1030040)

without any luck.

Any pointers would be helpful.

---

### Post by sir_herrbatka on 2010-10-20
why won't you edit rc.local?

---

### Post by miromiro on 2010-10-20
...for the simple reason that I hadn't thought of it. Thank you for the suggestion.

I added this to rc.local:
```
setfont /usr/share/consolefonts/Lat15-Terminus16.psf.gz 

```

but it made no difference.

---

### Post by miromiro on 2010-10-20
The solution is, after making changes to /etc/default/console-setup, to run:
```
sudo dpkg-reconfigure console-setup
```

---

### Post by hellblazer on 2010-11-17
yay! it seems to have worked, but I'm rather sure that it's not necessary to go through the entire setup script.

Maybe all that is needed is to regenerate the initframs?

---

### Post by miromiro on 2010-11-17
> **hellblazer said:**
> but I'm rather sure that it's not necessary to go through the entire setup script.

Maybe all that is needed is to regenerate the initframs?

Possibly - are you willing to test your hypothesis? :)

---

### Post by hellblazer on 2010-11-18
> **miromiro said:**
> Possibly - are you willing to test your hypothesis? :)

Maybe later today if I get bored ;) I'll reply when I do.

---

