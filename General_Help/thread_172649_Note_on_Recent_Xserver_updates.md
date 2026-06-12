---
title: "Note on Recent Xserver updates"
date: 2006-05-09
forum: General Help
---

### Post by rcarring on 2006-05-09
After the bad experience I had applying the series of recent xserver updates via the Update Manager, I used the command line method as root, that is to say apt-get update; and then apt-get upgrade.

What I found is that the upgrade does in fact trash server-xorg utterly. I then did apt-get install xorg-common as a sanity check and the system reported it was installed, and the latest version, then apt-get install xserver-xorg showed that the system had vaporized xserver-xorg and this had to be reinstalled.

Next I ran dpkg-reconfigure xserver-xorg and ran through a series of text based config screens. These are fairly simple, but the choices may not be so easy. Since I was running vmware I chose vmware as the video card detected and 1024 x 768 at 60htz and 24 color depth.

Finally I rebooted the machine and unlike the previous upgrade on another vm, I was able to boot straight into the desktop.

Please can the people in charge of the updates look into this, as a newbie would not necessarily know what to do when their xserver crashed spectacularly after updating. **

This applies to Breezy Badger 5.10 and not to Dapper Drake beta 2 6.06

** I freely admit this issue may be exclusively confined to users of vmware's browser-appliance.

---

### Post by felipe on 2006-05-10
*bump*

---

