---
title: "There is no sound (Ubuntu 10.04)"
date: 2011-01-03
forum: General Help
---

### Post by asifnaz on 2011-01-03
asif@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
asif@ubuntu:~$ 


If you can identify the problem...???

Thank you

---

### Post by arpoodle on 2011-01-03
Similar problem here.

Did a regular apt-get update/upgrade last week and since then, sound had  stopped working. (the upgrade also screwed my video settings but that  was a bit hacky to start with)

```

root@hiro:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@hiro:~# uname -a
Linux hiro 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
root@hiro:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
root@hiro:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
root@hiro:~# lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
02:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)
root@hiro:~# cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ID 665
root@hiro:~# 


 
```Hardware is a Dell XPS 17 laptop.

I did some digging and this seemed to have fixed it.

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)


```
to install the latest driver modules.

---

### Post by asifnaz on 2011-01-04
> **arpoodle said:**
> Similar problem here.

Did a regular apt-get update/upgrade last week and since then, sound had  stopped working. (the upgrade also screwed my video settings but that  was a bit hacky to start with)

```

root@hiro:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@hiro:~# uname -a
Linux hiro 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
root@hiro:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
root@hiro:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
root@hiro:~# lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
02:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)
root@hiro:~# cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ID 665
root@hiro:~# 


 
```Hardware is a Dell XPS 17 laptop.

I did some digging and this seemed to have fixed it.

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)


```to install the latest driver modules.

Thank you so so much . I really appreciate your help .

---

### Post by agilius on 2011-01-27
```
:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-28-generic
```

This is what I get when I try to update and install the alsa driver... Any tips? 

Thanks!

---

### Post by m3n3chm0 on 2011-01-27
waiting for the linux-alsa-driver-modules-2.6.32-28-* 

... :guitar:

---

### Post by patpaa on 2011-01-28
> **m3n3chm0 said:**
> waiting for the linux-alsa-driver-modules-2.6.32-28-* 

... :guitar:
Me too.

---

### Post by mastablasta on 2011-01-28
10.04? why not upgrade alsa? follow this guide:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
might take some time. be patientand download all the packages you need.
 
if it works make sure you lock the alsa packages in synaptic or one of ubuntu updates might overwrite them....

---

