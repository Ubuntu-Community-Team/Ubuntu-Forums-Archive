---
title: "Newest Updates hosed my video drivers."
date: 2010-02-05
forum: General Help
---

### Post by The Funkbomb on 2010-02-05
Running a 9600GT.  Newest update as of today knocked out my drivers.  I reverted to an earlier kernel.  I can re-install the driver to end the error on boot but now I can't use desktop effects.

---

### Post by Leppie on 2010-02-05
if you received a kernel update, you will have to re-install your video drivers unless you were using the kernel drivers.

---

### Post by Idiens on 2010-02-05
Dell Studio, same problem with -19 installation. How do I reload the drivers please? (Newbie)

---

### Post by Leppie on 2010-02-05
you could try going to System>Administration>Hardware Drivers and enable them if they are presented there.

---

### Post by ratcheer on 2010-02-05
> **Idiens said:**
> Dell Studio, same problem with -19 installation. How do I reload the drivers please? (Newbie)

**If** they are nVidia drivers:

Ctrl-Alt-F1 and log in to the system console
sudo service gdm stop
cd (to directory where your driver file is)
sudo sh ./xxxxxxxxxxxxxxxx (<-- your driver file)
(When script asks if you want to auto configure xorg, select Yes)
sudo init 6

Tim

---

### Post by Richard1979 on 2010-02-05
> **ratcheer said:**
> **If** they are nVidia drivers:

Ctrl-Alt-F1 and log in to the system console
sudo service gdm stop
cd (to directory where your driver file is)
sudo sh ./xxxxxxxxxxxxxxxx (<-- your driver file)
(When script asks if you want to auto configure xorg, select Yes)
sudo init 6

Tim

Tim, for info - is init 6 the desktop runlevel?

Thanks.

---

### Post by ratcheer on 2010-02-05
No, it reboots the machine, which needs to be done after these procedures.

Tim

---

### Post by FrankVdb on 2010-02-05
Same problem here, have to reinstall my nVidia drivers. I've lost a lot of time with this kind of problems. I'm on a Dell XPS M1330 laptop.

Do other distributions have this kind of issues? I'm seriously considering another putting another distro on that laptop. I've had it.

---

