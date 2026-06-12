---
title: "Spotify links, xfce, google-chrome"
date: 2010-01-05
forum: General Help
---

### Post by LarsEriksson on 2010-01-05
I am trying to make spotify-links (i.e. spotify:user:user:playlist:7LDkc94b2wMVjyaIlcU ) clickable, and sent to spotify in google-chrome.

I have followed a couple of different guides i've found on google, but with no success.

As i have understood, google-chrome uses xdg-open, how do i configure that to work?

```
brasse@brasse-laptop:~$ xdg-open spotify:user:floppa:playlist:7LDkc94b2wMVjyNzlaIlcU
brasse@brasse-laptop:~$ A new window was created during the current browser session.
```

is all the results i get when i try to use xdg-open.
if i do the same with gnome-open it works great. (through a .sh-script: wine  "$HOME/.wine/drive_c/Program Files/Spotify/spotify.exe" /uri "$@")

---

### Post by rec53 on 2011-02-23
Hey,
I just came across this thread with the same problem. Although it doesn't really fix the cause, you said that gnome-open works. So one can do:

sudo ln -s /usr/bin/gnome-open /usr/local/bin/xdg-open

To hack around the problem if gnome is installed on the system too.

Hope it helps you/anyone else googling the problem ;)

---

