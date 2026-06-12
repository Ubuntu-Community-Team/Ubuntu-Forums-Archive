---
title: "Adwaita Dark theme title bar bug in 11.10?"
date: 2011-10-25
forum: General Help
---

### Post by georgelappies on 2011-10-25
Hi all

I tried variety of methods to install to install / set the default Adwaita white theme to use the dark version. This works, the only problem is the title bar in my black version stays white unlike the dark color in the screen shots of the theme. This is very distracting as it contrasts to much with the rest of the theme and basically makes it unusable which is a pity as it is a very nice looking theme otherwise.

Any help / advice will be greatly appreciated.

Thanks in advance,

George

---

### Post by bhutada.sachin@gmail.com on 2012-02-17
I had the same problem in my Ubuntu 11.10. Here is what I had done to fix this.

Go the desktop. Right Click -> Select Change Desktop Backgroud -> Change **Theme to be used for the UI** to **Ambiance** . ( If it's already selected to Ambiance, then change it to something else, and again select Ambiance ). It worked for me after doing this. Hope this helps !!!

Sachin

---

### Post by cwklinuxguy on 2012-02-17
Can anyone explain to me exactly what Adwaita is? When I try to use MATE, some of the themes report that they need Adwaita to run, but I can't find it in the repository, and trying to search for Adwaita hasn't turned up much. However, if it's included by default, then I assume I just need to edit a file somewhere to point it to the right place?

---

### Post by Krytarik on 2012-02-18
> **cwklinuxguy said:**
> Can anyone explain to me exactly what Adwaita is? When I try to use MATE, some of the themes report that they need Adwaita to run, but I can't find it in the repository, and trying to search for Adwaita hasn't turned up much. However, if it's included by default ...
"Adwaita" is a set of matching themes - for GTK+ 3 and Metacity (window decoration), plus cursors. It's the default theme set of Gnome Shell, and, like that, not installed by default. It's included in the package "[gnome-themes-standard]("http://packages.ubuntu.com/oneiric-updates/gnome-themes-standard")"; to install it, run:
```
sudo apt-get install gnome-themes-standard
```
Regards.

---

### Post by slickvguy on 2012-02-25
> **bhutada.sachin@gmail.com said:**
> I had the same problem in my Ubuntu 11.10. Here is what I had done to fix this.

Go the desktop. Right Click -> Select Change Desktop Backgroud -> Change **Theme to be used for the UI** to **Ambiance** . ( If it's already selected to Ambiance, then change it to something else, and again select Ambiance ). It worked for me after doing this. Hope this helps !!!

Sachin

lol. You've just changed the window frame to Ambiance (which is dark) so it look sok because it's matching. But that is NOT the proper top of the window in your picture.

---

