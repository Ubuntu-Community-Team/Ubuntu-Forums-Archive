---
title: "Nautilus 'Open as Administrator' opens folder with wrong program"
date: 2011-10-21
forum: General Help
---

### Post by silentstone on 2011-10-21
Running **Unity** in Ubuntu 11.04 and this used to work. But now, right-click on a folder in **Nautilus**, click 'Open as Administrator' and a dialog requests admin password with a "*The application 'decibel-audio-player file:///path/to/folder lets you modify essential parts of your system*."  

How could **Decibel** hijack this?  It's not even listed as a possible folder-opening program in Nautilus's incredibly lean preferences.  When just selecting a folder, it will open with Nautilus, in Nautilus.  And only when trying to open with root privileges through the 'open as admin' menu item does the problem occur.  **gksu nautilus /path/to/folder** asks for password and opens in Nautilus, as expected.

---

### Post by crdlb on 2011-10-21
Nautilus does not come with an "Open as Administrator" entry. This appears to come from the nautilus-gksu extension. I'm not sure why it's malfunctioning.

---

### Post by mc4man on 2011-10-21
could you post what this shows, more interested in an entry that doesn't end with a ;
```
cat ~/.local/share/applications/mimeapps.list |grep inode
```

And while probably not a factor this
```
 cat /etc/gnome/defaults.list |grep inode
```

---

### Post by nochiel on 2011-10-22
> **mc4man said:**
> could you post what this shows, more interested in an entry that doesn't end with a ;
```
cat ~/.local/share/applications/mimeapps.list |grep inode
```And while probably not a factor this
```
 cat /etc/gnome/defaults.list |grep inode
```


Upgrading to Oneiric has been a tragedy. Here's what I get:
```
inode/directory=vlc.desktop;nautilus-folder-handler.desktop;evince.desktop;
```As a result, when any application attempts to open a folder, or when I click a folder icon in the panel, VLC opens!

---

### Post by mc4man on 2011-10-22
open up that that file
```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Added Associations] section make the line look like this
```
inode/directory=nautilus-home.desktop;vlc.desktop;evince.desktop;
```
There should be a [Default Applications] section, add this line to it, make sure the line isn't present, if it is then replace with this
(note the entry in this section does not end with a ;
```
inode/directory=nautilus-home.desktop
```
You may need a log out or restart

if unsure then post the complete mimeapps.list & will fix it

Edit: did you cat the /etc/gnome/defaults.list? If so it must return 
inode/directory=nautilus-home.desktop

---

### Post by silentstone on 2011-11-22
Sorry for the delay:  I upgraded to Oneiric :biggrin:.  Lost the "Decibel opens folders" problem and gained some new ones!

Thanks for the replies.  **decibel-player** was indeed associated with inode/directory in *~/.local/share/applications/mimeapps.list*.  I don't know how it could have happened, though, as I hadn't even used Decibel then-recently.  And the **nautilus-gksu** extension was working fine before.  

Regardless, I'm glad to learn where these settings are stored.  I'm hoping to fix a bunch of listings and "open with" links to programs that were carried over from my Natty configs and files.  Not everything was reinstalled on Oneiric.

---

