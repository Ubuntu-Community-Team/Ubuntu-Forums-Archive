---
title: "System screwed after installing nvidia-glx-173"
date: 2009-07-02
forum: General Help
---

### Post by hambone79 on 2009-07-02
I have an older P3 machine with an NVidia video card in it that is running Ubuntu 9.04. I just ran the little Hardware Drivers application to let it setup the nvidia drivers for me and it has completely screwed up my system. After a reboot to let the drivers load, I'm now stuck without a GUI and I can't revert back to the old setup because I can't remove the damn Nvidia drivers. Every time I try to force the removal of the nivida packages I get this message:

```

Errors were encountered while processing:
 nvidia-glx-173
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can someone please tell me how to force the removal of this package or how to otherwise trick the system so I can reinstall it? I have tried everything I have found online and have used every combination of dpkg and apt commands to try and fix it.

---

### Post by synapsys on 2009-07-02
Have you tried this as root?

```
dpkg-reconfigure xserver-xorg
```

---

### Post by hambone79 on 2009-07-02
I get this output:
```

/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

```

---

### Post by wojox on 2009-07-02
May want to try 

```
sudo apt-get -install --reinstall xserver-xorg
```

---

### Post by hambone79 on 2009-07-02
That gives me the first error message again.

---

### Post by synapsys on 2009-07-02
```
apt-get remove xserver-xorg
apt-get purge xserver-xorg
apt-get install xserver-xorg
```

---

### Post by hambone79 on 2009-07-02
Same error message.

---

### Post by hambone79 on 2009-07-02
Is there some way I can just tell apt to forget that nvida-glx-173 exits?

---

### Post by hambone79 on 2009-07-02
Ok, I finally figured it out...it was looking for this file:

/usr/lib/xorg/modules/libGLcore.so

but it didn't exist. To make it uninstall nvidia-glx-173, I simply created a blank file for libGLcore.so and apt ran successfully.

Thanks for your help synapsys, it was greatly appreciated :)

---

### Post by synapsys on 2009-07-03
That's strange that re-installing xorg didn't re-install xorg libraries... i'll have to research that.... Sounds like I should ask YOU next time I have a graphics problem....

---

