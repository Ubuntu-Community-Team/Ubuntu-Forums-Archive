---
title: "Applet in the middle of the Gnome Panel"
date: 2010-04-24
forum: General Help
---

### Post by carlosgs91 on 2010-04-24
.

---

### Post by dcstar on 2010-04-25
> **carlosgs91 said:**
> Hi, I'd like to put an applet exactly in the middle of my Gnome Panel, I can't do it manually as the applet size varies so I need a way to put it in the middle always.

The applet is dockbarX (a window list) so when I open or close a window the size of the applet changes and then it's not in the middle.


Lock it.

---

### Post by scouser73 on 2010-04-25
Right click on the applet and select **Lock To Panel**

---

### Post by carlosgs91 on 2010-04-25
.

---

### Post by kerry_s on 2010-04-25
you need to put expanding spacers on both sides, i think in gnome you put the separator then right click it & set it to expand in the properties.

---

### Post by mcduck on 2010-04-25
I don't think Gnome-panel has such option.

The location of applets is always defined as pixels from left end f the panel  left end of the applet, (or right  end of panel to right end of the applet, if you toggle that option through gconf-editor), but there is no option for centering anything or using the center of the applet when defining it's position in the panel.

So, no matter what you do, you are not going to get Window List, Dockbar, Notification Area, or any other applet that changes it's size properly centered in the panel.

---

### Post by carlosgs91 on 2010-04-25
.

---

### Post by mcduck on 2010-04-25
> **carlosgs91 said:**
> I tried installing Avant Window Manager (a dock) and I got it working fine in the middle, but as it's not a panel applet when I touch the panel AWN is hided and I can't see it anymore, do you know how to avoid this problem?

You could probably set the AWN window to be always on top. That should keep it above the panel. If you are using Compiz then you can do it with the Window Rules-plugin...

---

### Post by carlosgs91 on 2010-04-25
.

---

### Post by fabounet on 2010-04-26
it's much easier to do that with Cairo-Dock : open the config -panel, choose "Always on top" in the "visibility" menu.

---

### Post by carlosgs91 on 2010-04-26
.

---

### Post by fabounet on 2010-04-27
cairo-dock --keep-above
but honnestly I don't think having 2 docks/panels at the same place is a good solution.

---

### Post by carlosgs91 on 2010-04-28
.

---

