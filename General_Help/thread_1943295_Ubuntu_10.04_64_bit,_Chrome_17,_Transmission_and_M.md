---
title: "Ubuntu 10.04 64 bit, Chrome 17, Transmission and Magnet links"
date: 2012-03-19
forum: General Help
---

### Post by TMachado on 2012-03-19
I have transmission installed (by default) and ktorrent, but none of them are "prompted" when I "accept" the magnet link - I want transmission to start but I also would like to know how to change it for ktorrent (for example).


How can I do that?

---

### Post by andrew.46 on 2012-03-19
The preference can be stored here:

```
gedit ~/.local/share/applications/mimeapps.list 
```

You should see something like the following for Transmission:

```

[Default Applications]
x-scheme-handler/magnet=userapp-transmission-gtk-XVPPBW.desktop

```

Just be a little careful editing this file, make a backup copy first :).

---

### Post by TMachado on 2012-03-20
> **andrew.46 said:**
> The preference can be stored here:

```
gedit ~/.local/share/applications/mimeapps.list 
```

You should see something like the following for Transmission:

```

[Default Applications]
x-scheme-handler/magnet=userapp-transmission-gtk-XVPPBW.desktop

```

Just be a little careful editing this file, make a backup copy first :).

Thanks for your reply.

In fact the only content I have on that file is 

[Default Applications]
text/html=google-chrome.desktop

I added the line above but still don't work. Nothing happens when I "launch application".

---

### Post by andrew.46 on 2012-03-20
Mind you I have a slightly non-standard Transmission. Perhaps the following will be enough:

```
x-scheme-handler/magnet=transmission-gtk.desktop
```

---

### Post by TMachado on 2012-04-03
> **andrew.46 said:**
> Mind you I have a slightly non-standard Transmission. Perhaps the following will be enough:

```
x-scheme-handler/magnet=transmission-gtk.desktop
```

It works, thanks :)

---

### Post by andrew.46 on 2012-04-03
Great news :)

---

### Post by rudecam on 2012-05-05
what would the code line look like in the case of vuze as a torrent client?

---

