---
title: "Ubuntu 10.04 won't remember application choice"
date: 2010-07-27
forum: General Help
---

### Post by Morientes on 2010-07-27
I want VLC to be the default media player in my Ubuntu 10.04 installation. However, even though I right click on a media file and select it to open with VLC and ticks the "Remember this application for ..." box, files of this type still keep opening in the "Movie Player" application. It seems the "Remember this application for ..." box has no effect what-so-ever. Anyone know what might be wrong? Some configuration file somewhere that I don't have the right to or something?

---

### Post by mcduck on 2010-07-27
To set the default application for a file type you must right-click the file, select Properties  and there, under the Open With-tab you can select the application.

If you just right-click and choose Open With you are only selecting the application to use that time, not the default.

I don't remember there even being an "Remember this application"-option in that dialog, unless you are opening the file from Firefox (in which case it's of course completely different thing, as you are changing Firefox's options, not Gnome's).

---

### Post by Morientes on 2010-07-27
Thank you for the reply. The open-with under properties works. However, my method should also work. There IS an option called "Remember this application for ..." I am not making that up. For me, however, it's not working.

---

### Post by renecschutte on 2010-08-15
I had similar problems and unfortunately had to go the manual route:

Running Ubuntu 10.4 (Lucid) and none of the right-clicking or setting  "preferred application" or setting Nautilus properties worked for me.

Editing the following file DID work though:
> .local/share/applications/mimeapps.list

Run command:
> vim .local/share/applications/mimeapps.list

Press  > i

Then paste the following for .wav files .avi or .mp4  files:

> x-content/video-dvd=vlc.desktop;
video/x-msvideo=vlc.desktop;totem.desktop;
video/x-ms-wmv=vlc.desktop;
video/mp4=vlc.desktop;Now press Escape-key and type:
> :wq

Double clicking on any .wav .wmv or .mp4 will open  with VLC as the deafult player.

Hope this was helpful

---

### Post by alambpencil on 2011-11-21
HI, also having this issue with VLC.
How would I go about setting it as the default for .mkv files?
TYIA
alambpencil

---

