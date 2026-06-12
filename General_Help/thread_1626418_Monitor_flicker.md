---
title: "Monitor flicker"
date: 2010-11-20
forum: General Help
---

### Post by listvon9 on 2010-11-20
I bought a new ViewSonic 22 inch monitor but have terrible flickering problems. The monitor flickers once every couple of seconds and rapid flickering occurs when any kind of process is running. For example while downloading something, opening a new window/xterminal or even on clicking (but not while typing).

I am using Ubuntu 10.04 and have followed the instructions on [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)  to download install and config the latest drivers for nvidia (since I have 
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2))

Any suggestions/ideas?

Thanks.

---

### Post by dino99 on 2010-11-20
seems to be due to video driver not activated: system admin additional driver

open a terminal (Applications Acessories Terminal) and run:

sudo rm -f /etc/X11/xorg.conf

then open synaptic (system admin synaptic)
and remove/purge (right click) ALL the installed nvidia packages

then install: nvidia-current, nvidia-common, nvidia-settings (always with synaptic)

then reboot and check driver activation (nvidia-current might be)

---

### Post by listvon9 on 2010-11-20
dino99,

Thank you for your information.  Unfortunately it does not work.  One thing I did different from your suggestion was I used System->Admin->Hardware Drivers to download and installed the recommended nvidia driver.  This is because if I just follow your steps, after reboot I get a screen filled with cross-hatches!

---

### Post by listvon9 on 2010-12-02
hmm.... no takers? 

I have since upgraded to 10.10 and redone the steps mentioned by dino99 above. To no avail.

Is there any other possibility like hardware issues with the computer? 

I have a MSI wind with XP on it and I can use the external monitor as a second screen and it works perfect. so the monitor is healthy.

---

### Post by Spyderkid on 2010-12-02
Okay so try enableing the recommended driver and restart

also if your screen has any extensions plugs make sure there tight together.

---

### Post by listvon9 on 2010-12-02
Thank you spyderkid for your reply. 

 I assumed installing the latest driver, then using the Administration -> hardware drivers to activate the lastest driver would have done this. Is there anything else I should be doing?

dino99 also says in the post to check driver activation. How is that done. 

Note: I have already blacklisted a bunch of default drivers. so there is probably no interference from older drivers. Also they I have uninstalled / purged old driver.

Thanks again.

---

### Post by listvon9 on 2010-12-02
Actually I just checked and System->Administration->Additional Drivers no longer lists any nvidia drivers!! 

Any suggestions as to what I could try?

Thanks.

---

