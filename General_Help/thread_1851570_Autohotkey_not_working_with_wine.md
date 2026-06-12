---
title: "Autohotkey not working with wine"
date: 2011-09-28
forum: General Help
---

### Post by vletoh on 2011-09-28
Hello,

I've setup Autohotkey (the Windows automation tool) using wine (since several users reported to have this combination running successfully). I've some keys in the script as wel as some hotstrings. Unfortunately none of them are working in Ubuntu 11.04.
The AHK icon is shown in the status bar and if I right-click the icon and select 'Edit this script' my script containing the keys/hotstrings are indeed opened. So it seems AHK is running OK.
Any idea why keys/hotstrings are not captured/executed?
Any help welcome.

---

### Post by marshag63 on 2011-09-28
Sorry I cannot help you specifically with AutoHotKey and Wine.

I use Autokey for linux:  [http://code.google.com/p/autokey/](http://code.google.com/p/autokey/)

If your issues with AHK and Wine are unsolvable, maybe you could give AutoKey a try.

Hope this helps  :)

MDG

---

### Post by vletoh on 2011-09-29
> **marshag63 said:**
> Sorry I cannot help you specifically with AutoHotKey and Wine.

I use Autokey for linux:  [http://code.google.com/p/autokey/](http://code.google.com/p/autokey/)

If your issues with AHK and Wine are unsolvable, maybe you could give AutoKey a try.

Hope this helps  :)

MDG

Hi MDG,

Thx for your hint. I noticed the existence of AutoKey but didn't want to take the burden to convert my phrases and scripts. However your message was the motivation to give it a try. It works actually quite good and translation of the AHK file did cost me about an hour.
One thing that doesn't work properly in Ubuntu 11.04 is that no icon is shown in the statusbar. According to the preferences there is a choice for showing the icon, even there is a choice for a colored or gray icon. Any idea how to get the icon visible?
(Note: AK is running; I can get to the configuration using the Super-K key).

Thanks for any help

---

### Post by marshag63 on 2011-10-02
vletoh,
Did you install the beta version (0.80)? Are you using Gnome, KDE or something else?  GTK or QT? 

MDG

---

### Post by vletoh on 2011-10-08
I'm using Ubuntu 11.04 with Unity. The Autokey installed with Ubuntu SW Center is 0.71.2.
I did take a look at autokey.googlecode.com but I have no clue how to install that 0.8 version offered there. It seems a source package. The FAQ offered on that site isn't of any help either.

---

### Post by vletoh on 2011-10-08
In the meantime I've found a way to install 0.80 by adding cdekter's repository ([http://www.ubuntugeek.com/autokey-desktop-automation-utility-for-linux-and-x11.html](http://www.ubuntugeek.com/autokey-desktop-automation-utility-for-linux-and-x11.html))

After it has replaced Autokey ('Preparing to replace autokey-gtk 0.71.2-1 (using .../autokey-gtk_0.80.2-0~natty_all.deb) ...') it seems the Autokey installation is totally f* up. The icon is gone when I search for Autokey in the Dash and when I run it in a terminal I get: 

$autokey-gtk
Traceback (most recent call last):
  File "/usr/bin/autokey-gtk", line 20, in <module>
    from autokey.gtkapp import Application
  File "/usr/lib/python2.7/dist-packages/autokey/gtkapp.py", line 25, in <module>
    import service, monitor
  File "/usr/lib/python2.7/dist-packages/autokey/service.py", line 21, in <module>
    from iomediator import Key, IoMediator
  File "/usr/lib/python2.7/dist-packages/autokey/iomediator.py", line 106, in <module>
    from interface import *
  File "/usr/lib/python2.7/dist-packages/autokey/interface.py", line 39, in <module>
    from PyQt4.QtGui import QClipboard, QApplication
ImportError: No module named PyQt4.QtGui


Cool!

---

