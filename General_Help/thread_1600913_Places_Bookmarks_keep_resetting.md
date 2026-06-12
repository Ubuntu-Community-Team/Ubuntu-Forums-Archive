---
title: "Places Bookmarks keep resetting"
date: 2010-10-19
forum: General Help
---

### Post by okayneil on 2010-10-19
A simple and small problem but annoying all the same...

I don't like having the downloads/pictures etc bookmarks in the places menu so I remove them but every time I restart my machine they come back. 

Any way to fix this?

---

### Post by okayneil on 2010-10-19
Bump :)

---

### Post by okayneil on 2010-10-19
Yikes, bump!

---

### Post by okayneil on 2010-10-20
Bump Again!

---

### Post by okayneil on 2010-10-22
Bump

---

### Post by okayneil on 2010-10-25
Bump

---

### Post by okayneil on 2010-11-03
Bump

---

### Post by braikar on 2011-03-13
I've posted a solution in: [http://ubuntuforums.org/showthread.php?p=10555600#post10555600](http://ubuntuforums.org/showthread.php?p=10555600#post10555600)

> 
The solution is in /home/user/.config/user-dirs.dirs !

By default it looks something like:
Code:

XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOWNLOAD_DIR="$HOME/Download"
XDG_MUSIC_DIR="$HOME/Music"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PICTURES_DIR="$HOME/Pictures"

change it to:
Code:

XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"

And on the next reboot the bookmarks won't reappear.
But one tiny problem with that is that programs that by default use these folders declarations, might need to modified to point to the correct directory, but it's not really annoying to change..

If you notice a program for example that deals with videos and dumps all the videos in /home/user/ (because that's now where the video folder is defined), just go and change the location of that dir manually...


---

