---
title: "MAYDAY - computer not booting"
date: 2009-08-02
forum: General Help
---

### Post by fisheater on 2009-08-02
MAYDAY - computer not booting
Shoot. My computer (my main) is not booting after trying to mount my NAS.

Help.

What I did:
sudo aptitude install smbfs (this uninstalled 200= MB of stuff)
sudo mkdir /media/sharename
sudo nano /etc/nsswitch.conf
from this: hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
to this: hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4



then I stopped because I didnt understand where it was going. I rebooted and not it hangs at 'starting samba services'


How can I fix this?
Very least how can I get access to my files!

thx

FE

This is double posted in Main and networking. Sry.
[http://ubuntuforums.org/showthread.php?t=1217797](http://ubuntuforums.org/showthread.php?t=1217797)

---

### Post by russo.mic on 2009-08-02
Boot to a recovery console out of the boot menu, and do a 
sudo apt-get remove smbfs

---

### Post by fisheater on 2009-08-02
THANKS! That was 9 minutes of sheer terror. All my stuff was backed up, except for the docs that I am working on now!

That fixed the boot issue, I check my networks and network printer to see if it is all working.

Thanks again, you saved the day.

FE

/Close topic/

---

