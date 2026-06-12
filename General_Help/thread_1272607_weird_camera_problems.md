---
title: "weird camera problems"
date: 2009-09-22
forum: General Help
---

### Post by chucky chuckaluck on 2009-09-22
mounting appears to be the core issue. when i open nautilus, my camera appears in the index. i right-click and select 'mount' at which time it has given me a variety of error messages ("can't lock device", etc.). oddly, the camera then appears to be mounted and i can access my pics. nautilus is the only file manager that lists the camera in the index. dolphin, konqueror and thunar do not. when i try to mount my camera using a terminal, i get this error message "mount: special device /dev/sdb1 does not exist". this is what i have in my /etc/fstab

/dev/sdb1  /home/fuscia/camera vfat user,noauto,exec 0  0

the problem seems to be further confused when apps like f-stop, digikam and kamera are installed. i've tried all this with my camera set at both PTP and mass storage.

---

### Post by ImmortalSoFar on 2009-10-03
Same problem here. My Canon is detected correctly, auto-mounts but fails to lock. It is inaccessible from file manager but downloads fine via f-spot photo manager.

---

