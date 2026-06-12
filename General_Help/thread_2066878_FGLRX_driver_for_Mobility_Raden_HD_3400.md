---
title: "FGLRX driver for Mobility Raden HD 3400"
date: 2012-10-05
forum: General Help
---

### Post by Fatwhale on 2012-10-05
Hey guys,

I'm currently trying to develop a 3D application using openFrameworks. But I am facing some problems because my graphic card isn't used to it's full potential.

Calling lspci | grep VGA gives me:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV620 [Mobility Radeon HD 3400 Series]

At first I have tried installing drivers using the option from the lubuntu menu. After rebooting my system says, that the drivers are activated but when I try to open the catalyst control center I get a error saying that my driver might not be correctly installed. 

After removing the driver I checked the AMD site and saw, that the mobility radeon hd 3400 is not supported by the current version of the driver. So I downloaded version 12.6 and installed it manually. But when I try to call "sudo aticonfig --initial" I get the following output (there are german parts which I tried to translate):

```
Found fglrx primary device section
PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: Warnung: Neuinstallation der Alternative /usr/lib/fglrx/ld.so.conf ist erzwungen, weil Linkgruppe x86_64-linux-gnu_gl_conf defekt ist.
update-alternatives: Warnung: Erstellung von /usr/bin/amdcccle wird übersprungen, weil die zugehörige Datei /usr/lib/fglrx/bin/amdcccle (der Link-Gruppe x86_64-linux-gnu_gl_conf) nicht existiert.
update-alternatives: Warnung: Erstellung von /usr/share/applications/ubuntu-amdcccle.desktop wird übersprungen, weil die zugehörige Datei /usr/share/fglrx/amdcccle.desktop (der Link-Gruppe x86_64-linux-gnu_gl_conf) nicht existiert.
update-alternatives: Warnung: Erstellung von /usr/share/applications/ubuntu-amdccclesu.desktop wird übersprungen, weil die zugehörige Datei /usr/share/fglrx/amdccclesu.desktop (der Link-Gruppe x86_64-linux-gnu_gl_conf) nicht existiert.
update-alternatives: Warnung: Erstellung von /etc/OpenCL/vendors/amdocl32.icd wird übersprungen, weil die zugehörige Datei /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (der Link-Gruppe x86_64-linux-gnu_gl_conf) nicht existiert.
update-alternatives: Warnung: Erstellung von /usr/bin/amdupdaterandrconfig wird übersprungen, weil die zugehörige Datei /usr/lib/fglrx/bin/amdupdaterandrconfig (der Link-Gruppe x86_64-linux-gnu_gl_conf) nicht existiert.
update-alternatives: Warnung: Erstellung von /usr/bin/amdxdg-su wird übersprungen, weil die zugehörige Datei /usr/lib/fglrx/bin/amdxdg-su (der Link-Gruppe x86_64-linux-gnu_gl_conf) nicht existiert.
update-alternatives: Warnung: /usr/lib/x86_64-linux-gnu/xorg/extra-modules wird nicht durch einen Link ersetzt.

Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-2
```

Translation:
```

Found fglrx primary device section
PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: Warning: Reinstallation of alternative /usr/lib/fglrx/ld.so.conf is forced, because linkgroup x86_64-linux-gnu_gl_conf is defect.
update-alternatives: Warning: Creation of /usr/bin/amdcccle skipped, because the file /usr/lib/fglrx/bin/amdcccle (of link-group x86_64-linux-gnu_gl_conf) does not exist.
update-alternatives: Warning: Creation of /usr/share/applications/ubuntu-amdcccle.desktop skipped, because the file /usr/share/fglrx/amdcccle.desktop (of link-group x86_64-linux-gnu_gl_conf) does not exist.
update-alternatives: Warning: Creation of /usr/share/applications/ubuntu-amdccclesu.desktop skipped, because the file /usr/share/fglrx/amdccclesu.desktop (of link-group x86_64-linux-gnu_gl_conf) does not exist.
update-alternatives:  Warning: Creation of /etc/OpenCL/vendors/amdocl32.icd skipped, because the file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link-group x86_64-linux-gnu_gl_conf) does not exist.
update-alternatives:  Warning: Creation of /usr/bin/amdupdaterandrconfig skipped, because the file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link-group x86_64-linux-gnu_gl_conf) does not exist.
update-alternatives:  Warning: Creation of /usr/bin/amdxdg-su skipped, because the file /usr/lib/fglrx/bin/amdxdg-su (of link-group x86_64-linux-gnu_gl_conf) does not exist.
update-alternatives: Warning: /usr/lib/x86_64-linux-gnu/xorg/extra-modules is not set by a link

Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-2
```

And a call of "fglrxinfo" gives me:

```
display: :0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
OpenGL version string: 2.1 Mesa 8.0.2
```

What can I do?
I want to use geometry shaders while developing but I can't get them to work and I think it's because of my driver problem.

---

