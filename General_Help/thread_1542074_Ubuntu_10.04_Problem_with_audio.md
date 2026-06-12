---
title: "Ubuntu 10.04 Problem with audio"
date: 2010-07-30
forum: General Help
---

### Post by newmoon_h on 2010-07-30
Hi, Im using Ubuntu 10.04 and having an annoying problem with sound. Symptoms of the this problem is when I fresh boot into Ubuntu I can listen audio with any media players. But after spending some times when I try to play audio, it does not sound. Say I'm trying to listen a mp3 in rhythmbox, when I click the play button I dont hear any music and the progress bar of the music player does not move too. I have tried to listen music with other software too like VLC, MPlayer, Totem, and the same thing happens, no sound comes and progress bar of the players does not move either. I tried to play videos too. In video's case I see the video without any audio and video progress bar moves in that case. It seems like audio driver stops working after some time. I experienced this problem for the first time when I was using chromium browser and it crashed for no reason. After crashing the chromium browser I restarted the browser and started rhythmbox to listen mp3 but I experienced above problem. I then restarted the pc thinking that after a fresh boot this problem will get solved. And it did for a short time and again I experienced no audio. After this when I give fresh boot I can listen to any audio and after sometimes audio do not occur. Please help me to fix this problem.

---

### Post by lidex on 2010-07-30
Is this an upgrade or fresh install?
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by newmoon_h on 2010-07-31
Thanks for the reply. Today I found another issue regarding this problem. When after fresh boot I played mp3 via rhythmbox it played well. After listening it I clicked the upper panel's rhythmbox icon and unchecked play. Later I again wanted to listen to another music and now it is not working. Do u think my rhythmbox got corrupt??


According to your asking, I'm copying the whole terminal after pasting your inputs.


heemel@heemel-desktop:~$ uname -a
Linux heemel-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
heemel@heemel-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
heemel@heemel-desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
heemel@heemel-desktop:~$ head -n 1 /proc/asound/card*/codec#*^C

 
And Ubuntu 10.04 was a fresh install. Note that after installing everything worked fine. I'm just experiencing this problem for only 3 days. I have fresh installed it 7 days ago. 

My PC is a custom built desktop. The configuration is: 

Intel Pentium E5200 2.5 Ghz Processor
Biostar G31 M7 TE Motherboard
2 * 1GB Transcend DDR2 Ram 800 Bus
Samsung Sata 1 TB HDD
ATI Radeon HD 4670 PCI Ex Graphics Card
TP Link Ethernet Card
Realtek ALC 662 Internal Sound Chip
Benq 16x DVD RW
350 Watt PSU

---

### Post by lidex on 2010-07-31
How about these outputs:
```
cat /var/log/messages
sudo dmidecode -t bios
sudo dmidecode -t baseboard
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by newmoon_h on 2010-07-31
Okay. Here it goes.

******************************************************************************************************

heemel@heemel-desktop:~$ cat /var/log/messages
Aug  1 01:12:28 heemel-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="763" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug  1 01:12:28 heemel-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="763" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug  1 01:52:40 heemel-desktop kernel: [ 3696.422762] ata3: soft resetting link
Aug  1 01:52:40 heemel-desktop kernel: [ 3696.592355] ata3.00: configured for UDMA/133
Aug  1 01:52:40 heemel-desktop kernel: [ 3696.592372] ata3: EH complete
Aug  1 01:52:48 heemel-desktop kernel: [ 3704.103929] ata3: soft resetting link
Aug  1 01:52:48 heemel-desktop kernel: [ 3704.272361] ata3.00: configured for UDMA/133
Aug  1 01:52:48 heemel-desktop kernel: [ 3704.272377] ata3: EH complete
heemel@heemel-desktop:~$ sudo dmidecode -t bios
[sudo] password for heemel: 
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 080014 
    Release Date: 04/10/2009
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 8.14

Handle 0x000D, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1


****************************************************************************************************

---

### Post by lidex on 2010-08-01
What aboutthis one:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by newmoon_h on 2010-08-03
Hey the problem automatically got fixed. I have not experienced the problem any more. Thanks for your help.

---

### Post by spxavales on 2010-09-02
Exact same problem here :((.
Any help would be appreciated..

Edit: I just realized that if i have firefox closed, then sound works fine... o.O
Any ideas?

---

