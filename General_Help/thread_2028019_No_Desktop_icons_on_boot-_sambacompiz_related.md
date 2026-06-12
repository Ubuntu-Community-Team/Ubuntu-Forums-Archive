---
title: "No Desktop icons on boot- samba/compiz related"
date: 2012-07-17
forum: General Help
---

### Post by steveray100 on 2012-07-17
when I boot up, I have an empty desktop, if I run " killall nautilus" in terminal to hopefully get my icons back this is what happens:

steveray100@steveray100-desktop:~$ killall nautilus
nautilus: no process found

I then run nautilus:

steveray100@steveray100-desktop:~$ nautilus
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 1.4.0
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


I get my icons back, a nautilus window opens, and I also get a shade effect from the upper panel that has to do with the compizconfig setting. (Avanced Desktop Effects Settings)

I am the only user/administrator of the machine.

any help? why is nautilus not loading at boot? how do you enable user sharing if need be? And why would i need to if I am the only user?

---

