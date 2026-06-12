---
title: "GM45 Chipset HDA Intel Sound Mic Issues"
date: 2010-06-04
forum: General Help
---

### Post by highflyr on 2010-06-04
New to Ubuntu. I've read all I can about the current mic issues with the Lucid 10.04 release. There does not seem to be any specific threads dealing with the GM45 chipset.

I've had sound out of speakers on fresh install, and have done every single line addition (individually) suggested with: 
```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

```to get microphone working. 

To:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
``` 
under Conexant (which is the only relation to the GM45, but it is a modem anyway?!) I believe the VT1720 is my sound though?

```
cat /proc/asound/card0/codec#* | grep Codec
```
returns:
Codec: VIA VT1702
Codec: Conexant HSF
Codec: Intel G45 DEVCTG

This is one of the only posts specific to hardware I've found [http://linmodems.technion.ac.il/bigarch/archive-tenth/msg00022.html](http://linmodems.technion.ac.il/bigarch/archive-tenth/msg00022.html)

Any advice? Or do I just wait until hardware is more specifically supported?

---

### Post by lisati on 2010-06-05
Not related to technical problems with the website (i.e. broken features), or a question pertaining to forum features.

Thread moved from "Forum Feedback and help" to "General help"

---

### Post by highflyr on 2010-09-02
bump. 

linux rox!! the only thing keeping me booting windose is skype (chipset mic issue) and silverlight / netflix

i get the silverlight issue, but have had no luck getting audio / mic record up.

---

