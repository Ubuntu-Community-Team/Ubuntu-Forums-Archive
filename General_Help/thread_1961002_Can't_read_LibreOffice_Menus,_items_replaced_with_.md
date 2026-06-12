---
title: "Can't read LibreOffice Menus, items replaced with dashes"
date: 2012-04-18
forum: General Help
---

### Post by Pragu on 2012-04-18
Hi there, i'm running xubuntu 11.10 and I've come across something of a problem with LibreOffice 3.5. The drop down menus (file, edit, view, format, etc) have all of the items there, but the names are replaced with dashes of varying length. I don't think it has anything to do with my theme (xfce-dusk) because I have tried other themes with no change. I have tried increasing and decreasing the default font size for the system, and I have tried increasing the GUI zoom from the LibreOffice preferences (which I know is the last item on the tools menu) to no avail.
What else can I do? Is there a way to reset LibreOffice?

---

### Post by philinux on 2012-04-18
Try changing your theme back to the default.

---

### Post by Pragu on 2012-04-18
I've tried and it doesn't affect the issue. They're still dashes in the menu, just on a white background.

---

### Post by kohoutek1 on 2012-04-30
I am getting the same problem here, in Ubuntu 12.04.

See this thread: [http://ubuntuforums.org/showthread.php?t=1968595](http://ubuntuforums.org/showthread.php?t=1968595)

I have posted a bug report on Launchpad Here: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/991574](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/991574)

Please go to that link and report that the bug affects you so that they might place higher priority on it.

Thanks.

---

### Post by rmartinez79 on 2012-05-23
Using Ubuntu 12.04 + XFCE4.10 (from ppa).
I also had this issue.
FIXED (sort off): The menu became visible when I disabled display compositing. (Main Menu -> Settings -> Settings Manager -> Window Manager Tweaks -> Compositor -> Enable display compositing).

---

### Post by kotek on 2012-06-10
Another "sort of" solution: in ubuntu-tweak changing the default font (ubuntu) to some other ones (best seems to be Nimbus Sans) displays almost all the menus back...

---

### Post by Seaban on 2012-07-05
> **kotek said:**
> Another "sort of" solution: in ubuntu-tweak changing the default font (ubuntu) to some other ones (best seems to be Nimbus Sans) displays almost all the menus back...
Hi I have tried this and the previous idea with little success.  If I tweak the font down to 4 or 5 pt i can see all the menus but cannot read them!!!! Has anyone come up with any other solution?

---

### Post by LinuxNubian on 2012-10-03
I recently installed Ubuntu 12.04 and experienced the same issue. I tried some of the settings tweaks to no avail. However, I found some love by doing the following:

1. uninstalled all libreoffice packages with Synaptic Package Manager,

2. downloaded the Main Installer and the LibreOffice built-in help from [http://www.libreoffice.org/download/](http://www.libreoffice.org/download/) ,

3. extracted the compressed packages and

4. followed the instruction in the "readmes"

All menus items are now legible :-)

hope this helps

---

### Post by tlee on 2012-10-23
This worked for me.  Thanks!

---

