---
title: "VLC won't be my Preferred Application"
date: 2010-07-06
forum: General Help
---

### Post by Dex73 on 2010-07-06
I can't seem to set VLC as my default media player.

I've been in System/Preferences/Preferred Applications/MultiMedia and selected custom and entered the command "VLC media player %s" I'm not sure this is right though.

I've also tried clicking on the videos and selecting Open with Other Application and chose VLC and clicked the remember option but Movie pops up when you open the file again?

Can anyone help me solve at least one of these problems that would bet great.

---

### Post by hhh on 2010-07-06
Drop media player from the command and don't capitalize vlc.

---

### Post by giddyup306 on 2010-07-06
Right click > open with other application > Remember this application...

---

### Post by Dex73 on 2010-07-06
I've entered "vlc %s" as the command now but Movie Player still comes up. Also still can't get it done via Open with Other Application yet either.

---

### Post by mc4man on 2010-07-06
For removable media go to File Management -> media
```
nautilus-file-management-properties
```

For file types right click on a file -> properties -> open with and set vlc there.
(once per filetype

---

### Post by hhh on 2010-07-06
> **Dex73 said:**
> I've entered "vlc %s" as the command now but Movie Player still comes up.
You need to log out at least or probably reboot for Ubuntu to set the new command.

---

### Post by piju on 2010-07-06
i got this problem too

then i do chown myusername.myusername ~/.local/share/applications/mimeapps.list

the error was the ownership of that file is default to root. not user.

---

### Post by Dex73 on 2010-07-07
Right clicking on the file and going to Properties worked for me.

I've also been to /usr/share/applications and it says the command for VLC is vlc %U. This might be why vlc %s didn't work.

Thanks for all the help!

---

### Post by renecschutte on 2010-08-15
Running Ubuntu 10.4 (Lucid) and none of the right-clicking or setting "preferred application" or setting Nautilus properties worked for me.

Editing the following file DID work though:
> .local/share/applications/mimeapps.listRun command:
> vim .local/share/applications/mimeapps.listPress > iThen paste the following for .wav files .avi or .mp4 files:
> x-content/video-dvd=vlc.desktop;
video/x-msvideo=vlc.desktop;totem.desktop;
video/x-ms-wmv=vlc.desktop;
video/mp4=vlc.desktop;Now press Escape-key and type:
> :wqDouble clicking on any .wav .wmv or .mp4 will open with VLC as the deafult player.

Hope this was helpful

---

### Post by Heero_Yuy_X on 2010-08-22
Very helpful thanks !

---

### Post by abramo.franchetti on 2010-11-02
It work for me:)

---

