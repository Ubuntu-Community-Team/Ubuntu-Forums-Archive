---
title: "Drivers....."
date: 2006-05-09
forum: General Help
---

### Post by Slavus on 2006-05-09
I have a Geforce 6800 and I cant get the latest drivers working, grrrr

I followed tseliots HOWTO exactly, installation went fine, but the only driver that doesnt crash my system is vesa!

I get an error saying "caught signal 11! server aborting-"

I have no idea what signal 11 is, i have been searching for a while now, will continue though.

any suggestions?

---

### Post by johnc4510 on 2006-05-09
Here are the commands:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
ctrl+alt+backspace to restart x
This should do it.

---

### Post by Slavus on 2006-05-09
Ah, no, doing that just locks up my system forcing a hard reboot.

If I fiddle with the xorg.conf to load the right modules and the right driver manually, it still catches "signal 11" and wont load.

ehmm, any other suggestions? *shrugs*

---

