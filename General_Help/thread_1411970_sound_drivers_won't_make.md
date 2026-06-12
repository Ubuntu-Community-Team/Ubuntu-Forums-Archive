---
title: "sound drivers won't make"
date: 2010-02-20
forum: General Help
---

### Post by keth802 on 2010-02-20
i cd to the directory and then i use ./configure --with-cards=hda-intel. that works. i then type make and get this: ```
make dep                                                   
make[1]: Entering directory `/home/jeff/Downloads/alsa-driver-1.0.22.1'
make[2]: Entering directory `/home/jeff/Downloads/alsa-driver-1.0.22.1/include'
make -C sound prepare                                                          
make[3]: Entering directory `/home/jeff/Downloads/alsa-driver-1.0.22.1/include/sound'
make prepare2
make[4]: Entering directory `/home/jeff/Downloads/alsa-driver-1.0.22.1/include/sound'
make[4]: Nothing to be done for `prepare2'.
make[4]: Leaving directory `/home/jeff/Downloads/alsa-driver-1.0.22.1/include/sound'
make[3]: Leaving directory `/home/jeff/Downloads/alsa-driver-1.0.22.1/include/sound'
make[2]: Leaving directory `/home/jeff/Downloads/alsa-driver-1.0.22.1/include'
make[2]: Entering directory `/home/jeff/Downloads/alsa-driver-1.0.22.1/acore'
copying file alsa-kernel/core/info.c
/home/jeff/Downloads/alsa-driver-1.0.22.1/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/jeff/Downloads/alsa-driver-1.0.22.1/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/jeff/Downloads/alsa-driver-1.0.22.1'
make: *** [include/sndversions.h] Error 2
```

---

### Post by keth802 on 2010-02-20
never mind. my dumb rear end didn't install build-essential :( its fixed now :)

---

### Post by jsriz on 2010-02-20
plz mark d tread as solved

---

