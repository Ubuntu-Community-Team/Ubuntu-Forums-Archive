---
title: "GUI restore"
date: 2011-03-31
forum: General Help
---

### Post by Arpayon on 2011-03-31
Hi,
Let me reassume what I just did, because it will be easier for you to understand my problem.
Today I played a bit with my Ubuntu (10.04, latest kernel) because I wanted to try xmms. I tried to install it manually, but since i couldn't make some libraries work I went for
```
sudo apt-get install xmms2
```
After that I realized that i didn't need it and I could simply use VLC, so i first
```
sudo apt-get remove xmms2
```
and then
```
sudo apt-get autoremove
```
cause there were packages left.
Then I tried to make VLC enqueue as default action, but since that function is bugged I used this miniguide [http://ubuntuforums.org/showthread.php?t=1100766](http://ubuntuforums.org/showthread.php?t=1100766)
and added this line to the "open with" tab choices.
```
vlc --started-from-file --playlist-enqueue
```

I don't know where something went wrong, but when i rebooted my GUI disappeared. I'm stuck in login screen with nothing in there.
I tried to do this [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/) , but it doesn't work (if i'm not wrong those folders are inside /home, so after login I have to do [cd ..] and then using the rm command)
I tried also 
```
pkill gnome-panel
``` 
before coming back to desktop, but it doesn't work either.
I tried to 
```
sudo apt-get install ubuntu-desktop
```
but it says I've got the latest one already installed.

Any idea?

---

### Post by Smart Viking on 2011-03-31
Try
```
startx
```

---

### Post by Arpayon on 2011-03-31
Edit of my first post: the cd.. before removing .gnome .gnome2 etc. was wrong, i removed them from the right directory now

Tried startx:
```
Fatal server error
server is already active for display 0
   if this server is no longer running, remove /tmp/.X0-lock and start again

Please consult... for help

ddxsiggiveup: closing log

invalid mit-magic-cookie-1 key giving up.
xinit: resource temporary unavaible (errno 11): unable to connect to X server
xinit: no such process (errno 3): server error

```

Should i rm /tmp/.X0-lock?

---

### Post by Smart Viking on 2011-03-31
Press
<ctrl>+<alt>+<F7>
and
<ctrl>+<alt>+<F8>

See if that gets you anywhere

---

### Post by Arpayon on 2011-03-31
ctrl+alt+f7 > starting screen, only my cursor
ctrl+alt+f8 > black screen with flashing writing cursor (I don't know his actual name, that horizontal bar that flashes in the position where you can write something)

---

