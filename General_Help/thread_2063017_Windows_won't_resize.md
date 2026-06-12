---
title: "Windows won't resize"
date: 2012-09-26
forum: General Help
---

### Post by Cyber72 on 2012-09-26
Ubuntu 12.04, unity. All my windows are opening the same size and fitted to the top left hand corner of the screen (I can drag them OK). The problem is that I can no longer resize them. The close, minimize and resize buttons normally at the top left of a window are absent (they are not hiding on the bar across the top of the screen).  I cannot grab a window by the edge or corner to change its size. I think this may be connected with Compiz. How do I resolve this?

---

### Post by HiImTye on 2012-09-26
```
sudo apt-get install dconf-tools
```
then set this key to your desired setting:
```
gsettings set org.gnome.shell.overrides button-layout close,minimize,maximize:
```
the order of the buttons is the order it is typed out, and the ':' is the middle of the bar, so the above will have the buttons on the left side.

---

### Post by shaktiman1234 on 2012-09-26
You can also try installing some tweaking software like Ubuntu Tweak or MyUnity.

---

### Post by Cyber72 on 2012-09-26
Thanks Hilm Tye, I did as you suggested, no problems doing so in Terminal but the problem persists. I have restarted the computer but still no resize.

---

