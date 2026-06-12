---
title: "Vmware"
date: 2006-06-20
forum: General Help
---

### Post by Harold P on 2006-06-20
Hello,
For some reason I'm not getting sound when I use VMware with Windows XP. I'm not quite sure what it is. Do I have to enable it somewhere, or what? Or is it just that there is something conflicting in the sound configuration?

---

### Post by firetux on 2006-06-20
Try to kill artsd in your system manager, it is probably blocking the sound.
Also, on the left underside of your window here should be a audio-icon.

---

### Post by bluevoodoo1 on 2006-06-20
[QUOTE=Harold P]Hello,
For some reason I'm not getting sound when I use VMware with Windows XP. I'm not quite sure what it is. Do I have to enable it somewhere, or what? Or is it just that there is something conflicting in the sound configuration?[/QUOTE]


Have you tried installing Vmware Tools?

---

### Post by galv on 2006-06-20
Hello,
I don't have vmware "with me" right now but i believe that you can install sound drivers/codecs in you Windows.

---

### Post by matrooswolf on 2006-06-20
You have to manually add a sound device in the VM settings.
Look in this thread:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
(but I cannot do it at the moment, my VM settings are disabled for some reason :-k )

---

### Post by Harold P on 2006-06-21
[QUOTE=bluevoodoo1]Have you tried installing Vmware Tools?[/QUOTE]
Yes.

I'm going to try to setup my sound device in a few minutes here. I'll get back with this topic in a second.

Okay, is this right?

[IMG]http://img66.imageshack.us/img66/5229/screenshotvirtualmachinesettin.png[/IMG]

---

### Post by bluevoodoo1 on 2006-06-21
[QUOTE=Harold P]Okay, is this right?[/QUOTE]

That should do it. I've done that with 2 installs of Dapper on vmware (used auto detection) and they've both worked.

---

### Post by Harold P on 2006-06-21
It works.

Thanks!

---

### Post by chuvisco on 2006-06-22
[QUOTE=matrooswolf]
(but I cannot do it at the moment, my VM settings are disabled for some reason :-k )[/QUOTE]

My VM settings are also disabled ("greyed out"), so I can't add a sound device or change anything.  Does anyone know how to fix this?

Edit: I'll answer my own question--It looks like the VM needs to be powered off before settings can be changed.

---

