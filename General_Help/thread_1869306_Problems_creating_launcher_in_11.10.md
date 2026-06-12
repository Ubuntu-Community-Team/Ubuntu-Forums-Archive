---
title: "Problems creating launcher in 11.10"
date: 2011-10-25
forum: General Help
---

### Post by jelliott1910 on 2011-10-25
I'm upgrading from 10.04, where I would right click on the desktop to create a launcher for Eclipse. That isn't available in 11.10, so I clicked on the executable for Eclipse in Nautilus. This starts Eclipse and creates an icon with a question mark in the launcher bar on the left (not sure of the terminology, so I'll call it a launcher bar).

I right click on the icon and click "keep in launcher". When I close Eclipse the question mark icon stays in the launcher bar. But when I click on the icon to start Eclipse again, it oscillates in color for about 10 seconds, but Eclipse doesn't launch.

Is there a way to create a launcher for frequently used programs? And is there a way to assign an icon image to it?

Thanks,
Joe

---

### Post by JRV on 2011-10-25
Welcome aboard.

The program you want might already have a launcher in /usr/share/applications.
Open the dash and look for it, start the program and the icon will appear in the launcher bar.  Right click the icon and check "Keep in Launcher".

IF it is not there try this:

Create a blank file on your desktop and copy this template into it.
Name it what you want it to be called.

```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=administration
Name[en_US]="THIS IS WHAT WILL APPEAR IN THE LAUNCHER, NO QUOTES"
Exec="FULL PATH TO PROGRAM, NO QUOTES"
Name="THIS SHOULD BE THE SAME AS Name[en_US] ABOVE"
Icon=administration

```

Both name fields should be edited to the same thing you named the file.

When you are finished editing add ".desktop" to the name and make it executable.

Now you can right click the icon and change the icon and the Exec.

Test it, copy it where you want to keep it.
(The standard place is ~/.local/share/applications.)
Then drag it to the launcher bar.

For more information on .desktop files read my tutorial and the threads listed at the bottom.

[http://ubuntuforums.org/showthread.php?t=1857589](http://ubuntuforums.org/showthread.php?t=1857589)

---

### Post by jelliott1910 on 2011-10-25
Thanks, JRV, I'm getting closer, but I'm still having problems with the launcher. I can create the script and change the icon and it works from the desktop. I also put it in ~/.local/share/applications. 

However, I've been experiencing two problems:

**1) Instead of the Eclipse icon, there is a screwdriver and wrench icon:**
When I go to look in the Applications menu, my Eclipse application has a screwdriver and wrench icon. If double click on my Eclipse icon, Eclipse launches, but has the screwdriver/wrench icon in the launcher.

**2) Strange results when I try to drag and drop my Eclipse application in the launcher:**
 If I try to drag my Eclipse icon to the launcher as you mentioned, a bubble will come up saying "Drop to add application". But at times I get different results. It either won't "stay" if I try to drop it, or other times it creates a new spot in the launcher without any icon at all. I can right click on this area that has no icon to unselect "Keep in launcher".

Not sure where to go from here.
Thanks,
Joe

---

### Post by JRV on 2011-10-26
Right click on the icon in ~/.local/share/applications
Select Properties
Right click on the icon to change it, icons are in /user/share/icons.

Double click on the icon in ~/.local/share/applications to open the program.
Right click on the icon in the launcher bar and select "Keep in Launcher".

---

### Post by jelliott1910 on 2011-10-26
Thanks, JRV
I've had no problem assigning the icon. But when I launch the app from  ~/.local/share/applications, the icon in the launcher (vertical bar on left) is the hammer/screwdriver icon, not the eclipse icon I see in Nautilus in  ~/.local/share/applications.
-Joe

---

