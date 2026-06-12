---
title: "&quot;the update information is outdated&quot; redux"
date: 2009-07-25
forum: General Help
---

### Post by Ashin Sopaka on 2009-07-25
Yesterday, a yellow triangle with an exclamation point began appearing the notification area. Hovering the cursor above it, this message appears:

[INDENT]"The update information is outdated. this may be caused by network problems or by a repository that is no longer available. please update manually by clicking on this icon and then selecting "check for updates" and check of some of the listed repositories fail."[/INDENT]

Ran update manager and it returns:

[INDENT]**Your system is up-to-date**The package information was last updated less than one hour ago.[/INDENT]

Ran [sudo apt-get update] in a terminal. Everything **Hit** except for the Translations, which returned **IGN**, (or **Failed** in the update manager), but that has always been the case for me with Intrepid, and now Jaunty.

Searching the forums for similar issues, I did another [sudo apt-get update] in the terminal as well as [sudo apt-get upgrade]. The upgrade returned:

[INDENT]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/INDENT]

The triangle disappears after all these machinations, but reappears seemingly randomly.

Is this something to worry about? Any other recommendations?

Thanks in advance

---

### Post by hubertofliege on 2009-09-09
Same happens for me.  Something like this happened once before, and I fixed it by opening up a list of sources in gedit and pasting a bunch of new ones in.  I don't know what thread that was though, and I wish I knew more specifically what fixes it.

---

