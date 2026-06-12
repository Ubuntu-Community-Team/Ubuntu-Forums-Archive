---
title: "Folder Icons Won't Change"
date: 2009-11-05
forum: General Help
---

### Post by anberside on 2009-11-05
i'm using ubuntu 9.10. I tried to change the documents, downloads, etc. folders by just changing the icons for other pictures. Now when i try to switch themes the folders are just icons of white pieces of paper. They will not change with the theme. 

I hope i explained this well enough! Thanks for any help!

---

### Post by iruel on 2009-11-05
it's because "**glib**" which has *xdg*, and some *xdg* function search for the icons where the icons has been included by icon theme on Appearances. usually the icon resides on *_places_* directory
ie the structure of Human icon
-Human
--16x16
---places
--24x24
---places
--scalable
---places

and xdg search the icon name same as the xdg variable,you can found this declaration config on** /home/yourhome/.config/user-dirs.dirs**
it would be like this

```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

where** XDG_DOWNLOAD_DIR** will search for the icon named **folder-download.***
and **XDG_DOCUMENTS_DIR** will search for the icon named **folder-documents.***

so if you want to add some icons just renamed to **folder-XXXXX**

or you can delete the XDG line;)
HTH

---

### Post by anberside on 2009-11-05
thanks for replying :) 

although, i have all the XDG lines in my user-dirs.dirs file. do i rename them to something else? the folders under my icon themes are all still there.

---

### Post by iruel on 2009-11-06
you can put "**#**" as commented line it's more safe than you rename it or remove it.

---

### Post by carlosdark54 on 2009-11-30
> **anberside said:**
> thanks for replying :) 

although, i have all the XDG lines in my user-dirs.dirs file. do i rename them to something else? the folders under my icon themes are all still there.

Hi friend, I've just discovered how to fix the issue,

Left click the folder you want to restore, then Properties > Click on the button to change the icon.

Up to this step is the ussual way to change an icon. BUT if you look carefully the window has three buttons, 
<Open> <Cancel> <Reverse or Restore>
(I'm using ubuntu in spanish) and click this last button and voilá.
Everythings has just come back to normal.

See the attachment to have a better look

---

### Post by raktarok on 2009-11-30
@carlosdark54
This is not related to this thread at all, but can I know which theme you are using? The screenshot looks good, and I want a theme like that too! :)

---

### Post by michael18 on 2009-12-08
guys...i'm having this problem oso..=(
and this time is the 1st time i'm using a LINUX OS...the Ubuntu 9.10 Karmic Koala
now even i change themes, the folder icon also never change at all...
so wat can i do now?
i saw the reply at above..but i does not understand what was that...
please help...
i'll be appreciate that..
thanks...

---

