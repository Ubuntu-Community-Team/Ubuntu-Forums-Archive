---
title: "remastersys problem -missing applet"
date: 2011-01-30
forum: General Help
---

### Post by patjennings on 2011-01-30
Hi not sure where to post this , hope this is the right place. Anyway I wanted to make a backup of my system using remastersys . I have had success in the past on a different machine using 10.04. This time I tried on my new laptop running 10.10 and got this error message when testing the dvd by booting it.< The Panel encountered a problem while loading "OAFIID:GNOME_IndicatorAppletAppmenu">. I closed the box that asked me if I wanted to delete it and then tried to add it by right clicking on the panel. The same error came up. I ran remastersys twice and burned two different iso's and the same thing happened both times. I have evolution unchecked and hidden in my menus and also use thunderbird as my default mail client, do you think this might have something to do with this seeing that some of  the applets that dissapeared are related to evolution. (letter icon, and volume, and ubuntu one and chat stuff ) the network and calender icons did not disappear. Or is it a problem with 10.10 not responding well to remastersys.  Any help would be greatly appreciated. Oh by the way I got remastersys from sourceforge the latest version and this happened using the "backup" mode not the "distro" mode.

---

### Post by patjennings on 2011-02-22
part of the problem is solved, view this thread for the applet problem  [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10413331](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10413331)

---

### Post by patjennings on 2011-02-23
I needed to exclude /home/<user>/.cache and also make sure ubuquity frontend gtk was installed. And remastersys worked after that.

---

### Post by rabi111 on 2011-10-04
OAFIID:GNOME_IndicatorAppletAppmenu". show this error when i install macbuntu, how could i resolve this?

---

