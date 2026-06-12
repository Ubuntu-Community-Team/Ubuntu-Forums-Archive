---
title: "alsa driver in maverick"
date: 2010-10-04
forum: General Help
---

### Post by bhavya juneja on 2010-10-04
Hi all,

It's just a simple query.
Can someone tell me which alsa driver are there in maverick?? I mean which version(1.0.23 or ..??) and are they supporting Intel HDA ALC269 sound cards.

Thanks in advance.

---

### Post by andrewthomas on 2010-10-04
```
andrew@790Fx:~$ aptitude show alsa-base
Package: alsa-base                       
State: installed
Automatically installed: no
Version: 1.0.23+dfsg-1ubuntu4
Priority: optional
Section: sound
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 524k
Depends: lsof (>= 4.64), module-init-tools (>= 3.2.1), linux-sound-base, udev
Recommends: alsa-utils
Suggests: apmd (>= 3.0.2-1), alsa-oss, oss-compat
Conflicts: alsa-utils (< 1.0.9a-4), discover (< 2.0.7-1), discover1 (< 1.7.3),
           lsof-2.2 (< 4.64), modutils (= 2.3.20-1)
Provides: alsa
Description: ALSA driver configuration files
 This package contains various configuration files for the ALSA drivers. 
 
 For ALSA to work on a system with a given sound card, there must be an ALSA
 driver for that card in the kernel. Linux 2.6 as shipped in linux-image
 packages contains ALSA drivers for all supported sound cards in the form of
 loadable modules. A custom alsa-modules package can be built from the sources
 in the alsa-source package using the m-a utility (included in the
 module-assistant package). Please read the README.Debian file for more
 information about loading and building modules. 
 
 ALSA is the Advanced Linux Sound Architecture.
Homepage: http://www.alsa-project.org/
```

This module is supported in the kernel.  What are you having problems with?

---

### Post by bhavya juneja on 2010-10-04
Thanks for replying, I have not yet switched to maverick but in lucid I was facing problems with sound and from searching a lot found that I should upgrade alsa to 1.0.23 (which was not default in lucid). 

I did that but there are some conflicts in flash player i.e. I can play sound only from one of either flash (youtube,..) or any music player(rhythmbox,banshee,vlc..).

My sound card is Intel HDA ALC269 on sony vaio VPCEB16FG.
I am hoping that it gets resolved in Maverick.

---

### Post by andrewthomas on 2010-10-04
Are you using pulseaudio?

---

### Post by bhavya juneja on 2010-10-04
Yes, I am using pulseaudio..

---

### Post by coibyxqx on 2010-10-05
No sound with my computer(acer4930+10.10rc amd64 alternative) as reported in [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/630835](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/630835).

---

