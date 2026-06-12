---
title: "OpenVZ on 9.10 Repository problem"
date: 2010-02-12
forum: General Help
---

### Post by RichyB on 2010-02-12
Hi im trying to install **OpenVZ **onto Ubuntu 9.10 im not sure if its the fiesty or hardy that is refered to in this article ```
https://help.ubuntu.com/community/OpenVZ
```

iv put ```
deb http://debian.systs.org/ stable openvz
``` into sources file and ran update which gave me this result  ```
Ign http://debian.systs.org stable Release
Ign http://debian.systs.org stable/openvz Packages
Ign http://debian.systs.org stable/openvz Packages
Err http://debian.systs.org stable/openvz Packages
  404  Not Found

```

I then as the guide says tried to run ```
sudo apt-get install ovzkernel-2.6.18
```

at which point i get this error
```
richy@VirtualizationSvr:~$ sudo apt-get install ovzkernel-2.6.18
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ovzkernel-2.6.18

```

anyidea where im going wrong? or is there a way i can manualy download it and install it using wget

Im sorry if this sounds like a noob question but i guess i am a noob to ubuntu :o)

---

