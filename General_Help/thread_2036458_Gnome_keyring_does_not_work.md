---
title: "Gnome keyring does not work"
date: 2012-08-01
forum: General Help
---

### Post by sbw87 on 2012-08-01
Hi,

I have just installed a fresh Xubuntu 12.04. The Gnome keyring only seems to work if I select "Load runtime environment for GNOME at system start" in the settings menu.
Specifically, I am using a secondary SSH key stored in, say, ~./ssh/id_rsa_2. Without the above option actived, I have to re-enter the SSH keyphrase every time.
However, I don't actually want to load a full "runtime environment for GNOME" on startup -- I just want the keyring to work, nothing else.
On my Unity machine, on the contrary, this all works perfectly fine and hassle-free out-of-the-box.

Thanks for your help!

---

### Post by sbw87 on 2012-08-02
*bump*

---

### Post by brainwash on 2012-08-02
Edit the needed gnome-keyring-*.desktop files located in **/etc/xdg/autostart** and change the value of "OnlyShowIn=" to:
```
OnlyShowIn=GNOME;Unity;XFCE;
```

Additionally, you might need to activate those entries in your application autostart list (settings manager).

---

### Post by sbw87 on 2012-08-02
I did this with just one of them (the ssh one), and it didn't work; do you think enabling all of them might help?
Also, I've tried executing the commands in these .desktop files manually just to see if this resolves the issue; but it didn't help.

---

