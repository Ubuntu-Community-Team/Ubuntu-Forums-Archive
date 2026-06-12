---
title: "Ubuntu 12.04: Unmet Dependencies for Audacious :-("
date: 2012-04-28
forum: General Help
---

### Post by The Bright Side on 2012-04-28
Hey guys,

I tried to install my favourite audio player Audacious from the webupd8 PPA today, and Software Centre gives me the following error:

```

The following packages have unmet dependencies:

audacious: Depends: libaudclient2 (= 3.2.2-1~webupd8~precise1) but 3.2.2-1~webupd8~precise1 is to be installed
           Depends: libaudcore1 (= 3.2.2-1~webupd8~precise1) but 3.2.2-1~webupd8~precise1 is to be installed
           Depends: libice6 (>= 1:1.0.0) but 2:1.0.7-2build1 is to be installed

```

Do you know what I can do in this case? Hope you can help me!

---

### Post by jerrrys on 2012-04-28
sudo apt-get update

and then try to install the PPA

---

### Post by The Bright Side on 2012-04-28
Thanks! The PPA is already installed. I disabled it and tried to install the version of Audacious present in the Ubuntu repos, but it gave me the same error.

After re-activating the webupd8 PPA, I still get the same error.

---

### Post by The Bright Side on 2012-04-28
It actually happens for VLC as well. From the terminal:

The following packages have unmet dependencies:
 vlc : Depends: libva-x11-1 (> 1.0.15~) but it is not going to be installed
       Depends: libva1 (> 1.0.15~) but 1.0.14-1 is to be installed
       Recommends: vlc-plugin-notify (= 2.0.1+git20120427+r189-0~r36~precise1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.1+git20120427+r189-0~r36~precise1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

