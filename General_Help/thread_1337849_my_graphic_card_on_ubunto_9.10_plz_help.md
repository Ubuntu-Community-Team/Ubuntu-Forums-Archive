---
title: "my graphic card on ubunto 9.10 plz help"
date: 2009-11-25
forum: General Help
---

### Post by 9th_tray on 2009-11-25
i need help on how to enable my graohic car on ubunto 9.10 cause i go to system admin and hardware driver and nothing shows up plz help

---

### Post by audiomick on 2009-11-25
Hallo again.
here is some info:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

and if that doesn't work, maybe this

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

hope that helps

---

### Post by 3rdalbum on 2009-11-25
The Hardware Drivers program needs to know what packages are available in the Ubuntu repositories. If your internet connection was not active during the install, then it probably doesn't have a list of packages.

Connect to the Internet. Go into Synaptic Package Manager and hit the Reload button; this will refresh the index of online packages. After it has done, quit Synaptic. Now Hardware Drivers should offer an appropriate Nvidia driver for you.

---

