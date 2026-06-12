---
title: "how to clean what i did? :D"
date: 2011-05-22
forum: General Help
---

### Post by jardo on 2011-05-22
ok...i know im a newbie...i think i wanted to do something bigger than me...and now i want to clean everything and going back...
here it's what i did on this page: [http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/126/how-to-detect-cpu-temperature-fan-speeds-and-voltages-lm-sensors-in-ubuntu)

i think i load a module when ubuntu startup,installed lm-sensors and made an executable script? right? how can i get everything back and cleaning ?
:D

---

### Post by matt_symes on 2011-05-22
Hi

It is an old tutorial written in 2008.

What version of Ubuntu are you using ? lm-sensors may have been installed when you installed the operating system. If you do need to remove it..

```
sudo apt-get remove lm-sensors
```

Enter your password. It will not be echoed to the screen.

but find out if it was installed with Ubuntu before you try that.

Delete the file mkdev.sh

If you know where it is ..

```
rm mkdev.sh
```

If you don't know where it is.

```
find / -name mkdev.sh -exec rm '{}' \;
```

Depending on where you created it, it may require sudo privileges.

Reboot your PC to get rid of the nodes created by mknod in the script. They are non persistent. Rebooting should also get rid of any modules you may have loaded.

Kind regards

---

### Post by jardo on 2011-06-13
thanks a lot for helping! i had installed ubuntu 11.04, and i installed lmsensors...so i just did what u suggested to me...hope i deleted everything :D
thanks!

---

