---
title: "lubuntu keybindings"
date: 2012-03-02
forum: General Help
---

### Post by gopher38 on 2012-03-02
I wanted to set up keyboard shortcuts for lubuntu.  I read somewhere that I should add keybindings of the model:

<keybind key="C-S-t">
  <action name="Execute">
    <command>lxterminal</command>
  </action>
</keybind>

To this file:

/.config/openbox/lubuntu-rc.xml

This worked, although the file was overwritten.  That is to say that the code disappeared from the "lubuntu-rc.xml" file on reboot, but the keyboard shortcuts stayed, so they are recorded somewhere.

While adding a few new shortcuts, I included the above terminal shortcut again, and the same thing happened.  That is to say, the code was overwritten, but now CTRL-SHIFT-t opens two terminals.  So the keyboard shortcuts were registered and overwritten.  Then registered again somewhere and overwritten again.

Can anyone tell me how I can reset this so the shortcuts are only implemented once?  On a related note, does anyone know where the keybinds get registered?  Thanks.

---

### Post by gopher38 on 2012-03-03
Well, silly me.  Turns out that the code wasn't overwritten, but it was put on one line and moved to then end of a comment, so I couldn't see it in nano.  Not sure why the formatting was changed, but at least code was still there, so I just had to delete the old bindings.

---

