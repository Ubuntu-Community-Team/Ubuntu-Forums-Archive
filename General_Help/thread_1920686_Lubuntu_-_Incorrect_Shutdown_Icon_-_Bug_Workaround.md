---
title: "Lubuntu - Incorrect Shutdown Icon - Bug Workaround"
date: 2012-02-05
forum: General Help
---

### Post by 2CV67 on 2012-02-05
Using Oxygen Icon theme in Lubuntu, I expected the Shutdown Button to be the Red one like "/usr/share/icons/oxygen/16x16/system-shutdown.png".

Instead, I just had a dull grey cogwheel, which I suppose is a default when no icon is found.

I located the   .desktop   file which is associated with this button  -   "lubuntu-logout.desktop" .
It is at /usr/share/applications/Shutdown, but there are several other files there with the same Label of "Shutdown"  -  you have to open them to find the right one with "lubuntu-logout.desktop" in the title bar.
It includes the line:   "Icon=system-shutdown-panel".
But oxygen theme (and many other themes) do not include a   "sytem-shutdown-panel"   icon...

I fixed my problem by changing the icon line in lubuntu-logout.desktop file to  "Icon=system-shutdown".

Now I have the right red icon.  :cool:

The revised  .desktop  file looks like the screenshot.

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/lubuntu-logoutdesktop.png[/IMG]

I think I have opened a bug report in Launchpad on this subject, but that was much more difficult that fixing the problem...
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/926560](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/926560)

---

### Post by 2CV67 on 2012-08-19
After upgrading to 12.04, my shutdown button was back to the grey cogwheel.

Repeating the previous method fixed it again.

Is there a more intuitive solution?

---

