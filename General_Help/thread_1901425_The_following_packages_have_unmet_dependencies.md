---
title: "The following packages have unmet dependencies"
date: 2011-12-28
forum: General Help
---

### Post by the_blue_box on 2011-12-28
I have know idea what I've gone and done :(

When ever I try to install the blender build dependencies I get...

```
The following packages have unmet dependencies.
 libavcodec-dev : Depends: libavcodec53 (>= 4:0.7.3-2u1~ppa1) but it is not going to be installed or
                           libavcodec-extra-53 (>= 4:0.7.3) but 4:0.7.2.1ubuntu3~ppa1 is to be installed
 libavdevice-dev : Depends: libavdevice53 (>= 4:0.7.3-2u1~ppa1) but 4:0.7.2-1ubuntu1 is to be installed or
                            libavdevice-extra-53 (>= 4:0.7.3) but it is not going to be installed
 libavformat-dev : Depends: libavformat53 (>= 4:0.7.3-2u1~ppa1) but 4:0.7.2-1ubuntu1 is to be installed or
                            libavformat-extra-53 (>= 4:0.7.3) but it is not going to be installed
 libavutil-dev : Depends: libavutil51 (>= 4:0.7.3-2u1~ppa1) but it is not going to be installed or
                          libavutil-extra-51 (>= 4:0.7.3) but 4:0.7.2.1ubuntu3~ppa1 is to be installed
 libswscale-dev : Depends: libswscale2 (>= 4:0.7.3-2u1~ppa1) but 4:0.7.2-1ubuntu1 is to be installed or
                           libswscale-extra-2 (>= 4:0.7.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I never had this problem before :(

How on Earth can I fix it :confused:

Any help would be greatly appreciated.

---

### Post by utnubuuser on 2011-12-28
synaptic has a filter for sorting out broken packages...

System>>Administration>>Synaptic Package Manager>>Custom>>Broken...

---

