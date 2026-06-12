---
title: "Nautilus is installed but not found !"
date: 2010-02-10
forum: General Help
---

### Post by omaralqady on 2010-02-10
After installing and removing some packages through Synaptic, which I don't know is related to this or not, I tried to open the home folder from the Place menu on the panel and received the following error: ```
Error
Could not open location 'file:///home/omar'
No application is registered as handling this file
```
So I tried to open nautilus from the terminal, I receive a response that it's not installed and I can install it using sudo apt-get install nautilus, so I do just that, and I get a response that it's already installed! So I went into Synaptic and reinstalled it, then it worked for a little while, but suddenly I got the same error again with no reboot or application installs/uninstalls/upgrades/updates in between! Does anyone have an idea as to what happened and how to fix it? I'd appreciate any help :)

---

### Post by Satoru-san on 2010-02-10
> **omaralqady said:**
> I'd appreciate any help :)
Try this 

```
sudo apt-get purge nautilus
sudo apt-get install
sudo /etc/init.d/gdm restart
```
then you can try nautilus again, if that still doesnt work try again to open it from the commndline, if you can do that, then right click a folder and set its default open app to nautilus.

---

### Post by omaralqady on 2010-02-10
When I restarted gdm, gnome was not available in the menu at the bottom of the login screen! There was only fluxbox and xterm there! So now I'm using fluxbox to post this. I can now run nautilus through the terminal in fluxbox :D but I can't start gdm. This is the error I get when I try to start it in the terminal: ```
omar@3omar:~$ sudo gdm

** (gdm-binary:17954): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:17954): WARNING **: Could not acquire name; bailing out

```

I tried to reinstall nautilus and gdm using synaptic in fluxbox but nothing changed. I also tried to boot from the recovery kernel and fix broken packages nothing changed! 

What can I do now :)??

---

### Post by omaralqady on 2010-02-10
I booted using the .17 recovery kernel and chose fix broken packages, this time it reinstalled some packages and everything is fine now :) Thanks for your help anyway :)

---

### Post by koryusai on 2010-06-24
also if you type:
```
sudo apt-get purge nautilus
sudo apt-get install ubuntu-desktop
sudo reboot

```

this worked for me but repairing the broken packs didn't

---

