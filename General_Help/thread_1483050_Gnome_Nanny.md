---
title: "Gnome Nanny"
date: 2010-05-14
forum: General Help
---

### Post by Juasjero on 2010-05-14
Hi there:

I'm trying to install Gnome Nanny [http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/)

I installed it using Synaptic and when I restart, the Nanny daemon appears to be working.
However, when I try to access to the Parental Control (System - Administration - Parental Control) and after writing my password, it does not shown anything. Nor any windows not any configuration.

I am using Lucid Lynx I386. Could you help me?

Do you know any parental control which could block programs execution (like games, instant messengers, browsers...), could have web filtering and could have spending time control?

Thanks.

---

### Post by Juasjero on 2010-05-14
Here's what i got while trying to start the consoles from the  terminal:
```
wingman@Sandiego:~$ sudo NannyBlacklistManager
Traceback (most recent call last):
  File "/usr/sbin/NannyBlacklistManager", line 37, in  <module>
    nanny_blacklist_manager = nanny.client.gnome.admin.BlacklistManager()
  File "/usr/lib/python2.6/dist-packages/nanny/client/gnome/admin/BlacklistManager.py",  line 46, in __init__
    self.alignment.unparent ()
AttributeError: BlacklistManager instance has no attribute 'alignment'
wingman@Sandiego:~$ sudo NannyAdminConsole
/usr/lib/python2.6/dist-packages/nanny/client/common/Utils.py:32:  GtkWarning: GtkSpinButton: setting an adjustment with non-zero page  size is deprecated
  object.xml.add_from_file (main_ui_filename)
wingman@Sandiego:~$
```
 Any ideas?


Line 32 shows in /usr/lib/
python2.6/dist-packages/nanny/client/common/Utils.py  :
```
31:    object.xml = gtk.Builder ()
32:    object.xml.add_from_file (main_ui_filename)
33:    objects = object.xml.get_objects()
```
 Line 46 in /usr/lib/python2.6/dist-packages/nanny/client/gnome/admin/BlacklistManager.py  shows:
```
44:       self.dbus_client = nanny.client.common.DBusClient ()
45:
46:       self.alignment.unparent ()
47:       self.dialog.get_content_area().add  (self.alignment)
```
 What could we do?

---

### Post by sandu.lulu on 2010-05-16
same here... any ideas?.. help still needed.

---

### Post by Juasjero on 2010-05-16
I have sent an email to the developers (I do not think they will answer me... but... I did it).

The bug is reported on Bugzilla and Launchpad. Cross our fingers and wait.

---

### Post by Juasjero on 2010-05-16
The developers have answered and they told me that they are going to release a new version and it will be fully fixed.

Great!

---

### Post by bumanie on 2010-05-16
The site link you sent does clearly say (once one goes to the download section) that there are no stable versions, only development versions. Good that you have found a bug, but it is not really ready for every-day use until a stable version is released.

---

### Post by Juasjero on 2010-05-16
Fixed:
[http://ftp.gnome.org/pub/GNOME/sources/nanny/2.29/nanny-2.29.4.tar.gz](http://ftp.gnome.org/pub/GNOME/sources/nanny/2.29/nanny-2.29.4.tar.gz)

---

### Post by sandu.lulu on 2010-05-17
thanks a million.
tried the fix but still not working properly. i'll wait for the official release. 
thanks anyway for the replies.

---

### Post by nigsy on 2010-08-29
Hi, just bumping this thread:

I have just installed the latest (Unstable) version of Gnome Nanny and am getting the:

Nanny daemon is not started message.

Have had a ook on goole but not finding any answers.

Anyone on here got a fix yet?

---

### Post by nigsy on 2010-08-31
If any one else is trying to install this on Ubuntu 9.1

from terminal:

sudo add-apt repository ppa:nanny  (enter)

then

sudo apt-get update && apt-get install nanny  (enter)


worked first time, no issues.

Then go to the Gnome nanny home page and d/l and import the blacklist file if required.

---

