---
title: "Login Via Terminal Possible?"
date: 2010-12-16
forum: General Help
---

### Post by Canadian_Pirate on 2010-12-16
Hi,
This may seem redundant, but here goes.
I want to log in via a terminal, like a tty, but I want the graphical interface to start right after login without any human interaction. I remember reading this somewhere, but cannot find where. Any help would be appreciated. 

NB

---

### Post by WorMzy on 2010-12-16
I'm not sure I fully understand your question, but I think what you want to do is add "startx" to your .bash_profile file. This will run the graphical environment upon login via tty (unless X is already running).

You'll need to boot into text mode, or remove/disable gdm from upstart (so the graphical login screen doesn't run on boot up)

---

### Post by wojox on 2010-12-16
I don't have an answer for you, but just out of curiosity why?

---

### Post by Canadian_Pirate on 2010-12-16
I want to login like this because it is more efficient (I think) than having a graphical login, and I do not want to completely remove a login prompt. 
I basically want a prompt like the tty logins instead of GDM. If you want more info then ask a specific question.

---

### Post by wojox on 2010-12-16
> **Canadian_Pirate said:**
> If you want more info then ask a specific question.

What version of Ubuntu you running?

---

### Post by sisco311 on 2010-12-16
You have to add something like:
```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
  . startx
  logout
fi
```
to your ~/.bash_profile file.

---

### Post by Canadian_Pirate on 2010-12-16
I am running maverick with most of the default options/system apps.

---

### Post by wojox on 2010-12-16
> **Canadian_Pirate said:**
> I am running maverick with most of the default options/system apps.

Sorry I haven't tried 10.10. Seems to buggy still. I'd give sisco311's idea a shot. He's good with that stuff. I've seen his previous work. ;)

---

### Post by Canadian_Pirate on 2010-12-16
Ok, got it working. 
I changes the default grub Linux boot to  "quite splash profile text", and then added xstart to ~/.bash_default.

---

### Post by sisco311 on 2010-12-16
Cool!

If you are looking for a lightweight but still fancy login manager, then check out [Qingy]("http://qingy.sourceforge.net/"). 

[[img]http://ompldr.org/tNmlmYw[/img]](http://ompldr.org/vNmlmYw)

---

