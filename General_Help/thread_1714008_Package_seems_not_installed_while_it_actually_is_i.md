---
title: "Package seems not installed while it actually is installed"
date: 2011-03-24
forum: General Help
---

### Post by Andrei Baciu on 2011-03-24
So i have to use lh command. I have installed all updates for ubuntu, live-build (the package for lh) and its updates. So my system is fully updated.

When i hit "lh" command i get the following message:

The program 'lh' is currently not installed.  You can install it by typing:
sudo apt-get install live-build

When i do type: "sudo apt-get install live-build" i get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
live-build is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Is there anything i can do?

Best regards,
Andrei.

---

### Post by Krytarik on 2011-03-24
Try re-installing it:
```
sudo apt-get install --reinstall live-build
```
Greetings.

---

### Post by Andrei Baciu on 2011-03-25
Thanks Krytarik. But, it did not work. Same response:

```
The program 'lh' is currently not installed.  You can install it by typing:
sudo apt-get install live-build

```

Also i can mention i did this (reinstall) before from the synaptics package manager, same result.

---

### Post by Krytarik on 2011-03-25
And which status is shown by Synaptic?

---

### Post by oldos2er on 2011-03-25
What does **dpkg -L live-build** tell you? Maybe the 'lh' script has been renamed to something else.

---

### Post by Andrei Baciu on 2011-03-30
So actually it is called live-build so it should be lb instead of lh. Still i think there is a real serious problem related to this two packages (live-build and live-helper) and ubuntu at this point. I will not go into details here but if anyone is really interested can go to: [http://tinyurl.com/6867t4w]("http://tinyurl.com/6867t4w")

---

