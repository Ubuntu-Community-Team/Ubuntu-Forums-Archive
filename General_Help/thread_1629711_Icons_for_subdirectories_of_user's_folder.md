---
title: "Icons for subdirectories of user's folder?"
date: 2010-11-24
forum: General Help
---

### Post by K25125 on 2010-11-24
Today, I figured I'd try out the Ubuntu Minimal install; I liked the concept of minimal distros like Arch-Linux (with a what-you-need-is-what-you-get type of system), but I really liked the community and general support of Ubuntu. Anyway, everything went fine after I got GRUB working properly, up to the point when I found that there were no subdirectories in my user's folder (Templates, Documents, Videos, etc). So, I just decided to create the folders I needed. However, there were two issues I came across when doing this:

[LIST=1]
[*]The items in the 'Templates' folder don't show up in the context menu like they should
[*]More importantly, the icons for each folder would have to be manually changed for every new icon theme (if I wanted to use a new icon theme, I would have to navigate to the theme's folder every time for each icon I wanted changed)
[/LIST]

I'm not too concerned with the templates at the moment, but I was wondering how I would make these icons dependent on the current icon theme. Is there some package I missed installing?

By the way, if it makes a difference, I'm trying to set up the default Humanity icon set (well, not default for me, since I'm using Ubuntu Minimal). Also, sorry if this question has been posted before (or if I find the solution immediately after posting, which almost always happens to me), I didn't know exactly what to search for... and thanks in advance!

(I'm really glad I switched from Windows :D)

---

### Post by mcduck on 2010-11-24
Check *~/.local/user-dirs.dirs* -file and make sure it has contents like this:

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

If that doesn't work, I believe the package that makes this work is called *xdg-user-dirs*. And of course if this works at all or not depends on what file manager you are using.

---

### Post by K25125 on 2010-11-24
> **mcduck said:**
> Check *~/.local/user-dirs.dirs* -file and make sure it has contents like this:

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

If that doesn't work, I believe the package that makes this work is called *xdg-user-dirs*. And of course if this works at all or not depends on what file manager you are using.

That was the package I was missing... and I got my Templates back! Thanks for your help!

---

