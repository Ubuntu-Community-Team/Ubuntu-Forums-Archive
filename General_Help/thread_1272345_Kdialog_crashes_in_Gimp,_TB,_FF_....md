---
title: "Kdialog crashes in Gimp, TB, FF ..."
date: 2009-09-22
forum: General Help
---

### Post by Oceanic on 2009-09-22
If I choose 
[INDENT]File>Open
File>Save as 
File>Save
File>Attach (in Thunderbird)[/INDENT]
various non-KDE applications like Gimp, FF, TB etc. crash » no hanging, all windows dissappear abruptly when the file dialog pops up.
Applications like Kate, OpenOffice, Amarok, Konqueror have remained unaffected by this.

Guessing this has to do with Kdialog? But how to solve?

Running KDE 4.3 on Jaunty.

Any ideas? - thanks so much !  :)

---

### Post by Oceanic on 2009-09-22
New information on this erratic behaviour:

With Gimp & Inkscape,the problem occurs only when starting (e.g.) gimp from the kde-panel:
/usr/share/applications/gimp.desktop
when starting from the konsole all is well, even no errors or warnings on STDERR or STDOUT.

When I enable `run in terminal' in the `advanced settings'of the gimp.desktop icon settings, the application does not crash anymore; At the cost of having a rather distracting console at the backgound; I cannot even type command  in it and it does not even show any STERR or STDOUT messages.

Firefox and Thunderbird however do still crash, upon opening the file dialog windows with a segmentation fault, when started from the commandshell.

Anybody have a clue to what goes wrong and preferrably also a structural solution/bugfix?

---

