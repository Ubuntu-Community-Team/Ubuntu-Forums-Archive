---
title: "Users system log config file location"
date: 2010-07-24
forum: General Help
---

### Post by solitaire on 2010-07-24
where are the "System Log Viewer" config files stored?

I know most have been moved into /var/rsyslog.d/ folder
but where are the users config file stored?

I restored my local /home to a fresh install and the Log viewer is looking for log files from the OLD install.

So there must be a config file somewhere in /home/$user that the system log viewer is reading from as well as the rsyslog.d folder...

Anyone help??

---

### Post by robsoles on 2010-07-24
Check if you can spot the offending file(s) in ~/.config

To make it easier, hopefully, open your home folder in nautilus and press [CTRL]+[H] to expose hidden files and poke through those looking for anything mentioning logs/logging.

Although in terminal you could type:
```
find -name *log*
```
while in your ~/ home directory (the directory terminal usually opens in so no need to cd usually) and entries that come up have an OK chance of being the configuration you are looking to kill.

---

