---
title: "Diablo LOD Mount Issues W/ Natty(wine)"
date: 2011-05-15
forum: General Help
---

### Post by amnite on 2011-05-15
Im trying to install my D2 expansion w/ wine. When im almost at the end of installation D2 installer no longer recognizes my mounted disc. I eject and re-insert and then linux will no longer read a disc has been inserted and wont mount. It wont mount any cd while while the installer is running. It happens in the same spot everytime so i dunno... I try going to wine config and updating devices to where it would normally be but if Linux wont mount it, it doesnt matter....

---

### Post by amnite on 2011-05-15
I just tried to mount via konsole, mount /dev/sr0 and get an error cannot find in etc/fstab or etc/mtab

---

### Post by amnite on 2011-05-15
Thx for the help guys... lol jk. OK for anybody with the same problem here is the solution. Use k3b to create a copy of the expansion disk. using Konsole mount your iso copy into a folder anywhere called Expansion. Through wine config change your drive path to your mounted iso. WHAM!!!

---

