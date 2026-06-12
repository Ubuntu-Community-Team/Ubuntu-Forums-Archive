---
title: "Dump/Load gconf"
date: 2010-10-07
forum: General Help
---

### Post by caleb.g.lawson on 2010-10-07
I'm working on a script.  After it has installed and removed packages, I need to configure a **ton** of settings.  In GNOME, I understand that those settings are kept in "/home/user/.gconf".

Can I create a virtual machine and configure the system through the GUI to my liking and then dump all of the settings, so that I can load them on another machine?  Is it as simple as copying the directories?

---

### Post by dcstar on 2010-10-08
> **caleb.g.lawson said:**
> I'm working on a script.  After it has installed and removed packages, I need to configure a **ton** of settings.  In GNOME, I understand that those settings are kept in "/home/user/.gconf".

Can I create a virtual machine and configure the system through the GUI to my liking and then dump all of the settings, so that I can load them on another machine?  Is it as simple as copying the directories?

Have a look at this:

```
man update-gconf-defaults
```

---

### Post by caleb.g.lawson on 2010-10-08
David, I looked into you solution; however, I decided to opt into copying the directories.  

**The following is intended for my own, personal use.  Take caution if you choose to run the following code.**

Here's my code:
```
#This is a BASH script... I don't do crunchbangs, sorry.
#This script is intended for machines running Ubuntu 10.10: Maverick Meerkat.
#To run this script, edit the permissions first by running: "sudo chmod +x"
#Run this script using: "sudo -k ./givebak.sh"
#If all else fails, run the script as root.

#First, we're gonna remove the stuff we don't need and clean the cache!
apt-get remove -y --purge tomboy
apt-get remove -y --purge evolution
apt-get remove -y --purge empathy
apt-get remove -y --purge gwibber
apt-get remove -y --purge transmission
apt-get remove -y --purge totem
apt-get remove -y --purge firefox
apt-get remove -y --purge ubuntuone-client-gnome
apt-get autoremove -y
apt-get clean

#Now, we'll try and update everything.
apt-get update
apt-get upgrade -y

#After that, we'll get the goodies.
add-apt-repository ppa:tualatrix/ppa
add-apt-repository ppa:chromium-daily/ppa
add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
add-apt-repository ppa:nilarimogard/webupd8
apt-get update
apt-get install -y shutter
apt-get install -y frozen-bubble
apt-get install -y gweled
apt-get install -y gimp
apt-get install -y inkscape
apt-get install -y chromium-browser
apt-get install -y audacity
apt-get install -y vlc
apt-get install -y gnome-do
apt-get install -y breathe-icon-theme
apt-get install -y ubuntu-restricted-areas
apt-get install -y community-themes
apt-get install -y gnome-colors
apt-get install -y shiki-colors
apt-get install -y geany
apt-get install -y talika
apt-get install -y ubuntu-tweak
apt-get upgrade -y

#Now, we copy over a default home directory.  Settings are kept there...
wget http://dl.dropbox.com/u/12910665/Payload.zip
unzip -o Payload.zip && rm Payload.zip

#Then we'll clean up after ourselves and exit nicely!
apt-get clean
shutdown -r 1
```

---

