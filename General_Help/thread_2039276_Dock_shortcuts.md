---
title: "Dock shortcuts"
date: 2012-08-08
forum: General Help
---

### Post by Toriam on 2012-08-08
I recently clean installed Xubuntu 12.4 and several weeks after installation a problem pops up. I use the included dock. I've added several launchers. Every time I reboot the netbook that this is happening on, the new launchers show up as a black screen with a red no symbol on them, and won't launch anything. Attached is an image of the dock as it was this morning when it started up. I'm using standard launchers of one program per launcher. It started when I put a launcher for the browser chromium on the dock.

The dock is listed as xfce4-panel 4.8.6 in about.
If I need to pull up a log I need specific info on how to find it.

---

### Post by Bigtime_Scrub on 2012-08-08
How did you add those short cuts? It sound like there is no command for them to use. Can you launch any other default app from the dock? If you can, then what you added is most likely an empty launcher. You would have to configure it yourself by adding the name, command, and icon or by drag and drop to the dock itself.

---

### Post by Toriam on 2012-08-08
Hello fellow texan!
I did add the command. Im familliar with adding items to the dock and did it by right clicking on the panel, going to add launcher the filling in the blanks. The command auto fills when I beging typing in the name of the app. Here is what I get when adding the launcher. It'll stay like this panel pic untill I reboot. 2 pics attached.

---

### Post by black veils on 2012-08-08
do you do paths to every app in the command section?

the commands would be like this, usually:

firefox

pidgin

thunar

etc

---

### Post by Toriam on 2012-08-08
In the command section, things look like this:
audacity %F
/usr/bin/chromium-browser %U (I changed this to run in terminal and it didn't make any difference)
Those are two that dissapear. Ones that stay are :
libreoffice --writer %U
clipit

I'll try and change them to simply the name of the app and see how that works out.

---

### Post by Toriam on 2012-08-08
Nope, the launcher for chromium disapeared again after the name change and a restart. I thought to right-click where the launcher used to be, and go to properties, and it said nothing to indicate I ever specified the launcher was meant to start a certian app. Oh, minor frustrations! The one for audacity I just created in my last session did the same thing. libreoffice and clipit are still sitting where I put them. I mentioned those apps because they're ones I added. And none of the apps already on the panel that I deleted have reapeared. This indicates that  somethine I add isn't 'sticking' after a certian point. And I haven't gone and changed anything in preferences or with a script or something in the file system.
I did just go in and find the specific launcer for that 'space' and included a pic below. It had 4 instances for chromium, and I deleted 3 to make it like the others. I'll restart and see what happens.

---

### Post by Toriam on 2012-08-08
Here's the contents of launcher-20

---

### Post by Toriam on 2012-08-09
bumpercars?:confused:

---

### Post by Toriam on 2012-08-11
:( :confused:

---

