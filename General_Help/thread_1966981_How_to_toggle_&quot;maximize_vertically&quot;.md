---
title: "How to toggle &quot;maximize vertically&quot;"
date: 2012-04-27
forum: General Help
---

### Post by Ralph L on 2012-04-27
Under lucid I set "maximize_vertically" to <Super>Down.  By entering Super+DownArrow I could extend a window from its current size to a size that extended from the top of the screen to the bottom of the screen. By enter Super+DownArrow again I could go back to the original window size.  In other words Super+DownArrow TOGGLED the window vertical dimension.  (Super is the "Windows" key between Fn and Alt.)  I selected this setting by installing the Configuration Editor, and selecting apps>metacity>window_keybindings>maximize_vertically><Super>Down.

Because I somewhat damaged my system I am reinstalling lucid in a new partition.  Again I set "maximize_vertically" to <Super>Down.  Under this new version of lucid, when I enter Super+DownArrow I can maximize vertically ok, but I cannot toggle back to the original size.

How can I get the new installation of lucid to behave like the old installation and toggle the window vertical size?  There must be a toggle setting someplace that I set in my old version of lucid but neglected to set in the new version.  Or maybe a recent update to lucid made the toggle feature not work.  Any help appreciated.

Ralph

---

### Post by Paddy Landau on 2012-04-28
I don't know if there is a toggle button. Look through the Compiz settings (Compiz Config Settings Manager, or CCSM).

I did find "Maximumize". CCSM > Window Management > Maximumize (enable) > Bindings.

If you don't already have CCSM, install [ccsm]("apt:compizconfig-settings-manager") (compizconfig-settings-manager).

---

### Post by Ralph L on 2012-07-06
I moved to Ubuntu 12.04 precise pangolin and the toggle worked fine.

---

