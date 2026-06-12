---
title: "How is the personal folder created?"
date: 2011-06-05
forum: General Help
---

### Post by rozbuntu on 2011-06-05
Hello,

Does anyone now where the personal folder is created from?
Particulary i mean how do the folders Documents,Downloads,Pictures etc.. get created?

Is there a config file where this is arranged in?

Thanx a lot.

---

### Post by linuxinstalledfromhdd on 2011-06-05
I would like to know this as well. I've done clones of my system where, mysteriously there are no personal directories after reinstalling the cloned system. 

:popcorn:

---

### Post by Mr. Shannon on 2011-06-05
> Is there a config file where this is arranged in?

Yes and no.  

On Ubuntu all of this is done automaticaly but if somthing happend and you need to restore them then you just create the folders like any other folders and then open the file
```
/home/yourusername/.config/user-dirs.dirs
```
In that file is some code specifying the special directories.  If yours has been changed and you want to change it back, the defualt code is below.  Note: You will need to restart before the changes take effect.  Note: You need to have xdg-user-dirs installed for this to work.
```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

---

### Post by rozbuntu on 2011-06-05
Okay thanx! I will put a comment on my progress with this thing later.

---

