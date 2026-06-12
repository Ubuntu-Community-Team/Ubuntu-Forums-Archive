---
title: "ubuntu 10.10 and Brother dcp-j125"
date: 2010-10-24
forum: General Help
---

### Post by DrStrom on 2010-10-24
hi,
i just discovered that i cant scan with my Brother DCP-J125. Under  Ubuntu 10.04 was it possible. I reinstalled the driver from Brother  brscan3  and the brscan keys. I add the lines to to the libsane.rules. I  can find my printer with "lsusb" i find it with sane-find-scanners but  when i start sane it wouldn’t find any scanner.
what did I wrong or what can i do to find out where is something missing, btw the printer works.

---

### Post by robbielink on 2010-11-22
I had this same problem with my Brother MFC420CN. Printed fine, no scanner since update to 10.10.
Check your installed packages. My scanner uses brscan2 but I saw that I also had brscan installed which synaptic claimed was the CUPS package for that scanner but it is actually another scanner package for different models. You can't have both. I uninstalled brscan, restarted computer (don't know if that was necessary), everything works fine now.
You should only have your brscan3 package and not brscan - if it's there I suspect it was somehow installed with the 10.10 update.

---

