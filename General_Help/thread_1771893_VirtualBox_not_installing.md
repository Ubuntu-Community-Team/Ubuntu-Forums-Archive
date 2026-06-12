---
title: "VirtualBox not installing"
date: 2011-05-30
forum: General Help
---

### Post by r2d211 on 2011-05-30
Hello,

I downloaded the Virtualbox for Natty (a .deb file) and by double clicking it the Software Center appears and is ready to install. I press the install button, give my password in the new popup and then it seems that it starts installing it. But after 10 seconds the progress bar disappears and I have again the install button, but dimmed, so I am not able to click it. Any further click on the Software center's window makes it non responsible and crashes.


Why and what to do?

---

### Post by sbraz on 2011-05-30
try installing it from oracle's repo as i did.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

scroll down to "Debian-based Linux distributions" and follow the instructions. :)

---

### Post by r2d211 on 2011-05-31
That's not easy because I have no internet on ubuntu. In windows I use Tether for Blackberry to get online and that's how I got the .deb package.

Anyway, I tried again today and for a few moments was installing it (through the software center), but then a popup tpld me this cannot be done because the file has 'untrusted dependences'.

???

---

### Post by sbraz on 2011-05-31
it is possible that the .deb is trying to install some other packages as well, like compilers libraries etc. since there's no available source as there's no internet connection or local repository, it throws an error and quits.

edit:
sorry i didn't read that you installed from ppa.

have you enabled "restricted" and "multiverse" from "software sources"?
also, you need to add the key as the guide says. :)

---

### Post by r2d211 on 2011-05-31
Which key and which guide? I know nothing about keys.  :(

---

### Post by sbraz on 2011-05-31
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

i think this is what you need.

---

### Post by linuxinstalledfromhdd on 2011-05-31
The only way you are going to get this right is by using the PPA above.  Make sure you install Virtualbox 4 the most recent updated version too. :)

---

### Post by boblizar on 2011-05-31
i would add the ppa repository from virtual box and follow the instructions on the download page to move the key to a file and then the command to make the repository active under synaptic

---

### Post by r2d211 on 2011-06-01
I tried again today but the installer needs some extra files from the internet, so I just leave it. In the mean time my bbtether start working but it needs some modifications and it will take a while till I'll sort them out.

---

### Post by r2d211 on 2011-06-02
Okay, everybody, finally I managed to install it! I had to manually download 11 libraries it was depending of, install them and the install the VB. Now it's working. Thank you, everybody for your support!

Now, I must figure out how to configure it, but that's for another thread.

Have a great weekend.

I think I could mark our thread as SOLVED now.

---

