---
title: "Accidentally deleted panel applet..."
date: 2009-12-02
forum: General Help
---

### Post by bradleypariah on 2009-12-02
I accidentally removed my sound volume Panel applet and, unless I'm crazy, I don't think it's in the list of things to "Add to Panel".  I saw stuff for launchers, weather, screen brightness, you know, all that stuff.... but no volume?
It's no emergency.  My laptop has volume buttons on it, I'm just anal.  I want it the way I had it.  I sometimes preferred to adjust my system volume from the applet.

I went in to **System > Preferences > Sound** and I saw nothing about pinning the application or an applet for it to the Panel.
Weird.

I am running 9.1, fully updated, on a MacBook.

Anybody bored and just dying to fix my problem?  Thanks in advance!  :-D

---

### Post by jmszr on 2009-12-02
bradleypariah,

Add "Notification Area" in "Add to Panel". That should do it.

---

### Post by bradleypariah on 2009-12-02
Aha!  Okay.  :-)  Thank you so much.  It worked.  It was a simple fix after all.  I appreciate your time.

---

### Post by ItalOz on 2009-12-04
aaaaah thanks:-D from my side as well and thanks to the originale poster for the easy to find title

maybe mark it as [solved]

---

### Post by tele_mark on 2009-12-04
That name "Notification Area" gets lots of people (me included). Not really a good indication of what's in there when you delete it and go looking for it the first time.

---

### Post by bradleypariah on 2009-12-04
> **ItalOz said:**
> maybe mark it as [solved]

Thanks for reminding me.  Done  :-)

---

### Post by Fozz on 2010-03-02
Thank you from me too!

---

### Post by brallan on 2010-04-12
yes, thank you! if the applet doesn't reappear in the notification area (i am running lucid lynx beta), then you may need to type ```
gnome-volume-control-applet
```, from a terminal.

---

### Post by crash123 on 2010-04-13
Brallan answered my question: even after adding the notification area, I still wan't seeing the volume control until issuing that command from the terminal. But as soon as I close the terminal, the volume control disappears to. When closing the terminal, it tells me I still have a terminal running and if I really want to close it.

I hate to be ignorant, but how do I get around this terminal problem? I've run into that issue with the terminal before but haven't seen the solution around here (pretty new to Ubuntu, FYI).

---

### Post by oldos2er on 2010-04-13
Add an '&' at the end of the command: ```
gnome-volume-control-applet&
```

---

### Post by dannyboy79 on 2010-04-13
> **crash123 said:**
> Brallan answered my question: even after adding the notification area, I still wan't seeing the volume control until issuing that command from the terminal. But as soon as I close the terminal, the volume control disappears to. When closing the terminal, it tells me I still have a terminal running and if I really want to close it.

I hate to be ignorant, but how do I get around this terminal problem? I've run into that issue with the terminal before but haven't seen the solution around here (pretty new to Ubuntu, FYI).

i had this issue recently, the speaker icon was gone. I jsut had to rename my .gnome2 folder which was in my home directory and log off and log back in. it'll recreate your speaker icon. then just copy anything you need from the old .gnome2 folder to the newly system created one. good luck

---

### Post by tayip on 2011-03-02
Just solved this problem. THX!!

---

