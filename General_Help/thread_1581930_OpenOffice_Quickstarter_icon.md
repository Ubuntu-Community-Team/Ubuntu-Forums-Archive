---
title: "OpenOffice Quickstarter icon"
date: 2010-09-25
forum: General Help
---

### Post by brucehohl on 2010-09-25
The OpenOffice Quickstarter icon in the system tray for Ubuntu 10.04 is an old image and does not fit in with the default theme (light grey background). In fact, the same icon used for the Windows version is at  /usr/share/icons/hicolor/32x32/apps/openofficeorg3-startcenter.png

Does anyone know where the quickstarter getting this misfitting icon? Perhaps I could simply copy the icon above to the location and file name used by quickstarter.

---

### Post by nagaprathyush on 2010-09-25
try right clicking that icon to open the properities dialog box and then click the image on the left side of that dialog box...to open the folder where the icons are stored! Hope, that helps....

---

### Post by luceerose on 2010-09-25
The light grey background on the office quickstarter is due to a well known bug with the way the gnome panel retrieves it's colors from the current theme.
I investigated this about a year ago & then again a few weeks ago.
I've never found a workaround.

---

### Post by brucehohl on 2010-09-27
nagaprathyush,
For this systray icon, right or left clicking does not provide a "Properties" choice.

larsenguitars,
I am aware of that bug. I was hoping to work around that bug by replacing the image file used by OpenOffice Quickstarter with an image file that fits better with the default theme and uses the current Quickstarter image. I could not locate the image file currently used by OpenOffice Quickstarter.

Does anyone have any idea where this image file might be located or how to find it?

---

### Post by Avoozl on 2010-10-10
If anyone finds the answer to replacing this icon please share.  It's really bugging me.

Edit: Finally found a fix after googling around again (I've looked before and come up with nothing).

I still haven't found how to replace the icon, but if you want to fix the incorrect rendering of the icon you can update gnome panel from a ppa as suggested here, at your own risk of course:

[https://lists.ubuntu.com/archives/ubuntu-mono/2010-June/024001.html](https://lists.ubuntu.com/archives/ubuntu-mono/2010-June/024001.html)

---

