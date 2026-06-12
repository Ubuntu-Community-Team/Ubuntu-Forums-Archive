---
title: "Spotify icon"
date: 2010-05-06
forum: General Help
---

### Post by mo79 on 2010-05-06
I've installed Wine and Spotify in UNE 10.04 and everything's fine, but how can I get an icon into one of the app category tabs?

Also, when [this page]("http://www.spotify.com/uk/help/faq/wine/") references a script for 'Opening spotify URIs from browsers' can I alternatively just enter those lines into Terminal?

---

### Post by kostkon on 2010-05-06
> **mo79 said:**
> I've installed Wine and Spotify in UNE 10.04 and everything's fine, but how can I get an icon into one of the app category tabs?
I suppose you need to create a new menu item. For *command* you can put something like this:
```
env WINEPREFIX="/home/xxxxx/.wine" wine "C:\Program Files\Spotify\spotify.exe"
```
Also, you can use this icon [here]("http://ncrow.deviantart.com/art/Icon-Spotify-139521172").
> **mo79 said:**
> Also, when [this page]("http://www.spotify.com/uk/help/faq/wine/") references a script for 'Opening spotify URIs from browsers' can I alternatively just enter those lines into Terminal?
My version of the script is this:
```
#!/bin/sh

cd "/home/xxxxx/.wine/drive_c/Program Files/Spotify";
wine "spotify.exe" /uri "$1";
```

---

### Post by mo79 on 2010-05-07
Cheers, I'll give that a go.

---

