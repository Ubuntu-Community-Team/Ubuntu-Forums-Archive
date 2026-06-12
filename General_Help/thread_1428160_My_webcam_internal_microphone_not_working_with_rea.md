---
title: "My webcam internal microphone not working with realtek new sound driver"
date: 2010-03-12
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-03-12
My webcam internal microphone not working with realtek new sound driver. My laptop is Asus G1S Any ideas how to fix this?

---

### Post by Lukasz Tarkowski on 2010-03-12
I have simply rebuild my alsa-source 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Using alsa-source

    * Open up a shell: (note: module-assistant is optional, it will compile the package for you)
    *

      Type sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
    *

      Type sudo dpkg-reconfigure alsa-source

Then sudo module-assistant a-i alsa-source

---

