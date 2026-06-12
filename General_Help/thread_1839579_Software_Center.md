---
title: "Software Center"
date: 2011-09-05
forum: General Help
---

### Post by Vepres on 2011-09-05
I'm trying to start up the Software Center application, but whenever I click on it, the program loads without any information on the screen, it's completely blank. I ran the sudo software-center --enable-lp command in the terminal and then the Software Center loaded, but many of the applications that were there previously were no longer there. Any ideas?

---

### Post by Toz on 2011-09-07
Can you try running, from the terminal:
```
sudo apt-get update
```and```
sudo apt-get upgrade
```
Post back any errors.

---

### Post by Vepres on 2011-09-08
With the sudo apt-update I got this as a response:

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

The sudo apt-get upgrade said that there were no new upgrades to install.

---

### Post by Toz on 2011-09-08
Go to System->Administration->Software Sources (or if you can get the Software Centre to start, then goto Edit->Software sources) and uncheck the entries for your CDROM.

Then run:
```
sudo apt-get update
``` one more time and see if the error messages are gone. If they are, then fire up Software Center and see if it works now.

---

### Post by Vepres on 2011-09-08
That didn't do it either. I guess I could just stick with running the sudo software code and that'll be fine.

---

### Post by wildmanne39 on 2011-09-08
Hi, after unchecking cdrom what errors are you getting now from:
```
sudo apt-get update
```
please post the complete results of that command here.
Thank you

---

### Post by Vepres on 2011-09-08
I don't get any errors when I use this code, all that happens is that the terminal tells me that the update is complete, but I still can't get onto the Software Center unless I use the sudo software-center --enable-lp code.

---

### Post by wildmanne39 on 2011-09-08
Hi, I do not know how to fix this issue but when you open a graphical program with sudo there is a possibility that it will become owned by root, then you will not have access to it.

Try to open synaptic package manager and see if it opens, but do not do it from the terminal do it from dash if you are using 11.04, if it opens you can use it to install packages.

The command so use for graphical programs is gksu or gksudo.

I will research this if I find an answer I will post back.
Thank you

---

### Post by Toz on 2011-09-08
What happens when you run just:
```
software-center
```
in a terminal window? 

Does it work? Can you post back the messages that appear in the terminal window after you run it?

---

