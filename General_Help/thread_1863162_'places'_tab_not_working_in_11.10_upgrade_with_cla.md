---
title: "'places' tab not working in 11.10 upgrade with classic"
date: 2011-10-17
forum: General Help
---

### Post by tickle me gusta on 2011-10-17
Hello-
I recently ran the upgrade to 11.10. I prefer to use the ubuntu classic desktop, but when I do, I can't access any of my 'places'. When I click on any of my 'places' (like 'Home', for example), it opens up GNOME MPlayer and tells me "couldn't open DVD device: /dev/dvd (No Such File or Directory)". 

So far I have tried to fix this by manually installing the new GNOME 3 interface for classic, but still doesn't work in classic or classic - no effects.

Any advice would be hugely appreciated!

-Tickle

---

### Post by mc4man on 2011-10-17
run
```
gedit ~/.local/share/applications/mimeapps.list
```

There should be 2 sections [Default Applications]  & [Added Associations]
In the default section if there is a line inode/directory= 
then delete the line completely.

Or simply browse there & delete the mimeapps.list file - it will be recreated as needed in a proper manner

```
nautilus  ~/.local/share/applications/
```

(or post the contents - will adjust for you

---

### Post by tickle me gusta on 2011-10-17
Here are the contents:

[Added Associations]
inode/directory=gnome-mplayer.desktop;
x-content/video-dvd=vlc.desktop;
x-scheme-handler/http=chromium-browser.desktop;firefox.desktop;
x-scheme-handler/mailto=thunderbird.desktop;
text/calendar=gedit.desktop;
audio/x-vorbis+ogg=banshee.desktop;
video/x-ogm+ogg=totem.desktop;vlc.desktop;
image/jpeg=eog.desktop;
x-scheme-handler/https=firefox.desktop;

[Default Applications]
inode/directory=nautilus-folder-handler.desktop
text/html=chromium-browser.desktop
x-scheme-handler/http=chromium-browser.desktop
x-scheme-handler/https=chromium-browser.desktop
x-scheme-handler/about=chromium-browser.desktop
x-scheme-handler/unknown=chromium-browser.desktop
x-content/video-dvd=vlc.desktop
video/x-ogm+ogg=vlc.desktop

Do I just delete that first line after [Default Associations] and then save?

---

### Post by mc4man on 2011-10-17
delete this line marked in blue
[Default Applications]
[COLOR="Blue"]inode/directory=nautilus-folder-handler.desktop[/COLOR]

---

### Post by mc4man on 2011-10-17
not right

---

### Post by tickle me gusta on 2011-10-17
Thank you. That works!

---

