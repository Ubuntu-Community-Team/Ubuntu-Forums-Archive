---
title: "gnome-panel doesn't start on login, but gconf settings look correct"
date: 2010-09-05
forum: General Help
---

### Post by bbqsandwich on 2010-09-05
Hello,

I installed avant-window-navigator and followed these instructions to remove gnome-panel from startup:

[http://wiki.awn-project.org/FAQ#How_do_I_permanently_remove_GNOME_Panel_from_my_GNOME_session.3F](http://wiki.awn-project.org/FAQ#How_do_I_permanently_remove_GNOME_Panel_from_my_GNOME_session.3F)

However I have since uninstalled AWN and now cannot get gnome-panel to load at startup.

I think I have put my settings back where they should be -- looking at them in gconf-editor:

1. desktop > gnome > session, the required_components_list is [windowmanager,filemanager,panel]

2. desktop > gnome > session > required_components_list, the panel value is "gnome-panel"

Yet gnome-panel does not load at startup. Any ideas why?

Clarification: I can get gnome-panel to load by listing it under Startup Applications, but I am curious why it won't load via the gconf settings. 

Thanks in advance for your thoughts/help!

---

### Post by 73ckn797 on 2010-09-05
Press ALT-F2 (to open a terminal) and type gnome panel.

---

### Post by bbqsandwich on 2010-09-05
Thank you but the problem is not getting gnome-panel to start at all - I have it in my Startup Applications - but rather understanding why the gconf settings don't appear to be making it start.

---

### Post by Mr_VeRiTy on 2010-09-05
What steps did you use to stop it from starting in the first place?

EDIT: I just noticed the link at top, It sounds like you did everything right.

---

### Post by fermulator on 2011-02-24
Any luck? I have the same situation.
(although in my case, I still have AWN installed, but I found a trick to "load gnome-panel" and hide it, so that I can still use ALT+F2.)

Just need to get gnome-panel to load again automatically.

---

### Post by stinkeye on 2011-02-24
I think the original posters problem was he had
**[windowmanager,filemanager,panel]**
in the wrong order, as I restarted with that order and gnome-panel failed to load.
The default order is **[windowmanager,panel,filemanager]**


To revert back to the default order
```
gconf-editor /desktop/gnome/session/required_components_list
```
and right click on the **required_components_list** entry and choose **Unset Key**.

---

### Post by ankit singh on 2011-02-24
You can go for resetting your gnome settings
open terminal and type this 

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by fermulator on 2011-02-24
This was the step I was missing:
2. desktop > gnome > session > required_components_list, the panel value is "gnome-panel"

The value for me was "empty".

---

### Post by stinkeye on 2011-02-25
> **fermulator said:**
> This was the step I was missing:
2. desktop > gnome > session > **required_components_list**, the panel value is "gnome-panel"

The value for me was "empty".
Yep ,but I think you may mean the key
```
gconf-editor /desktop/gnome/session/**required_components/panel**
```

---

### Post by fermulator on 2011-02-27
> **stinkeye said:**
> Yep ,but I think you may mean the key
```
gconf-editor /desktop/gnome/session/**required_components/panel**
```

 -- yes -- good catch

---

### Post by -dean- on 2011-03-16
> **fermulator said:**
> -- yes -- good catch

I am able to boot to the point that I get the opening tune, but no desktop.
I can, and have, switch to Ctrl-Alt F2 and log in.
I tried:
    sudo gconf-editor /desktop/gnome/session/required_components/panel
I get the message:
**(gconf-editor:2619)  CRITICAL**:  Failed to parse arguments:  Cannot open display   

I hope I am getting closer and am just missing something that someone out there can give me an assist.

I have a redundant 10.10 Maverick and I can see and operate on the broken 10.10 Maverick by opening Nautilus with sudo from the command line.  I know this is dicey so whatever I do in this fashion I do with care and trepidation, and do things so that  whatever I change I can get back the original configuration if necessary.

next day  3/16/:
I tried 
   gconf-editor .gnome/desktop/gnome/session/required_components/panel
with and without sudo. 
   same **CRITICAL message.

---

### Post by phillroberts on 2011-06-10
Not sure if you're still having this problem, but I came across this thread after experiencing the same issue and wanted to document it for my future reference as well as anyone else that may run into the problem.

It turns out that my default session was NOT Gnome.  I had inadvertently changed it to something else and forgot to change it back.  When I changed it back to Gnome, the gnome-panel started to load automatically again.

I've recently switched from Ubuntu to LinuxMint, so I don't remember exactly, but you should be able to set the default gnome session by clicking on Administration and navigating to Login Screen.  

Alternatively, there should be a session selection option on the login screen itself.

Hope this helps someone. 

--Phill

---

