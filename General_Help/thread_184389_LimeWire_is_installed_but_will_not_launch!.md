---
title: "LimeWire is installed but will not launch!"
date: 2006-05-29
forum: General Help
---

### Post by randell6564 on 2006-05-29
Hi!

I have finally been able to install limewire, and the limewire launcher is in my **Applications>internet** menu, BUT...

Every time that I click on it, nothing happens!!  No error messages, NOTHING!

It never starts!

Any help?   CRAP!

---

### Post by gerbman on 2006-05-29
[QUOTE=randell6564]Hi!

I have finally been able to install limewire, and the limewire launcher is in my **Applications>internet** menu, BUT...

Every time that I click on it, nothing happens!!  No error messages, NOTHING!

It never starts!

Any help?   CRAP![/QUOTE]Open up a terminal (Applications->Accessories->Terminal) and start limewire from there (type "limewire" and hit enter). What error messages do you get? My guess is that [Java]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport#head-68565ae07a003332e82c9f23706638777396c249") needs to be installed.

---

### Post by amcavoy on 2006-05-30
I have the same problem.
```
alex@ubuntu:~$  limewire
bash:  limewire:  command not found
```

---

### Post by gerbman on 2006-05-30
[QUOTE=amcavoy]I have the same problem.
```
alex@ubuntu:~$  limewire
bash:  limewire:  command not found
```[/QUOTE]I'm not sure if that's the correct command to start it, I just assumed it would be. If you can't get it to work, you might try [FrostWire]("http://www.frostwire.com/") - just as good IMO, and works fine out of the box (as long as Java is installed).

---

