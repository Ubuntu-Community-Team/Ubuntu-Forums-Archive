---
title: "Can't update ICEauthority file on startup - halp!"
date: 2010-09-27
forum: General Help
---

### Post by searchfgold6789 on 2010-09-27
yikes, I just did some updates with the update manager and one of them was gdm.
Now every time xubuntu starts up, before the login screen, I get the following error message:

[LIST]
[*]Could not update ICEauthority file /var/lib/gdm/.ICEauthority
[/LIST]
It is an empty dialog box with only a single Ok button. (Which doesn't make sense because this is definitely NOT ok.)
Once I press Enter it will take me to the login screen, where I can log into an xterm and xubuntu session without any trouble, except that there is some extra lag and many strange graphics quirks and other unappealing things that were not here before...
Could someone please help me get rid of this highly annoying error?
I've already tried ```
$ chown gdm:gdm -R /var/lib/gdm/
```

---

### Post by andrewthomas on 2010-09-27
try to move the file and see if it is fixed

```
mv ~/.ICEauthority ~/.ICEauthority.old
```

---

### Post by searchfgold6789 on 2010-09-27
Wow, okay... I didn't even have to do anything it just fixed itself...
Thanks anyway!

---

### Post by Zen87 on 2011-03-04
> **andrewthomas said:**
> try to move the file and see if it is fixed

```
mv ~/.ICEauthority ~/.ICEauthority.old
```

Thanks! This worked for me.

---

### Post by blue digit on 2011-05-15
I encountered exactly the same issue, and fixed your way... :guitar: ...it's working for me!
[FONT=Arial Black][SIZE=4]tnx[/SIZE][/FONT] :biggrin:

---

