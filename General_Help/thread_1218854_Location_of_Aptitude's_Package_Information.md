---
title: "Location of Aptitude's Package Information"
date: 2009-07-21
forum: General Help
---

### Post by ubiedubie on 2009-07-21
Hello,

Where will I find these files?

I would like to copy them from one computer to another - because on my home computer it says "flashplugin-nonfree-extrasound" is not found. They are both using the same repositories, and it works on this computer.

Flash sound doesn't work with my creative x-fi without it so I need to do this! :KS

Thank you guys

---

### Post by CatKiller on 2009-07-21
flashplugin-nonfree-extrasound is in the Multiverse repository. Don't forget to refresh the list of available packages with ```
sudo apt-get update
```

---

### Post by ubiedubie on 2009-07-21
I've done all that, and the repository is enabled - it just doesn't seem to work.

I thought maybe I could transfer the list of packages on this computer's repositories to my home computer, and then it will recognise it

---

### Post by ubiedubie on 2009-07-22
I just realised one is x86 and one is amd64 so that is why flashplugins-nonfree-extrasound doesn't work.

For some reason I can't get it for 64 bit ubuntu

---

