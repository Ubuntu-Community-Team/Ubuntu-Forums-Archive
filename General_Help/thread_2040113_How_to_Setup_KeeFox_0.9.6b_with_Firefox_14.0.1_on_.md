---
title: "How to Setup KeeFox 0.9.6b with Firefox 14.0.1 on Ubuntu 12.04."
date: 2012-08-10
forum: General Help
---

### Post by Maximus_ARNP on 2012-08-10
How to setup [COLOR="Purple"]**KeeFox 0.9.4**[/COLOR] with [COLOR="Purple"]**Firefox 14.0.1**[/COLOR] on **[COLOR="Purple"]Ubuntu 12.04[/COLOR]**

This instructions **[COLOR="Red"]DOES NOT[/COLOR]** require KeeFox Portable download.

Via Synaptic Package Manager, install following packages:
KeePass2
mono-runtime
mono-utils
mono-devel
mono-complete
xdotool

Go to Firefox addon website.
Search and go to KeeFox.
Scross page until you see **[COLOR="Red"]version 0.9.4[/COLOR]**
Install this version into your Firefox.
Restart Firefox.

[COLOR="Red"]**DISABLE auto-update of KeeFox**[/COLOR] extention as follows:
Go to Firefox ----> Add-On ---> KeeFox ----> MORE ----> Automatic Updates ----> Turn OFF.

Now go to:
/home/username/.mozilla/firefox/um9834u4.default/extensions/keefox@chris.tomlinson/deps
Copy all 4 files.
As a root, create a folder name "plugins" into:
/usr/lib/keepass2/
PASTE all 4 files into "plugins" folder.

Restart Firefox.

[COLOR="Blue"]**You will get a KeeFox message. Do not worry, just continue as follows:**[/COLOR]

CONFIGURING KEEFOX in FIREFOX:
Now go to --> Firefox --> Add-On --> KeeFox --> Options --> Advanced --> When opening or logging in to KeePass, use this database file --> Browse and select your KDBX file.

Next tab --> KeePass
In [COLOR="Blue"]**"KeePassRPC plugin location"**[/COLOR], please write the location of KeePassRPC file as follows. In your home directory, please search KeePassRPC and use it's location:
/home/username/.mozilla/firefox/um9834u4.default/extensions/keefox@chris.tomlinson/deps

Assuming that you have installed "KeePass2", in [COLOR="Blue"]**"KeePass installation location"**[/COLOR] please write:
/use/lib/keepass2

Assuming that you have installed "mono-runtime", in "Mono executable location" please write:
/usr/bin/mono

Restart Firefox.

When you start KeePass2 and select tools -> plugins, you should see “KeePassRPC”. Do Nothing Here.

Now Restart Firefox.
Go to any website tha requires username and password. Following alert may show up:
"Your are not logged in to your password database." There, load your database, enter password, and enjoy KeeFox.

On how to use KeeFox, please visit it's tutorial on the developer's website.

[COLOR="Magenta"]**To save screen real estate from KeeFox toolbar:**[/COLOR]
View --- Toolbars --- Customize --- Drag and drop individual buttons from KeeFox toolbar to where ever you want. In my case, I've put them next to URL-box/address-box.
Now, View --- Toolbars --- Uncheck KeeFox toolbar.

Thank you.

---

### Post by tgri on 2013-04-21
Thanks for this.:D
Just wanted to mention it also works with Ubuntu 12.10 and KeeFox 1.1.4.

---

