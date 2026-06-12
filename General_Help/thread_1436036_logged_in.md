---
title: "logged in"
date: 2010-03-22
forum: General Help
---

### Post by nischalinn on 2010-03-22
My pidgin doesn't show the name of who logged in,as in yahoo messenger. What can I do for that?

---

### Post by zeroseven0183 on 2010-03-22
Hi! I used to have that settings before but thought of disabling it. Now that I'm using 2.6.6, I didn't find libnotify in the Plugins list. So what version of Pidgin are you using? Anyway, I believe** pidgin-libnotify** is the package you need. To install it, type the following in a Terminal
```
sudo apt-get install pidgin-libnotify
``` or download the .deb from [Ubuntu Package Download Page for Karmic > pidgin-libnotify]("http://packages.ubuntu.com/karmic/i386/pidgin-libnotify/download"). That is, if you're using Karmic Koala (9.10). If not, selec the version you're running from the [menu]("http://packages.ubuntu.com/").

Once installed, click **Tools** > **Plugins** in the Pidgin main window, scroll down and put a checkmark on **Libnotify Popups**. If you want, you can also configure what will appear in the popups (new messages, buddy signs on, buddy signs off, etc).

Hope that helps

---

