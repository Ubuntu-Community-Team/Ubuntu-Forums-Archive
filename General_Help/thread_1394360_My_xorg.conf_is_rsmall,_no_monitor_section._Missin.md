---
title: "My xorg.conf is rsmall, no monitor section. Missing options ?"
date: 2010-01-30
forum: General Help
---

### Post by pimseb on 2010-01-30
Hello,

While I was trying to improve my fonts config, I've opened my xorg.conf. Here is a copy :


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


It's really small and basic, isn't it ? I wanted to add dpi option into the monitor section but there is no such section :) 
I also find that my movies are not correctly displayed0
I'm using a Gigabyte 9600GT.
I've installed nvidia drivers when I was prompted when I launched ubuntu at the first time.
Am I missing something or everything is right ?
Thx

---

### Post by t0p on 2010-01-30
With 9.10, the devs decided to do away with xorg.conf  There's an explanation [here]("http://superuser.com/questions/51248/where-is-the-xorg-conf-file-in-karmic-koala-ubuntu-9-10").

---

### Post by mcduck on 2010-01-30
most of the settings are now automatically detected instead of having to define them in xorg.conf. Still, if you want to do any custom settings you can simply add them to xorg.conf just like before. :)

---

### Post by pimseb on 2010-01-30
ok so everything should be ok by default
thx :)

---

