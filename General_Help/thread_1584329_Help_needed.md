---
title: "Help needed"
date: 2010-09-29
forum: General Help
---

### Post by ssenthilkumar on 2010-09-29
Hi All,

I am a newbie to ubuntu. I installed ubuntu 10.04 LTS recently.

Then i installed kde (using internet). The problems are

1. whenever i login by default it enters into GNOME and not to kde
2. If i go to kmenu- leave tab, turn-off is not available

How i can bring these things active ???

Thanks
Senthil.

---

### Post by Old *ix Geek on 2010-09-29
> **ssenthilkumar said:**
> 1. whenever i login by default it enters into GNOME and not to kde
You can edit your /etc/X11/default-display-manager file, changing "gdm" to "kdm." Or you can select "Sessions" (I think...I haven't rebooted lately) from the login screen, and you'll see a list of options including Gnome and KDE. If you select KDE, from that point on it should become the default.
> 2. If i go to kmenu- leave tab, turn-off is not available
I'm not sure why it's missing, but if you right-click on the kmenu button and choose "Application Launcher Menu Settings" you can check "Shutdown" and it'll add it to the menu. Not under "Leave" but at least it'll be there!

---

### Post by ssenthilkumar on 2010-09-29
> **Old *ix Geek said:**
>  you can select "Sessions" (I think...I haven't rebooted lately) from the login screen, and you'll see a list of options including Gnome and KDE. If you select KDE, from that point on it should become the default.

Everytime i am selecting from "Sessions" only, but it is not giving a permanent solution.

I have to check the other method u told..

---

