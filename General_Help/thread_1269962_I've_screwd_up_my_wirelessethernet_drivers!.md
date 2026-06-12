---
title: "I've screwd up my wireless/ethernet drivers!"
date: 2009-09-18
forum: General Help
---

### Post by JigglyWiggly_ on 2009-09-18
Ok so on my laptop I decided to install this new network manager that people said was good on the synaptic package manger. So I isntalled it, except I couldn't get it to work with Intel Leap, so I uninstalled it... little did I know it got rid of the built in ubuntu wireless manager.
if I do ifconfig:


it just shows the interface "lo" as the interface with an interface of 127.0.0.1

So I tried running nm-applet and it said I need to install network-manager-gnome...
But how?!, there is no internet via wifi or via the ethernet port. I need help... I didn't realize ubuntu was this easy to break.

---

### Post by JigglyWiggly_ on 2009-09-18
Oh also I downlaoded network-manager and network-manager-gnome from a different pc and then the stupid network manager says it needs other files to run it... which is the other deb file. Like it says it wants both for it to work, I have downloaded both, how can I get around this?

Btw I used wicd.

---

### Post by Chronon on 2009-09-18
Maybe post the exact command you're running and the output.

---

### Post by mikewhatever on 2009-09-18
Well, you didn't really break Ubuntu. It should be expected that removing the NM will also remove its managing functionalities. Anyway, you can download the required package from here [http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=jaunty&section=all)
Double click to install.

---

### Post by JigglyWiggly_ on 2009-09-18
Hmm I went into the synaptic package manger and just and tried clicking wicd, and it installed again. I'm back online, I guess ubuntu didn't throw the deb file for it out :D

---

### Post by Chronon on 2009-09-19
They are usually cached and don't get removed unless you do "sudo apt-get clean" or "sudo apt-get autoclean".

---

