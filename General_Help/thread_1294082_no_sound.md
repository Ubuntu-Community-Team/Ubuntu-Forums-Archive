---
title: "no sound?"
date: 2009-10-17
forum: General Help
---

### Post by Arminius on 2009-10-17
hey, I've had this problem before, and the only way I could fix it was by formatting and starting over.

my sound blaster Xfi was working fine, but with no warning suddenly there is no audo
I went to the directory and uninstalled the sound driver.
rebooted, then ran in terminal

"wget http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz"
"tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz"
"cd XFiDrv_Linux_Public_US_1.00"
"sudo apt-get install build-essential linux-headers-`uname -r`"
"make"
"sudo make install"

but still no audio.
last time this happened no one could fix it.
so hope someone can help incase this happens a 3rd time.

---

### Post by Arminius on 2009-10-22
bump

---

### Post by P4man on 2009-10-22
I guess each time you got a kernel upgrade, the driver stopped working. X-fi support in linux is still quite bad.

There might be an elegant way to avoid recompiling the drivers after a kernel upgrade, but i dont know it. I would only suggest you consider using the onboard sound (if any), rather than the x-fi. With the help of a friend do a double blind test and see if you can hear any difference. I bet you cant.

---

### Post by Arminius on 2009-10-22
no, wasn't the kernal, I removed the driver, then reinstalled completely.
still no sound
only way to solve it was to reinstall everything
it's running fine now, but it's the 2nd time it's happened, and if anyone can suggest a fix before it happens a 3rd time?

if not, what sound card has the best linux support?

---

