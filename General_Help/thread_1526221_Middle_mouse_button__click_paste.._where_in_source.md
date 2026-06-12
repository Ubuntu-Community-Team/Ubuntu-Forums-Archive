---
title: "Middle mouse button / click paste.. where in source code?"
date: 2010-07-07
forum: General Help
---

### Post by xoros on 2010-07-07
As title says... 
**where in Ubuntu's / Gnome's source code is the middle mouse button being bound to paste?? which file and about which line number?**

Thanks in advance

---

### Post by xoros on 2010-07-07
Anyone ?  So far I have grep'd through **gdm's, metacity's** source codes and the **gnome-daemon-settings** stuff with statements like:
```
~: grep -wir "scroll" /path *
~: grep -wir "Button 2" *
~: grep -wir "Button2" *
~: grep -wir "mouse" *
~: grep -wir "paste" *
~: grep -wir "ctrl" *
~: grep -wir "xbutton.button"
```


I have not had much luck other than finding some function that was excluding the scroll wheel.. 

but didn't have to do anything with pasting

---

### Post by xoros on 2010-07-07
Maybe this thread should be placed in programming.. 
I thought it was too general of a question for that. 

I can't believe it is buried that deep in the source.  :(

---

### Post by xoros on 2010-07-08
20 hour bump ..

---

### Post by diesch on 2010-07-08
It's a function of the X server  so you have to search there.

Why do you want to find this?

---

### Post by endotherm on 2010-07-08
it looks like mouse button actions are set by X rather than gnome or higher, so that may be the problem. per the community documentation, xinput is used to modify x mouse button mappings, so starting there may tell you where the setting is being stored, which may lead you to the code that is referencing it. 

hth

---

