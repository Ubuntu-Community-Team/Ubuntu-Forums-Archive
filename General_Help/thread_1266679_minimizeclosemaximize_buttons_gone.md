---
title: "minimize/close/maximize buttons gone"
date: 2009-09-14
forum: General Help
---

### Post by stupidchunk on 2009-09-14
I'm using Ubuntu 9.04 and when I rebooted my pc all the buttons on the top right corner of the windows are gone and I cannot move my windows. Even when I run the terminal, all I see is a white screen. After googling around, I tried the 'metacity --replace' command and it's working fine now. However, is there a way for me to enable video effects in metacity? When I choose Normal in Visual Effects, i get a dialog box saying 'Desktop effects could not be enabled'. I did some tweaking around in gconf-editor went to compix>allscreens>options and the maximixe_button, close_button, minimize_button entries are all disabled. I assumed that changing them to enabled might work but unfortunately, it didn't. Do you guys know any workaround for this? Thanks.

The only thing I remember doing that might have caused this is changing screen resolution via gksudo nvidia-settings.

---

### Post by briantoumbs on 2009-09-14
I use Compiz Fusion Icon from synaptic manager, added it to my start up apps.

maybe that would help. I use emerald theme manager and compiz instead of metacity but there's options for metacity

---

### Post by stupidchunk on 2009-09-14
Ok, I installed Compiz Fusion Icon and Emerald. Is there anything in the settings that I should tweak? 

I restarted my pc when the window for aMSN loaded, the buttons appeared for a while, my screen flickered and now they're gone again.

---

### Post by briantoumbs on 2009-09-16
When you right click the Fusion Icon in the system tray there's one that says Select Window Decorator, make sure it says Emerald.


gnome-look.org has a bunch of themes for emerald an compiz.

---

