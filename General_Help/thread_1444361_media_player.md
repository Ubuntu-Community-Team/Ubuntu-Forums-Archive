---
title: "media player"
date: 2010-04-01
forum: General Help
---

### Post by nischalinn on 2010-04-01
My default media player for** ".wmv" & "avi"** files is *_**VLC**_*. I want to make **VLC** as a default media player for_** ".flv", "mp3" & "m4a" **_files.

How can I do that?

---

### Post by Nisal on 2010-04-01
go to file properties nd set open with VLC

---

### Post by nischalinn on 2010-04-01
will You please elaborate your reply.

---

### Post by sky net on 2010-04-01
You need to edit the /etc/mime.types to match extensions with programs.  You can do this with sudo gedit /etc/mime.types

>    Open mime.types:    sudo gedit /etc/mime.types
>    Search for file extension:    <ctrl+f> &#8220;file type&#8221;
>    Copy Mimetype
>    Create a backup of defaults.list:    sudo cp  /usr/share/applications/defaults.list  /usr/share/applications/defaults.list.backup
>    Open defaults.list:    sudo gedit  /usr/share/applications/defaults.list
>    Search for Mimetype:    <ctrl+f> <ctrl+v>           (mimetype should still be on your clipboard)
>    List available applications:    ls /usr/share/applications/*.desktop
>    Change default application or Mimetype in the form     [mime-type]=[new-app].desktop
>    Save mime.types
>    Restart nautilus: killall nautilus

further info :
[http://ubuntuforums.org/showthread.php?t=606128](http://ubuntuforums.org/showthread.php?t=606128)
[http://ubuntuforums.org/showthread.php?t=654320](http://ubuntuforums.org/showthread.php?t=654320)   << this one is the best !!

---

### Post by cjhabs on 2010-04-01
> **sky net said:**
> You need to edit the /etc/mime.types to match extensions with programs.  You can do this with sudo gedit /etc/mime.types

>    Open mime.types:    sudo gedit /etc/mime.types
>    Search for file extension:    <ctrl+f> “file type”
>    Copy Mimetype
>    Create a backup of defaults.list:    sudo cp  /usr/share/applications/defaults.list  /usr/share/applications/defaults.list.backup
>    Open defaults.list:    sudo gedit  /usr/share/applications/defaults.list
>    Search for Mimetype:    <ctrl+f> <ctrl+v>           (mimetype should still be on your clipboard)
>    List available applications:    ls /usr/share/applications/*.desktop
>    Change default application or Mimetype in the form     [mime-type]=[new-app].desktop
>    Save mime.types
>    Restart nautilus: killall nautilus

further info :
[http://ubuntuforums.org/showthread.php?t=606128](http://ubuntuforums.org/showthread.php?t=606128)
[http://ubuntuforums.org/showthread.php?t=654320](http://ubuntuforums.org/showthread.php?t=654320)   << this one is the best !!

Or you can select a file of that type, right click and select "Properties -> Open with" and add/remove the apps you want available to open with - this will update this for all files with that extension.

---

