---
title: "Turning &quot;composite&quot; on and off easily ? Maybe via shell script ?"
date: 2010-11-26
forum: General Help
---

### Post by hexahive on 2010-11-26
Hi everyone.

I've been searching for an easy method to toggle compositing option within the Xorg, but haven't found any solution. Is there a way to do it via some command or something else in the terminal or it has to be done by adding/removing:

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```

into /etc/X11/xorg.conf, and then restarting it ?

If that is the only way, could someone help me by creating the script that would add/remove those lines by parsing the xorg.conf, and then restart the Xorg server ? I know how to do the restarting part, but have no experience with parsing documents so I promise to be a good student and utilise that in the future :)
I'd also like to know if there is a way to, instead of making two scripts - one for enabling and the other for disabling, make only one script that would be accessed by issuing something like "sudo sh composite.sh param=off" ?

Thanks in advance.

---

### Post by SteveDee on 2010-11-27
> **hexahive said:**
> ...If that is the only way, could someone help me by creating the script that would add/remove those lines by parsing the xorg.conf....

An easier way is to have 2 versions of xorg.conf (e.g. xorg.comp and xorg.nocomp) and just write a script that copies xorg.comp to xorg.conf, and another script that copies xorg.nocomp to xorg.conf. You then need to restart X.

These 2 scripts can be run via desktop or panel launchers.

---

### Post by wojox on 2010-11-27
What's wrong with 

```
compiz --replace
```

```
metacity --replace
```

---

### Post by wet-willy on 2010-11-27
Although I might have different repositories enabled, xcompmgr is available through package installer. Based on the little information I read, it should be what you're looking for. Perhaps googling "man xcompmgr" might give you a link to the man pages to read up first if you like.

---

