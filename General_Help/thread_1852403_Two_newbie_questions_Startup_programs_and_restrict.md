---
title: "Two newbie questions: Startup programs and restricting panels"
date: 2011-09-30
forum: General Help
---

### Post by resle on 2011-09-30
Hi, I am more or less a newbie to Ubuntu. Trying to fix 2 things:
(Ubuntu 10.10)

1) I add a new program to the startup list, namely a command line that launches Chromium with some parameters. Save, restart, and it correctly launches at startup. But then, it automatically disappears from the startup list. I unchecked the box that asks to save the currently running programs to startup them at the next login, too. 

2) Is there a way to prevent a user from adding/removing panels?

Thanks a lot in advance,

 andrea

---

### Post by garvinrick4 on 2011-09-30
> Is there a way to prevent a user from adding/removing panels?
Configuration editor to: Apps/panel/global/ checkmark lockdown

---

### Post by coldraven on 2011-09-30
I think that garvinrick4 meant to say to type this in a terminal
```
sudo gconf-editor
```You should then see this (screenhot)

I have not had your startup problem, entries in my list seem to stay there.
Hopefully someone will help you solve it.

---

### Post by garvinrick4 on 2011-09-30
> I think that garvinrick4 meant to say to type this in a terminalThe GUI is configuration editor (gconf-editor) can be selected in main menu (alacarte) as a part of system tools in GUI. I try to be more User interface than command line for the 
"newbie" as OP states. 
But both ways work coldraven and nice to give both options and screenshot is always cool.

---

