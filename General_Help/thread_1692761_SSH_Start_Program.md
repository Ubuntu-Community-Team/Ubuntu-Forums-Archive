---
title: "SSH Start Program"
date: 2011-02-21
forum: General Help
---

### Post by bmdsherman on 2011-02-21
Is there a way to start a program via ssh?

I have a SSH app on my android phone and would like to start VLC from my phone. Neither the command "VLC", "nohup VLC" or "VLC &"  seem to do the trick.

---

### Post by deconstrained on 2011-02-21
Are you ssh'd into your android from your phone? Or sshing into your computer from your Android (which is also your phone)? What's going on here?

Unless you use X11 tunnelling, you won't be able to start a program over SSH and have it utilize a display. Instead it will have to run through the command line interface. If you mean to have it open on the remote host and use a display on the remote host as well...then I'm not sure how to do that.

---

### Post by bmdsherman on 2011-02-21
I want to run VLC on my computer by sshing into my computer from my android phone.

If I can start VLC, I can then connect to it from the web interface.


update:
I found that running:
```

$ export DISPLAY=:0.0
$ vlc

```works, but quits when I end the ssh connection.

---

### Post by deconstrained on 2011-02-21
Solution: run VLC as a daemon with the -d flag.

---

### Post by hugmenot on 2011-02-21
Use vlc-nox.

---

