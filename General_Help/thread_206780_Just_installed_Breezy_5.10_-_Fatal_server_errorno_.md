---
title: "Just installed Breezy 5.10 - Fatal server error:no screens found"
date: 2006-06-30
forum: General Help
---

### Post by eggmanpete on 2006-06-30
just installed ubuntu 5.10 from 64bit CD, went through install process fine and i get a fatal server error with x server.
the message i get is:

**bunch of system spec**

(EE) No devices found *(or something similar)*
Fatal server error: 
No screens found

my system spec is:
A64 3700+
Asrock 939SLI32-eSATA2
nVidia 
7900GT

---

### Post by invalid on 2006-06-30
[QUOTE=eggmanpete]just installed ubuntu 5.10 from 64bit CD, went through install process fine and i get a fatal server error with x server.
the message i get is:

**bunch of system spec**

(EE) No devices found *(or something similar)*
Fatal server error: 
No screens found

my system spec is:
A64 3700+
Asrock 939SLI32-eSATA2
nVidia 
7900GT[/QUOTE]
Try reconfiguring X with the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by atoponce on 2006-06-30
[quote=eggmanpete]just installed ubuntu 5.10 from 64bit CD, went through install process fine and i get a fatal server error with x server.
the message i get is:

**bunch of system spec**

(EE) No devices found *(or something similar)*
Fatal server error: 
No screens found

my system spec is:
A64 3700+
Asrock 939SLI32-eSATA2
nVidia 
7900GT[/quote]

Make sure you are using the correct video card driver.  For nVidia, i believe it is 'nv'.  If that doesn't work, try vesa.  Use the command invalid mentioned for reconfiguring your X.

---

### Post by eggmanpete on 2006-06-30
ive tried to reconfigure the xserver using that command, no luck. i will try vesa soon.

---

### Post by ifokkema on 2006-07-01
[QUOTE=eggmanpete]ive tried to reconfigure the xserver using that command, no luck. i will try vesa soon.[/QUOTE]
See this:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
to install nVidia drivers that should get you better support (3D accelleration).

---

