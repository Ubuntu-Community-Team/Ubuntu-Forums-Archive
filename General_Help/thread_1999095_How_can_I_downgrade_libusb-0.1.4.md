---
title: "How can I downgrade libusb-0.1.4?"
date: 2012-06-07
forum: General Help
---

### Post by quickk on 2012-06-07
Hi everyone, 

   My hp M551DN printer keeps having random device communication errors (error 5012, as reported by the HP device manager).   After lots of searching, it seems this is related to libusb-0.1.4.   Apparently, downgrading to a previous version (2:0.1.12-14) can fix the problem.   How can I do this?   Synaptic does not provide the option to downgrade this package.

---

### Post by Enigmapond on 2012-06-07
What do you mean synaptic can't? You can always force a version..Package/Force Version...unless it's just not available for 12.04 (assuming you are running 12.04).

---

### Post by quickk on 2012-06-08
The option for "force version" in synaptic is greyed out.   Does this mean that I can't install an older version of the library?   Is there a way to manually do this?

Thanks for your help!

---

### Post by QuiGonJinn130 on 2012-06-08
sudo apt-get purge libusb-0.1.4

---

