---
title: "Run Terminal Shortcut Enabled But Not Working??"
date: 2011-04-14
forum: General Help
---

### Post by Matt Pellegrini on 2011-04-14
I've checked under system>preferences>keyboard shortcuts, and the shortcut is enabled but not working.

Is there another setting that is conflicting somewhere that i can't find?

Something to do with CompizConfig settings manager? (I think but can't be sure that's when they stopped working)

Thanks in Advance

---

### Post by ajgreeny on 2011-04-14
**Ctrl+Alt+T**, the default for a gnome terminal in Ubuntu, and maybe generally for gnome as well, is the setting on my system for a new tab in Firefox, and it does not produce a terminal even if FF is not running.

I have set **Ctrl+T** as my terminal keyboard shortcut, and that works much better for me, and I also think it is less palaver than Ctrl+Alt+T.

---

### Post by Matt Pellegrini on 2011-04-14
(EDIT)  after some research the shortcut for FF new tab is **CTRL+t**

[http://support.mozilla.com/en-US/kb/Keyboard%20shortcuts#w_editing]("http://support.mozilla.com/en-US/kb/Keyboard%20shortcuts#w_editing")

Changing it to another combination didn't work, but thanks anyway

---

### Post by Matt Pellegrini on 2011-04-14
also, sorry to confuse things but i managed to create a new shortcut in preference> keyboard shortcuts and set the command gnome-terminal and the shortcut to ctrl+alt+t and it worked fine. (obviously had to disable the other one for that) My problem with this solution was that the terminal would open in the root directory instead of my home directory and changing the bashrc file helped but it would be a LOT simpler if i could just find a way to make the original shortcut work...

Thanks again

_Other shortcuts such as **Alt+F2 **also don't work, whereas **Ctrl+Alt+l **for lock screen works fine._

---

### Post by ajgreeny on 2011-04-14
I use Tab Mix Plus add-on in firefox and I suspect that is where my Ctrl+Alt+T shortcut for a new tab comes from, though I admit I am not sure.  This is, I suppose, one of the potential problems of having so many different keyboard shortcuts in an OS, not all of which are set by the OS itself.  However see the next paragraph below for more possible confusions.

For Alt+F2 to work for the run command there is a setting in compiz-config-settings-manager->General->Gnome Compatibility->General tab where that key combination can be set, and in the commands tab where you can set the screenshot and new terminal shortcuts, so perhaps that is where I have set my keyboard shortcuts; it is such a long time ago that I set them, and they have just been carried over in my /home partition ever since.

---

### Post by Matt Pellegrini on 2011-04-15
Brilliant, that was it, i knew it would have something to do with CompizConfig manager.

So here's the solution for anyone looking at this thread.

************************************************************************************************************************************
Open** System > Preferences > Keyboard Shortcuts** and check that the **Run Terminal **and the **Run Program** shortcuts are set to the shortcut of your choice.

Then open **CompizComfig Manager** and click **Gnome Compatibility** and set the **Run Terminal** and **Run Program** shortcuts here to the **same key combination**. Click back and make sure that the Gnome Compatibility is **checked/ enabled**.

************************************************************************************************************************************
Thanks to ajgreeny for the help.

---

