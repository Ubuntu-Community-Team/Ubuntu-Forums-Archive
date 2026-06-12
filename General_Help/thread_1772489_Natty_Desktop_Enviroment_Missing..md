---
title: "Natty Desktop Enviroment Missing."
date: 2011-05-31
forum: General Help
---

### Post by haveguitarwilltravel on 2011-05-31
So I installed the 32-bit natty image on my old IBM ThinkPad laptop, CD works fine, natty start up asks me to login just normally then when I login I get a few errors, my desktop background but no toolbars or anything I can click, by luck some setup option popping up gave me a terminal but I have no idea how I could use the terminal to fix this.


Errors Include:

"Could not update ICEauthority file /home/acedelgado/.ICEauthority"

"There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

"It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using traditional environment."

NOTE: I have tried Ubuntu Classic Environment and still get pretty much the same errors and can only see my desktop background, nothing else.

"Nautilus could not create the following required folders: /home/acedelgado/Desktop, /homo/acedelgado/.nautilus.

Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."

Any help with this problem would be much appreciated.

Thanks,
-haveguitarwilltravel

---

### Post by fwpost on 2011-06-06
Hello, and thanks in advance.

From a freshly installed 32-bit Natty on a Pentium-D 4GB RAM machine, this morning the aforementioned errors keep popping up when i try to log in using GDM, the graphic login-screen.

Switching to the console (Ctrl + Alt + F1) and logging in, works perfectly. Logging in remotely via ssh, too.

Could somebody help us resolve this issue?

Thanks, once again,


EDIT:
Reinstalling gnome-panel seems to fix this issue, as proposed in this thread:
[http://ubuntuforums.org/showthread.php?t=13076]("http://ubuntuforums.org/showthread.php?t=13076")



FWieP

---

