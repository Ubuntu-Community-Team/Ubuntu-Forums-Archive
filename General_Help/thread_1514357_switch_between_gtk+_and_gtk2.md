---
title: "switch between gtk+ and gtk2"
date: 2010-06-20
forum: General Help
---

### Post by M!K3_$ on 2010-06-20
Hello,

I'm using ubuntu 10.04LTS with gnome.

I had to install gtk+ today (this program i was compiling said it needed it) and i managed to get gtk+ working. but now the entire OS has switched to gtk+ (it's all grey and nasty).

Can I switch back to gtk2 without un-installing gtk+?

---

### Post by M!K3_$ on 2010-06-21
bump

---

### Post by elliotn on 2010-06-21
Check if u have libgtk2.0-dev by using synaptic and typing the above name, it its not installed then install it

---

### Post by M!K3_$ on 2010-06-21
I have the **libgtk2.0-dev** package installed.

gtk2.0 was working before i installed the older gtk+ package, so i'm assuming that all the gtk2.0 files are still there.

---

### Post by XSAlliN on 2010-06-21
What are you talking about?

GTK2 is actually GTK**+** 2, meaning it's the same thing.

---

### Post by M!K3_$ on 2010-06-21
I suppose i installed the older version then.

---

### Post by M!K3_$ on 2010-06-21
OK. seemed to have fixed it.

Going off of what XSAlliN said I installed a new theme from gnome-look.org and it worked.

All of the "default" themes are gone, which is what made me think that gtk2 was broken but i suppose it wasn't broken, just incompatible with the default themes.

---

