---
title: "&quot;Unredirect fullscreen window&quot; ccsm setting causes Compiz to crash on reboot"
date: 2012-04-28
forum: General Help
---

### Post by Jeinhor on 2012-04-28
I ticked this option in Ubuntu 11.10 to have XBMC run jitter-free (suggested at different sites, for example Solution 1 here: [http://forum.xbmc.org/showthread.php?tid=98108](http://forum.xbmc.org/showthread.php?tid=98108)).

If I tick the same option in Ubuntu 12.04 amd64 it works as it did in Ubuntu 11.10 - until I reboot. When I reboot, no UI is shown, and (sometimes) after a few minutes an error message pops up saying  Compiz has crashed.

Anyone know what changes could have caused this behaviour? Can anyone confirm it?

To reproduce (obviously only do this if you know how to restore the setting without a GUI):
[LIST=1]
[*]sudo apt-get install compizconfig-settings-manager
[*]Open a terminal, write "ccsm".
[*]Pick the "Composite" category.
[*]Tick the box "Unredirect fullscreen window".
[*]Reboot.
[/LIST]

Thanks in advance!

EDIT: Should probably mention I posted a similar thread on the XBMC forums, to get a view from their side: [http://forum.xbmc.org/showthread.php?tid=130140](http://forum.xbmc.org/showthread.php?tid=130140).

---

