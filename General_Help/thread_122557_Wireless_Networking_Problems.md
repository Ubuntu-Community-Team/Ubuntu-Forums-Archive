---
title: "Wireless Networking Problems"
date: 2006-01-27
forum: General Help
---

### Post by Zygen on 2006-01-27
Well, after scouring the internet for the past couple of days, I decided that maybe I should post here.  The problem is that I recently bought a MSI Dual Net Card that supports bluetooth and 802.11b/g.  It apparently uses an rt2500 driver that Ubuntu loaded out of the box.  So I connect to the router and everything seems to work.  But the problem is that I get spotty access at best to most everything.  Gaim won't connect, Google won't even load, but for some reason I can visit the Ubuntu forums and a handful of other sites like the Tech Report.  I can ping everything perfectly and use wget, and in general it seems that it works flawlessly if I don't have more than a few connections going at once.

So I installed ndiswrapper and the rt2500 driver for it, which worked the same.  So then I got the newest rt2500 from cvs, but still no dice.  I'm completely out of idea's for what could be causing this.  It's not a signal strength issue either, since it stays at ~75-80% most of the time.  I'm using a 64-bit processor, but the 32-bit version of Ubuntu, and the latest (2.6.12-10-k7) Ubuntu kernel.  My next move might be to compile a new enough kernel to use the rt2x00 driver, but I have a gut feeling that that won't work either.

---

### Post by zuzuzzzip on 2007-07-31
I also have problems and this is the only topic I found with this card...
anyone else having troubles and perhaps a fix?
I can see the networks and it says connected but I cannot see google or anything.. :S

---

### Post by zuzuzzzip on 2007-08-04
*bump*

---

### Post by Hoenheim on 2007-08-04
The rt2500 driver is for cnet rt2500 wlan card, so you could probably try to find a driver on msi website for your dual card.

---

### Post by eggdeng on 2007-08-04
I had issues with a wireless usb dongle with this chip on Edgy. At first it worked intermittently with the bundled driver but performance degraded rapidly. I installed the rt2500usb driver under ndiswrapper but the story was the same. Eventually (lsmod) I found that Edgy was still loading the bundled driver (it's rt73usb or something similar) so I blacklisted it, whereupon Edgy stopped recognising the dongle altogether, no green led, no nothing. In the end I had to go for new hardware :(

---

### Post by eggdeng on 2007-08-04
@zuzuzzzip
```
I can see the networks and it says connected but I cannot see google or anything.. :S
```
Can you ping the router?

---

### Post by zuzuzzzip on 2007-08-04
> **eggdeng said:**
> @zuzuzzzip
```
I can see the networks and it says connected but I cannot see google or anything.. :S
```Can you ping the router?
nope

---

### Post by eggdeng on 2007-08-04
All I can suggest is using iwlist to check the channel / frequency, mode etc and iwconfig to set parameters if you see any anomalies. Do ```
man iwlist
``` or ```
man iwconfig
``` if you need more info on the commands. Sorry not to be of more help.

---

### Post by zuzuzzzip on 2007-08-04
iwconfig says:
```
ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-223 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
and as i said, i can see the networks, but not able to connect...
```
ra0       Scan completed :
          Cell 01 - Address: 00:18:84:16:AD:C9
                    Mode:Managed
                    ESSID:"FON_Aireys"
                    Encryption key:off
                    Channel:1
                    Quality:0/100  Signal level:-71 dBm  Noise level:-223 dBm
          Cell 02 - Address: 00:18:84:16:AD:CA
                    Mode:Managed
                    ESSID:"PRIV_Aireys"
                    Encryption key:on
                    Channel:1
                    Quality:0/100  Signal level:-71 dBm  Noise level:-222 dBm
          Cell 03 - Address: 00:0F:66:4C:F6:2A
                    Mode:Managed
                    ESSID:""
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-79 dBm  Noise level:-222 dBm

```

---

### Post by eggdeng on 2007-08-04
> Mode:Managed  Frequency=2.412 GHz
First two networks on your list are on Channel 1 which corresponds to a frequency of 2.412MHz. Assuming your card knows the essid for either of these, it *should* be able to connect. You can try
```
iwconfig ra0 essid FON_Aireys mode Managed channel 1 ap 00:18:84:16:AD:C9 commit
```
but to be honest, with this card, I wouldn't get my hopes up .

---

### Post by zuzuzzzip on 2007-08-04
I know the card sucks but could you tell me why :D
and what I should get (the most 1337 is good ;))
now when I type in that command I can see my connection's strength in the notification bar! but when I click on it, it just doesn't do anything...

---

### Post by eggdeng on 2007-08-05
If you run ```
lsmod
```you'll probably see that ubuntu is loading a driver called rt73 to deal with the card. It almost but doesn't quite work. I tried using the rt2500usb drivers with ndiswrapper. They installed fine but when I blacklisted the native driver, ubuntu stopped detecting the card. In the end, I wondered if the usb wireless problem might have as much to do with the usb aspect as the wireless. 
My solution was to forget about usb dongles and get hold of a wireless access point which can be configured to act as a bridge. The beauty is that it connects to the ethernet card and has the same IP address, at the same time as it acts as a wireless reciever. So you get [COLOR="Red"]wireless networking via the ethernet card[/COLOR]. Drawbacks are that it costs about 50 euros and that you need somewhere to plug in the power supply. But it is 100% reliable.
If you prefer to stick with usb, there is a list of supported cards at [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported).

---

### Post by zuzuzzzip on 2007-08-05
The thing is I don't have a usb dongle, just the MSI Dualnet PCI Card (BT+802.11b/g). The card sucks though (it came for free with the mobo)

lsmod
```
Module                  Size  Used by
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
ppdev                  11272  0 
cpufreq_ondemand       10640  0 
cpufreq_stats           8416  0 
freq_table              6336  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     9736  0 
cpufreq_powersave       3072  0 
cpufreq_userspace       6176  0 
dev_acpi               17028  0 
tc1100_wmi              9224  0 
pcc_acpi               15616  0 
sony_acpi               7064  0 
asus_acpi              19756  0 
battery                12040  0 
dock                   11992  0 
ac                      6920  0 
container               6144  0 
video                  19080  0 
button                 10016  0 
backlight               8448  1 asus_acpi
sbs                    17856  0 
i2c_ec                  6912  1 sbs
ipv6                  307456  14 
af_packet              27020  2 
ndiswrapper           239608  0 
sbp2                   26628  0 
lp                     15048  0 
fuse                   51888  13 
snd_ca0106             39968  4 
snd_ac97_codec        117848  1 snd_ca0106
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  6 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  15 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
sky2                   47880  0 
hci_usb                20636  2 
rt2500                202088  1 
nvidia               5659736  32 
bluetooth              62468  7 rfcomm,l2cap,hci_usb
ac97_bus                3968  1 snd_ac97_codec
snd_page_alloc         11792  2 snd_ca0106,snd_pcm
psmouse                43536  0 
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
serio_raw               9092  0 
i2c_nforce2             7680  0 
i2c_core               26496  3 i2c_ec,nvidia,i2c_nforce2
k8temp                  7552  0 
pcspkr                  4736  0 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
tsdev                  10112  0 
evdev                  13056  4 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
ide_disk               18304  2 
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
sd_mod                 25092  11 
usbhid                 29088  0 
hid                    34048  1 usbhid
generic                 6532  0 [permanent]
amd74xx                16944  0 [permanent]
usb_storage            80448  2 
libusual               22184  1 usb_storage
ata_generic            10628  0 
floppy                 67944  0 
ohci1394               38088  0 
ieee1394              369784  2 sbp2,ohci1394
sata_sil24             17924  0 
forcedeth              48776  0 
ehci_hcd               37004  0 
ohci_hcd               24196  0 
usbcore               154416  8 ndiswrapper,hci_usb,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
sata_nv                24196  5 
libata                137000  3 ata_generic,sata_sil24,sata_nv
scsi_mod              166968  5 sbp2,sg,sd_mod,usb_storage,libata
thermal                16912  0 
processor              34952  1 thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

```
don't know if this makes any sense to you. It seems like it's using rt2500 though...
weird.

do you think this would help -> [http://ubuntuforums.org/showpost.php?p=2979393&postcount=10](http://ubuntuforums.org/showpost.php?p=2979393&postcount=10) (but I guess this is just setting which network to connect to at startup)

Thanks a lot for your help btw!! :)

---

### Post by zuzuzzzip on 2007-08-07
right so this worked for me! (and normally all other RT2500 driver cards)
[http://ubuntuforums.org/showthread.php?t=420136#6](http://ubuntuforums.org/showthread.php?t=420136#6)

but no WPA yet though, but wicd was going to update this for rt2500 drivers.
seems like those drivers are a big nono huh? :P

---

### Post by imdano on 2007-08-07
I'm working on the rt2500 card in wicd.  The problem is the driver is really, really bad and doesn't report anything in iwpriv or iwlist to allow wicd to determine what kind of encryption an access point is using.  So the user would have to specify what it is somewhere.  I'm just trying to figure out the best way to integrate that right now.

What we have now does work for some ralink cards though.  People using the serialmonkey enhanced rt* drivers are fine, and maybe a few of the other rt cards (rt73 I think worked for some people).  Basically if your card gives an error if you run ```
iwpriv <wireless interface> get_site_survey
```you're out of luck right now.

---

### Post by zuzuzzzip on 2007-08-07
```
zuzuzzzip@ZuzuPC-ubuntu:~$ iwpriv ra0 get_site_survey
Invalid command : get_site_survey
```
darn.. oh well, should get myself a new 802.11n one once then :)

---

