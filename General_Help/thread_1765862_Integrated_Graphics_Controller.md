---
title: "Integrated Graphics Controller"
date: 2011-05-23
forum: General Help
---

### Post by caspar21 on 2011-05-23
Hello ubuntuforum.com members,

i'm facing on a big problem with my HP Probook 5320m laptop. My problem is that i can't find any video card drivers for my laptop. I'm trying to get my dual monitors to work in Monitor Preference, there are Samsung Electric Company 19'' and UNKNOWN monitor. My laptop is blank if I connect my monitor to it. Otherwise it displays the right thing.

I can't locate xorg.conf file - it does not exist in my system. If I try to create it with Xorg :1 -configure, i get this error:

```

(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
Number of created screens does not match number of detected devices.
  Configuration failed.

```

lspci -v | grep VGA shows:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
```

How can i create xorg.conf or what else should i do?
(Sorry for my bad english)

---

