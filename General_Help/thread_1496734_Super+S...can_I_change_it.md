---
title: "Super+S...can I change it?"
date: 2010-05-29
forum: General Help
---

### Post by primetime34 on 2010-05-29
I'm trying to the use the select/group/tab windows feature in Compiz.  However, super+s is a shortcut that lets me logout/shut down.  How can I change that without changing the key binding in compiz?  Thanks.

---

### Post by alem189 on 2010-05-29
Do you know the command that does that? You might be able to change it with System --> Keyboard Shortcuts, but I don't know if it will override shutdown or even work.

---

### Post by primetime34 on 2010-05-29
I don't understand...the command super+s is like clicking the power button on the top panel.  I want to disable that shortcut or change it to something else.  Anybody know how??

---

### Post by alem189 on 2010-05-29
My earlier post wasn't very clear - I mean if you go in the main menu to System --> Keyboard Shortcuts, you could add a keyboard shortcut that would use Super + S, and your custom shortcut would override the shortcut to shut down the computer. However, I don't know the command that would do what you're asking it to do, so I can't help you there.

---

### Post by primetime34 on 2010-05-29
I basically want to erase the keyboard shortcut super+S which by default seems to bring up the shutdown system. Anybody able to help with that?  I didn't see it in keyboard shortcuts in the preferences menu

---

### Post by alem189 on 2010-05-29
If it's not in the keyboard shortcuts menu, I don't know how to help you.
:(

---

### Post by dcstar on 2010-05-29
> **primetime34 said:**
> I basically want to erase the keyboard shortcut super+S which by default seems to bring up the shutdown system. Anybody able to help with that?  I didn't see it in keyboard shortcuts in the preferences menu

Play around in System-Preferences-Keyboard-Layouts-Options, there may be something there that works for you.

---

### Post by l-x-l on 2010-05-29
Man, I've been looking for that shortcut forever (Super + S). Don't know why Alt+Ctrl+Delete doesn't have the logout/switch option. Thanks.

---

### Post by primetime34 on 2010-05-30
Not in the keyboard layout options...anybody else come across this?  I would love to change that shortcut...

---

### Post by klikevil on 2010-07-06
:KSFIGURED IT OUT:KS


Ghetto workaround time.... ready?  Right click on it, remove from panel go in to compiz choose disabled for the select single window keyboard binding then click close.  Re-enable the select single window and VIOLA  you can now group and tab windows as you please.  Of course you'll be restarting with init 6 and what not or your preferred method, but hey it got the job done and until you find a better solution then my word is the law!

---

### Post by simosx on 2010-07-06
> **klikevil said:**
> :KSFIGURED IT OUT:KS


Ghetto workaround time.... ready?  Right click on it, remove from panel go in to compiz choose disabled for the select single window keyboard binding then click close.  Re-enable the select single window and VIOLA  you can now group and tab windows as you please.  Of course you'll be restarting with init 6 and what not or your preferred method, but hey it got the job done and until you find a better solution then my word is the law!

Cool guerrilla tip. You may want to pass it to the people affected with this bug, at [https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/334544](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/334544)

---

### Post by bytesaber on 2010-10-07
> **klikevil said:**
> :KSFIGURED IT OUT:KS


Ghetto workaround time.... ready?  Right click on it, remove from panel go in to compiz choose disabled for the select single window keyboard binding then click close.  Re-enable the select single window and VIOLA  you can now group and tab windows as you please.  Of course you'll be restarting with init 6 and what not or your preferred method, but hey it got the job done and until you find a better solution then my word is the law!

Works great.  Then go back to the panel, right mouse click, choose "add to panel..." and add the "Shut Down" tool.  It serves the same job and then you don't have to do init 6 or ctrl alt del.

This may seem silly, but it does help me keep the same Compiz keystrokes from workstation to workstation.

-bytes

---

