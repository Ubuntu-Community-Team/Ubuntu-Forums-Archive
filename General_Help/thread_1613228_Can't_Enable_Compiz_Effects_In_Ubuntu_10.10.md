---
title: "Can't Enable Compiz Effects In Ubuntu 10.10"
date: 2010-11-04
forum: General Help
---

### Post by khunt_999 on 2010-11-04
I have Ubuntu 10.10, dual booted, on my PC. I installed some ATI drivers using Synaptics Package Manager.

Now my driver shows it is working in "Additional Hardware". But when I try to turn on "Extra" graphic features, so I can use Compiz, it searches for drivers and then says Graphic driver not installed.

Please help me. :-(

---

### Post by 3Miro on 2010-11-04
Go to Apps -> Accessories -> Terminal and type:
```
 glxgears 
```

This should give you FPS in the hundreds.

You are not supposed to use Synaptic to install the ATI derivers, but rathert the Hardware Center. Right now, you may have either the wrong driver installed or the systme may be unaware of the right driver.

---

### Post by cpmman on 2010-11-04
To reset to original:

```
sudo apt-get install ppa-purge

sudo ppa-purge ppa:compiz/ppa


```

Log out.

Logging in again try compiz without installing any extra drivers.

---

### Post by khunt_999 on 2010-11-05
Got the ATI drivers working for Ubuntu. Now Compiz works like a charm. Thank you guys for your help.

It seemed like I had installed the wrong driver through Synaptics. I went to Additional Hardware. Removed the existing driver. Made Ubuntu install the driver on its own. Restarted my PC and it worked.

Thank you. :):):):)

---

