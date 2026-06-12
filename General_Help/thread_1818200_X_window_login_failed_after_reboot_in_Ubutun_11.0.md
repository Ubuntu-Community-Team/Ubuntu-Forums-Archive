---
title: "X window login failed after reboot in Ubutun 11.0"
date: 2011-08-04
forum: General Help
---

### Post by feng@bnl.gov on 2011-08-04
I have been using Ubutu 11.0 X window for few months.  It works fine.
I shut down the system two days ago.  However, when I tried to boot it this 
morning, it does not pop up the X window for one to login anymore.
I can only use the recovery mode as a root.  However, I did not
change any X window configuration or update any X window related
packages since two months ago.  I did login as root to reinstall the
build-essential and gcc packages b/c some compiler tools were
missing.  Is it possible that some dependent packages were removed
when I type 'sudo apt-get remove build-essential' ?  I should have
typed 'sudo apt-get --reinstall install build-essential' instead.  Now it's
too late to correct the typing.

The following does not help.
1) sudo apt-get --reinstall install xserver-xorg
2) sudo apt-get --reinstall install xserver-xorg-core
3) dpkg-reconfigure xserver-xorg 

I am not sure if X server is broken.  I could no longer login as a remote user.
Any pointer would be greatly appreciated.

Sincerely,
Kate

---

