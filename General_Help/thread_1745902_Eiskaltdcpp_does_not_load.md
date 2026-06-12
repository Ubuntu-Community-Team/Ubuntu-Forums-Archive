---
title: "Eiskaltdcpp does not load"
date: 2011-05-01
forum: General Help
---

### Post by sm00nie on 2011-05-01
Hi all,

I installed eiskaltdc++ from the software center and occasionally when I launch the application, it does not load. No error is produced at all, so I tried launching from terminal to see if any errors are produced and the following comes up --> 
Internal server running on 6661
Signal handlers installed.
$XDG_CONFIG_HOME: /home/user1/.config/eiskaltdc++/
$XDG_DOWNLOAD_DIR: /home/user1/Downloads/
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Setting up new font: Ubuntu,11,-1,5,50,0,0,0,0,0
UserList icons has been loaded
Application icons has been loaded
void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "" under id 6 
void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "" under id 6 
void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "" under id 9 
void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "" under id 11 
QWidget::setMinimumSize: (transfer_dock/QDockWidget) Negative sizes (0,-1) are not possible
Setting up new font: Ubuntu,11,-1,5,50,0,0,0,0,0


eiskaltdc++ is not running when I do try and relaunch. 

Would anyone have any idea's on how I could resolve this ?

---

### Post by conualfy on 2011-05-10
I'm having the same problem, the main window is invisible or not painted. But I could see some messages from hub bots in the top left part of the screen, so I think it's working, but we just don't see it.

In System Monitor you'll find the eiskaltdcpp process and you can kill it, but still useless as it will not work.

I have no idea how to make it work. I use Ubuntu 11.4 with some updates from proposed upgrades (kernel, etc.; I hoped it will fix the high power consumption but it's still there).

> uname -r
2.6.38-9-generic

It really looked like a nice software, but too bad it's not working properly :(

---

### Post by conualfy on 2011-05-10
I've upgraded the standard repository (2.0.x) to 2.2:

```
sudo add-apt-repository ppa:tehnick/tehnick
sudo apt-get update
sudo apt-get install eiskaltdcpp
```

And it seems to work better.

---

