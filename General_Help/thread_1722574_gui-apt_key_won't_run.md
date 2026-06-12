---
title: "gui-apt key won't run"
date: 2011-04-05
forum: General Help
---

### Post by nocturnal1 on 2011-04-05
I'm on Ubuntu Maverick and trying to install a key so I can then install a developmental version of Scribus. 
I'm following the directions from the site: [http://wiki.scribus.net/canvas/Debian](http://wiki.scribus.net/canvas/Debian)
Step one shows:  **Add the Scribus Archive gpg key to your package manager using gui-apt-key**
After installing gui-apt-key from synaptic package manager, when I try to run it:
Applications -> system tools -> APT Key Manager, I get the error:
> [B]Could not launch 'APT Key Manager'
Failed to execute child process "usr/bin/su-to-root" (No such file or directory)[/B]

I tried uninstalling and reinstalling then running it from the command line with: 
sudo apt-key
It opens but when when I type in the key and press enter nothing happens. It freezes and I have to force quit.

---

### Post by towheedm on 2011-04-06
> **II. Step-by-step instructions.**

 These instructions are focused on Ubuntu.
 ** 1. Add the Scribus Archive gpg key to your package manager using gui-apt-key**

 
[LIST]
[*]Start gui-apt-key from the command line by running "[COLOR=Red]**sudo  gui-apt-key**[/COLOR]" or from the "Run Application" dialog window that appears  when  you press Alt+F2. When gui-apt-key starts you will see its main  window. Enter the Scribus Archive key's ID into the "Key ID" box (1) and  click on the "Add" button (2).
[/LIST]
Start gui-apt-key as stated above from the site:
```
sudo gui-apt-key
```And follow the rest of the instructions.

---

### Post by nocturnal1 on 2011-04-06
It will open but still freezes when I go to add the key and it's not opening as superuser like the site shows.

---

### Post by towheedm on 2011-04-06
Oops!!!!!!!  This is a gui app.  GUI apps must be started using gksudo:

```
gksudo gui-apt-key
```The screenshot is not from Maverick, but from Debian.  Ubuntu does not show '(as superuser)' in the title bar when running a GUI app with root privileges.

Debian uses the su/gksu package as opposed to sudo/gksudo in Ubuntu.

Recommend you use 2b method 2.  This would automatically add the key for you.  No need to use gui-apt-key.

---

