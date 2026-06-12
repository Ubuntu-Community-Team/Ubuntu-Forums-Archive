---
title: "default 9.10 icon quesiton"
date: 2009-12-12
forum: General Help
---

### Post by brandon88tube on 2009-12-12
I wanted to know what file determines what icons to use for the home,user,Downloads,Music,etc. folders. Right now none of the usr/share/icons are being used for such folder and they just appear as normal ones.

---

### Post by brandon88tube on 2009-12-13
Anyone>>>?

---

### Post by brandon88tube on 2009-12-14
I know its not really a big issue or anything, but it still would be nice to know.

---

### Post by brandon88tube on 2009-12-30
I found the answer myself. To get the new icons for folders such as Downloads, Videos etc. you need to have a file called user-dirs.dirs in your .config folder. That file should contain something similar to this.
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

