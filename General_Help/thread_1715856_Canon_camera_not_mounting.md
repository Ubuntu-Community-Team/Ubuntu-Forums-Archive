---
title: "Canon camera not mounting"
date: 2011-03-27
forum: General Help
---

### Post by nightwolf2k5 on 2011-03-27
Hello there,

I have a canon camera and it used to mount fine on kubuntu. However, due to my lack of ram, I shifted to xubuntu.
When I try to mount the camera now, nothing happens.
lsusb gives me this
```

:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 024: ID 04a9:319a Canon, Inc. EOS 7D
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I saw some previous posts that mentioned that using gThumb or fspot solved the issue for some others but my system does not seem to recognise the camera.

It would be great if someone could help me with this :(

[edit]
Hello, all that was needed was the installation of digiKAM and now it works fine!
[/edit]

---

