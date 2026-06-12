---
title: "Avermedia H830"
date: 2011-04-21
forum: General Help
---

### Post by ljl69 on 2011-04-21
Hi,

Ubuntu 10.10
kernel 2.6.35-29
gnome 2.32.0

To install this usb tnt stick avermedia asks for loading a driver. I did it.

And asks for checking some prerequesits What does it mean ?

Prerequisits
    a. support linux kernel 2.6.29 or after.
Note: 1. This package is tested with MythTV against Ubuntu 10.04
      2. This package is tested with VLC v1.1.4 against Ubuntu 10.04 and 10.10
      3. This package is tested with mplayer and Kaffeine against Ubuntu 10.04 and 10.10
    b. make sure /lib/modules/`uname -r`/build exists
    c. make sure "dvb_frontend.h" exist in your Ubuntu.
    d. kernel modules dependency: videodev, videobuf-core, v4l2-common, videobuf-vmalloc,
           dvb-core, i2c-core, tda18271, snd_pcm, snd_timer, snd_page_alloc, snd, soundcore          

1. Install driver to system
    
    > sudo ./xxx_LinuxDrv_x86_vxxx-beta_Install.sh


i didnt find /lib/modules/'uname -r/build.


Thx for help

---

