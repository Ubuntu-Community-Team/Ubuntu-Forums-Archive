---
title: "ubuntu not booting to gnome..."
date: 2010-03-16
forum: General Help
---

### Post by f1champ on 2010-03-16
Hello,
I'm a noob with Linux. I was trying to disable pulseaudio, I went to synaptic software and mark pulseaudio server for uninstallation, then mark ALL on the next screen.... afterward, my skype works fine. however, after i reboot, it only boots to prompt....
anyway i can fix it without reinstalling?

---

### Post by MelDJ on 2010-03-16
you have removed the ubuntu-desktop package. 
connect to internet from terminal and reinstall it by

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Fxy on 2010-03-16
If you can get to terminal log in using you username and password, then type **startx**...

Through typing that you desktop should appear/load ;) ...

---

### Post by jcbrown on 2010-04-20
> **f1champ said:**
> Hello,
I'm a noob with Linux. I was trying to disable pulseaudio, I went to synaptic software and mark pulseaudio server for uninstallation, then mark ALL on the next screen.... afterward, my skype works fine. however, after i reboot, it only boots to prompt....
anyway i can fix it without reinstalling?[FONT=Calibri][SIZE=3]Why call yourself a noob for having  Linux? Even I own a Linux and I don’t consider myself a noob. Anyway,  connect it to the internet and reinstall it by the above code. See if  that helps. It worked for me![/SIZE][/FONT]

---

