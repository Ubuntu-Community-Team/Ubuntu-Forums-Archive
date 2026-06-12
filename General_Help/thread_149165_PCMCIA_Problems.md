---
title: "PCMCIA Problems"
date: 2006-03-23
forum: General Help
---

### Post by joemite on 2006-03-23
All,
I'm using Kubuntu 5.10 on an iBook G3 500Mhz. I'm having difficulty enabling my Orinoco Airport card, which I have traced down to a problem with PCMCIA Services. Any insight would be appreciated! Thank You!

Here is what I have so far:

me@localhost:/etc$ sudo /etc/init.d/pcmcia restart
 * Shutting down PCMCIA services... [ ok ]
 * Starting PCMCIA services... [fail]

me@localhost:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth/Pangea GMAC (Sun GEM

me@localhost:~$ lsmod
Module                  Size  Used by
isofs                  40120  0
udf                    96612  0
nls_base                8416  2 isofs,udf
rfcomm                 45852  0
l2cap                  28356  5 rfcomm
bluetooth              60712  4 rfcomm,l2cap
cpufreq_userspace       5356  1
cpufreq_stats           6468  0
cpufreq_powersave       1888  0
cpufreq_ondemand        7580  0
cpufreq_conservative     8868  0
pcmcia                 33416  0
yenta_socket           27084  0
rsrc_nonstatic         13568  1 yenta_socket
pcmcia_core            58480  3 pcmcia,yenta_socket,rsrc_nonstatic
ipv6                  300456  6
af_packet              20840  2
tsdev                   9120  0
ohci1394               40436  0
uninorth_agp           10952  1
agpgart                38876  1 uninorth_agp
dm_mod                 67124  1
evdev                  11936  5
sr_mod                 20964  0
cdrom                  47420  1 sr_mod
snd_powermac           53700  1
snd_pcm_oss            65024  0
snd_mixer_oss          22048  1 snd_pcm_oss
snd_pcm               106020  2 snd_powermac,snd_pcm_oss
snd_timer              28388  1 snd_pcm
snd                    63668  7 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11364  1 snd
snd_page_alloc         11880  1 snd_pcm
sbp2                   26024  0
scsi_mod              171488  2 sr_mod,sbp2
ieee1394              434320  2 ohci1394,sbp2
apm_emu                 7916  1
md                     53588  0
ext3                  143272  1
jbd                    70456  1 ext3
mbcache                11076  1 ext3
sungem                 37220  0
sungem_phy              9728  1 sungem
ohci_hcd               25188  0
usbcore               137812  2 ohci_hcd
ide_disk               20544  2
unix                   31124  284

---

### Post by Cedfelix on 2006-03-23
Don't know if this will help you, but it got me up and running with a PCMCIA wireless card. 

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Hope it helps.

---

### Post by joemite on 2006-03-23
Thanks for the link -- there is a lot of useful information in there.

Unfortunately, none of it helps/applies.

Here's the output when I run: sudo cardctl ident
open_sock(): No such device

Also, I do want to mention that the wireless card works when I boot to OSX, so I know that my PCMCIA controller works fine. This isn't a hardware issue.

Thank You for any suggestions.

---

