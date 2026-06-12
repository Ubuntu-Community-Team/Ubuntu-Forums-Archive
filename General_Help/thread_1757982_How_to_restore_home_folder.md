---
title: "How to restore home folder"
date: 2011-05-14
forum: General Help
---

### Post by Scott Deagan on 2011-05-14
I followed this guide: 

[http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html)

to customize my launcher. When I tried to add an smb share, my home folder disappeared from the launcher, as did my /usr/share/applications/nautilus-home.desktop file.

I can't get my nautilus-home.desktop file working again. I have replaced it with:

[Desktop Entry]

Name=Home Folder
Comment=Open your personal folder
TryExec=nautilus
Exec=nautilus --no-desktop
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;Unity;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=nautilus

but it has no effect. When I sign out of Ubuntu and sign back in, the Home Folder icon is still missing from the Unity Launcher. I realize I can open Nautilus and then right-click it and select "Keep in Launcher", but this would not enable me to add the customizations I want from the link above.

I have also tried "unity --reset" and "unity --reset-icons", but this doesn't return my default home folder to the launcher.

How can I restore my original home folder to the launcher?

---

### Post by r-senior on 2011-05-14
Did you copy the .desktop file to ~/.local/share/applications?

It could be that your edits weren't exactly right. I've done a couple of these quicklists and it needs to be absolutely spot on otherwise you get grief. Nautilus is perhaps the most awkward to get right because of the way it integrates with the desktop.

You could try:

a. Rename the Nautilus .desktop file in ~/.local/share/applications (e.g. to my-nautilus-home.desktop), run Nautilus and try and pin it to the launcher.

b. Drag the nautilus-home.desktop file from /usr/share/applications (using Nautilus) to the launcher.

---

### Post by Scott Deagan on 2011-05-14
Thanks r-senior, that did the trick! My Unity universe is now complete :)

---

