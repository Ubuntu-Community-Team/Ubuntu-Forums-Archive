---
title: "Disable Pidgin show on system start"
date: 2009-08-22
forum: General Help
---

### Post by randomAccess on 2009-08-22
The only thing I've always hated about Pidgin is the fact that I can't disable it showing up on system boot. Whenever the system starts, Pidgin windows with contacts pop up, then I have to close it manually.
Does anyone know any way to disable this? There is no specific command for this in program's properties, from one version to another, from years ago. :(

---

### Post by fourthofjuly on 2009-08-22
> **randomAccess said:**
> The only thing I've always hated about Pidgin is the fact that I can't disable it showing up on system boot. Whenever the system starts, Pidgin windows with contacts pop up, then I have to close it manually.
Does anyone know any way to disable this? There is no specific command for this in program's properties, from one version to another, from years ago. :(
did you try disabling pidgin from the system>admin>services section where you can disable startup services?

---

### Post by ajgreeny on 2009-08-22
I seem to remember having this problem once before and solved it by delaying the startup of pidgin using sleep in a shell script.
```
#!/bin/sh
sleep 30; /usr/bin/pidgin
```
Try that as the shell script file ,ake it executable, and then point to that file in the startup list in Startup Applications, instead of the pidgin executable, and you may find it works.

EDIT:
I've just tried the two ways to start it at boot time, and I'm glad to say, it is the right answer.  I can't remember the explanation for it right now, but it is something to do with the priority of the timing of starting, or something similar, and it needs to be later for the "no buddies window" to be possible.

---

### Post by randomAccess on 2009-08-22
> **ajgreeny said:**
> I seem to remember having this problem once before and solved it by delaying the startup of pidgin using sleep in a shell script.
```
#!/bin/sh
sleep 30; /usr/bin/pidgin
```
Try that as the shell script file ,ake it executable, and then point to that file in the startup list in Startup Applications, instead of the pidgin executable, and you may find it works.

EDIT:
I've just tried the two ways to start it at boot time, and I'm glad to say, it is the right answer.  I can't remember the explanation for it right now, but it is something to do with the priority of the timing of starting, or something similar, and it needs to be later for the "no buddies window" to be possible.

OH MY GOD! It works!
I don't know how but it's an excellent hack.

THANKS MAN A LOT!!!!!!!!!!!!!!!!!
:guitar:

---

