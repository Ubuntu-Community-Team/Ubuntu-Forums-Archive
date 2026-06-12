---
title: "graphics card wont install"
date: 2011-05-23
forum: General Help
---

### Post by tetsu7 on 2011-05-23
ive got a PNY Verto VCGGT2401D3XPB GeForce GT 240 graphics card just installed ubuntu 10.10 and cant get the nvidia graphics card driver to install. what can i do?

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did you try System >> Administration >> Additional Drivers  ?

Does it show up there?

---

### Post by tetsu7 on 2011-05-23
yeah i have to load failsafe driver from recovery mode to boot. from there ive done just that and for awhile it wouldnt install even after sudo apt-get install nvidia-current from terminal. ran OS update then tried again, it said install failed rebooted in failsafe mode again and now it shows its installed in additional drivers (version current) however when i reboot i get a screen that looks like television static.

---

### Post by tetsu7 on 2011-05-23
when i go to nvidia x server setting in gui i get a message that says "you do not appear to be using the nvida x driver please edit x configuration file

---

### Post by tetsu7 on 2011-05-23
tried uninstalling the current nvidia driver and installed nvidia 173 driver. failed. i log in text mode and type startx and it says error parsing the config file

---

### Post by linuxinstalledfromhdd on 2011-05-23
There was a great little application a long time ago called Envy. it would automatically remove the old drivers and install the new drivers you want.  I miss it sometimes.

---

### Post by tetsu7 on 2011-05-24
i have the current driver installed so i dont think thats the problem

---

### Post by linuxinstalledfromhdd on 2011-05-24
Maybe this?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by tetsu7 on 2011-05-24
i fixed it by typing in terminal sudo nvidia-xconfig
which i had done before but this time it worked, go figure.

---

### Post by tetsu7 on 2011-05-24
thanks for your help linuxinstalledfromhdd i appreciate it!

---

### Post by linuxinstalledfromhdd on 2011-05-24
No problem.

---

