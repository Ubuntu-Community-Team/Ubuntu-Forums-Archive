---
title: "headphones work-speakers don't except when audioCD plays"
date: 2012-08-12
forum: General Help
---

### Post by Aardvark007 on 2012-08-12
Edubuntu 11.10 on HP desktop with AMD Sempron CPU version 15.15.2
Am a newbie but entered "sudo lshw" in terminal after reading 25 chapters on Linux. This produced audio device SBx00 Azalia(intel HDA) version 00 with 64bit width clocked at 33Mhz. Configuration says: driver=HDA Intel, Latency=32. Motherboard is Hewlett-Packard 3029h. The computer is a low profile desktop which has run Windoze Vista until I converted to Edubuntu only. In Windows both the regular speakers and headphone jack worked but in linux, only the headphones produce sound with the lone exception that a store bought AudioCD will play and activate both speakers and headphones. Rthymbox, Banshee, VLC all refuse to give sound on the speakers. All produce fantastic audio on the headset.  I've tried switching from analog to digital and back withing the software configurations but no joy. I checked a physical wire runs from the  speakers to the motherboard and it does. Any ideas would be appreciated.:confused:

---

### Post by Zvlwab on 2012-08-12
Run the following command:
```
pavucontrol
```
If it doesn't exist, install it first:
```
sudo apt-get install pavucontrol
```

Navigate to Playback. It should show a list of program's running that produce sound. Make sure those program's use the right output.

---

