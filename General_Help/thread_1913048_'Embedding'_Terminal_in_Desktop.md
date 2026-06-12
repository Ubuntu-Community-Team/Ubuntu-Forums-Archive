---
title: "'Embedding' Terminal in Desktop"
date: 2012-01-21
forum: General Help
---

### Post by Mr_Vile on 2012-01-21
Hi, relative newbie here, I used to do this using compiz fusion because I found it easier to learn to do things on the command line, not to mention the fact that having it there 'on' the desktop encouraged me to use it as much as possible.

However I've been having problems, after a stint of using windoze exclusively on my laptop for about a year for work purposes, I've come back to Ubuntu and it's now the new desktop environment. The problem is the old processes I've tried for 'embedding' the terminal now result in some nasty looking terminal windows opening up. 

Does anyone have any information on how to go about doing this now? It's not really of critical importance, I can live without it, it was just pretty handy!

Thankyou for any help

---

### Post by dcstar on 2012-01-22
> **Mr_Vile said:**
> Hi, relative newbie here, I used to do this using compiz fusion because I found it easier to learn to do things on the command line, not to mention the fact that having it there 'on' the desktop encouraged me to use it as much as possible.

However I've been having problems, after a stint of using windoze exclusively on my laptop for about a year for work purposes, I've come back to Ubuntu and it's now the new desktop environment. The problem is the old processes I've tried for 'embedding' the terminal now result in some nasty looking terminal windows opening up. 

Does anyone have any information on how to go about doing this now? It's not really of critical importance, I can live without it, it was just pretty handy!

Thankyou for any help

The Terminal is just an app, just start it in Unity and then lock it into the side panel like any other app.

---

### Post by mcduck on 2012-01-22
> **Mr_Vile said:**
> Hi, relative newbie here, I used to do this using compiz fusion because I found it easier to learn to do things on the command line, not to mention the fact that having it there 'on' the desktop encouraged me to use it as much as possible.

However I've been having problems, after a stint of using windoze exclusively on my laptop for about a year for work purposes, I've come back to Ubuntu and it's now the new desktop environment. The problem is the old processes I've tried for 'embedding' the terminal now result in some nasty looking terminal windows opening up. 

Does anyone have any information on how to go about doing this now? It's not really of critical importance, I can live without it, it was just pretty handy!

Thankyou for any help
So you want a borderless, transparent terminal on your desktop?

The easiest way to do it in current Ubuntu version is same as before, use the CompizConfig Settings Manager, and exclude your terminal window in the Window Decoration-plugin's rules & use the Place Windows plugin to set the correct location, and then the Window Rules-plugin to set the window below, sticky, disable moving/resizing and skip the taskbar etc.

Creating the Compiz rules is most likely easiest if you create a new profile in Gnome-terminal, set it to use a certain window title (also disable the option for programs to change the title) and then when adding the desktop terminal to your startup applications modify the command to load this profile instead of default one ("gnome-terminal --window-with-profile=PROFILENAME").

---

