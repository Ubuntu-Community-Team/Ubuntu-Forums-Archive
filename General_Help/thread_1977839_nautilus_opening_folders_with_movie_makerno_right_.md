---
title: "nautilus opening folders with movie maker/no right click"
date: 2012-05-10
forum: General Help
---

### Post by medusa569 on 2012-05-10
Like some other whenever I open nautilus from the panel all the folders will open with windows movie player. Ubuntu tweak has the correct file associations . After reading other posts I see that  right clicking on the folders or file will bring up an option but I don't get that..right clicking ALSo opens movie player. I reinstalled nautilus but that didn't correct the problem.   HELP.

---

### Post by mc4man on 2012-05-10
```
gedit ~/.local/share/applications/mimeapps.list
```
post the contents, likely easy to fix

---

### Post by medusa569 on 2012-05-12
> **mc4man said:**
> ```
gedit ~/.local/share/applications/mimeapps.list
```post the contents, likely easy to fix



results to command as listed......


[Added Associations]
x-content/audio-cdda=rhythmbox.desktop;
x-content/video-dvd=totem.desktop;
x-content/audio-player=rhythmbox.desktop;
x-content/image-dcf=shotwell.desktop;
text/html=icecat.desktop;
application/xml=openoffice.org-calc.desktop;
application/x-extension-002=rhythmbox.desktop;
message/rfc822=icecat.desktop;
video/x-msvideo=vlc.desktop;
x-content/blank-dvd=kde4-k3b.desktop;
application/x-ms-dos-executable=wine.desktop;virtualbox.desktop;wine-extension-htm.desktop;
audio/x-wav=rhythmbox.desktop;gnome-media-player.desktop;
application/x-cda=gnome-media-player.desktop;
image/jpeg=eog.desktop;wine-extension-pic.desktop;
application/x-extension-config=wine-extension-ini.desktop;
video/x-ms-wmv=gnome-mplayer.desktop;
audio/midi=gnome-mplayer.desktop;
video/mpeg=vlc.desktop;
application/x-rpm=file-roller.desktop;
application/pdf=evince.desktop;gimp.desktop;
application/x-trash=wine-extension-ini.desktop;
application/x-extension-drive=nautilus-browser.desktop;totem.desktop;
x-content/audio-dvd=rhythmbox.desktop;
inode/directory=totem.desktop;
application/zip=file-roller.desktop;mount-archive.desktop;userapp-unzip-U7OPDW.desktop;

[Removed Associations]
application/x-extension-drive=pcmanfm.desktop;

---

