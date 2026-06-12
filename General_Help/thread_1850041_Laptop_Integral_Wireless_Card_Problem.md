---
title: "Laptop Integral Wireless Card Problem"
date: 2011-09-25
forum: General Help
---

### Post by everenlightened on 2011-09-25
I installed Ubuntu 11.04 Today, 

My hp pavilion dv8000 hard drive crapped out, so I put in an old harddrive from an IBM laptop from the stone age. I booted from the LiveCD installed Ubuntu on a partition, and rebooted, did all the updates, booted again. Everything seems to work great.

 Only problem is that I can only use the internet when the ethernet cord is directly plugged into my router. I have wireless in the house and an 802.11b card that was operating fine before the HD crashed. I assume it is hopefully just a driver issue. 

I know it is a realtek 8139 card from following some help forums but could not figure out how to proceed from there. Also when using it with the original hard drive there is a dedicated on/off button for the wireless, maybe its something as simple as getting the card to turn on but the button does nothing now.

Anyone know how to get my wireless working? I would love to save the portability of the laptop. 

(PS I'm totally new to Ubuntu, but not totally hopeless when it comes to computers, so bear with me and I'll try not to be too much of a noob)

---

### Post by grahammechanical on 2011-09-25
Hi and welcome to the forums. Some questions.

Is this a dual boot? That dedicated on/off button most probably still does something. Can you check in the BIOS that the wireless adapter is still enabled? With some laptops if you turn off wireless in the Windows OS it becomes very difficult to turn it on in Ubuntu. This is why I ask if you are dual booting. If you are, then do not turn the wireless off in the other OS.

Do you see the network manager icon (top left - two arrows going in opposite directions)? When you right click it do you see

a) a tick mark against Enable Networking and Enable wireless? If not then click those lines to put the tick mark on both of them. This action works like an on/off switch.

b) do you see any wireless networks listed? With the two tick marks in place you should see some wireless networks. You might need to reboot.

What error messages does Ubuntu give you just after the desktop loads?

Can you confirm that you have activated any necessary drivers through the Additional Drivers utility? With a new installation it will put an icon of an expansion card in the top panel or you can load it from System Settings or search for it in the Dash - just type the name in the search panel.

Regards.

---

### Post by tech7 on 2011-09-25
System>Administration>Additional Drivers

For that particular model (hp dv8000 series) there will probably be drivers available for both your wlan card and your nvidia card.

---

### Post by everenlightened on 2011-09-26
I maintained the harddrive partition from windows, but the harddrive was froma different computer. So I have not used the dual boot. I just maintained it to salvage some old files. 

The wireless was turned off when the original harddrive crapped out, so I will check in bios. 

The network manager, is this while in bios or on the ubuntu desktop? I can look for this too. 

I'm not with the computer now (gotta pay the bills) but will check these out and respond later.
If I need more help getting the drivers installed if I can get the card on I will ask for more help then.

Thanks!

---

### Post by everenlightened on 2011-09-26
Ok 

Wireless LAN is enabled in BIOS, was all along.

I went to additional drivers and was able to automatically download one for "software modem" not sure if this was related to original issue or not but did not fix. 

I atttempted to find "network manager" unsuccesfully. I see no tabs like the one described. I did find "Network" and a tab for wireless under it, but no indication that my wireless card was operating, and no wireless networks detected. My wireless network is up and running. 

Any thoughts? Do I have to add all the info for my network? seems like it should detect all but the encryption key automatically. 

Thanks for the help!

---

### Post by wildmanne39 on 2011-09-26
Hi, please open a terminal by hitting ctrl+alt+t and paste these commands into it then paste the results here.
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
 by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by everenlightened on 2011-09-27
here we go 

everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ lspci -nnk | grep -iA2 net
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
    Kernel driver in use: b43-pci-bridge
--
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:309b]
    Kernel driver in use: 8139too

everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
joydev                 17322  0 
arc4                   12473  2 
snd_via82xx_modem      18305  0 
radeon                900494  3 
snd_atiixp_modem       18624  5 
snd_atiixp             19400  2 
b43                   296610  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_intel8x0m          18493  0 
mac80211              257001  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
snd_ac97_codec        105614  4 snd_via82xx_modem,snd_atiixp_modem,snd_atiixp,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  7 snd_via82xx_modem,snd_atiixp_modem,snd_atiixp,snd_intel8x0m,snd_ac97_codec
pcmcia                 39671  0 
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_seq,snd_pcm
hp_wmi                 13418  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  5 radeon,ttm,drm_kms_helper
cfg80211              156212  2 b43,mac80211
tifm_7xx1              12898  0 
sparse_keymap          13666  1 hp_wmi
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
snd                    55295  22 snd_via82xx_modem,snd_atiixp_modem,snd_atiixp,snd_rawmidi,snd_intel8x0m,snd_ac97_codec,snd_seq,snd_pcm,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12872  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
video                  18951  0 
soundcore              12600  1 snd
shpchp                 32345  0 
ati_agp                13202  0 
snd_page_alloc         14073  5 snd_via82xx_modem,snd_atiixp_modem,snd_atiixp,snd_intel8x0m,snd_pcm
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
8139too                23208  0 
sdhci_pci              13623  0 
ssb                    45942  1 b43
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core
pata_atiixp            12968  2 

I'm sure I pasted too much but I wasn't sure what was needed.

Thanks again!

---

### Post by everenlightened on 2011-09-27
```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ lspci -nnk | grep -iA2 net
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
    Kernel driver in use: b43-pci-bridge
--
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:309b]
    Kernel driver in use: 8139too
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
joydev                 17322  0 
arc4                   12473  2 
snd_via82xx_modem      18305  0 
radeon                900494  3 
snd_atiixp_modem       18624  5 
snd_atiixp             19400  2 
b43                   296610  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_intel8x0m          18493  0 
mac80211              257001  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
snd_ac97_codec        105614  4 snd_via82xx_modem,snd_atiixp_modem,snd_atiixp,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  7 snd_via82xx_modem,snd_atiixp_modem,snd_atiixp,snd_intel8x0m,snd_ac97_codec
pcmcia                 39671  0 
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_seq,snd_pcm
hp_wmi                 13418  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  5 radeon,ttm,drm_kms_helper
cfg80211              156212  2 b43,mac80211
tifm_7xx1              12898  0 
sparse_keymap          13666  1 hp_wmi
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
snd                    55295  22 snd_via82xx_modem,snd_atiixp_modem,snd_atiixp,snd_rawmidi,snd_intel8x0m,snd_ac97_codec,snd_seq,snd_pcm,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12872  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
video                  18951  0 
soundcore              12600  1 snd
shpchp                 32345  0 
ati_agp                13202  0 
snd_page_alloc         14073  5 snd_via82xx_modem,snd_atiixp_modem,snd_atiixp,snd_intel8x0m,snd_pcm
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
8139too                23208  0 
sdhci_pci              13623  0 
ssb                    45942  1 b43
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core
pata_atiixp            12968  2 
```Sorry hope this is easier to read

---

### Post by wildmanne39 on 2011-09-27
Hi, you did right when we ask for information we like to see all of it.

Please post the results of these commands:
```
lsmod | grep b43
```
```
dmesg | egrep 'b43|firm|wlan0'
```
Thank you

---

### Post by everenlightened on 2011-09-27
```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ dmesg | egrep 'b43|firm|wlan0'
[    1.337967] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   31.168874] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   31.321601] Registered led device: b43-phy0::radio
[   31.588121] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   31.588127] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   31.588131] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$
```sorry this info is coming in spurts, thanks for the help

---

### Post by everenlightened on 2011-09-27
I looked at the error code posted above and found the install instructions for b43 drivers here

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

I followed those, but under additional drivers all i have is a "software modem" that is activated that doesn't seem to be related, not sure where to find a list of activated drivers in ubuntu. 

"I want my device manager from windows!" haha but I think my drivers are up to date, now I just have to make sure they're working. Gonna restart and if that doesn't work head to bed. I'll post if its resolved, otherwise we'll try again tomorrow! 

Thanks again!

---

### Post by wildmanne39 on 2011-09-27
Hi, the driver you need was the one that was installed, it just did install the firmware correctly.

Do this please:
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
run one command at a time.

Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, then disconnect your wired connection. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Run these one code at a time.
Now it should be working.
Thank you

---

### Post by everenlightened on 2011-09-28
card seems to be on! Awesome. Gotta reboot and search for my network, but running late for work. Thanks so much! I'll repost tonight to say its totally resolved! Thanks!

---

### Post by wildmanne39 on 2011-09-28
Hi, great I will be watching this thread.
Thank you

---

### Post by everenlightened on 2011-09-28
hmmm, card seems to be on by the LED that lit up when it was on using windows. Still do not detect any wireless network. 

The windows desktop and IPhone are on the wireless so its up and running, but don't see any way to "check" for available networks. any thoughts?

---

### Post by wildmanne39 on 2011-09-28
Hi, please post the results of these commands:
```
nm-tool
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
dmesg | egrep 'b43|firm|wlan0'
```
```
lsmod | grep b43
```
Thank you

---

### Post by everenlightened on 2011-09-29
here we go! and I should have a couple hours where i'll be able to check and get back to you before 12hrs later.

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:16:D4:02:C6:33

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:14:A5:A8:E3:6F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE443:        Infra, B0:E7:54:CB:1C:91, Freq 2452 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    beachbound-guest:Infra, 68:7F:74:38:C4:5B, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    RichEagle-guest: Infra, 68:7F:74:BD:83:3B, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    MOTOROLA-6AB6A:  Infra, AC:81:12:2A:71:1F, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA2
    RichEagle:       Infra, 68:7F:74:BD:83:39, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    beachbound:      Infra, 68:7F:74:38:C4:5A, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    whaleynetwork:   Infra, 00:1E:58:EF:A4:29, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    NetworkHughes:   Infra, 00:1C:10:86:9A:31, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    DUDE:            Infra, E0:91:F5:D8:FC:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 91 WPA2


``````
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ sudo iwlist scan
[sudo] password for everenlightened: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: E0:91:F5:D8:FC:90
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"DUDE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000029e737c619b
                    Extra: Last beacon: 992ms ago
                    IE: Unknown: 000444554445
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B0001031047001054CD33343579FF542A3181D3786D837F1021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1C:10:86:9A:31
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NetworkHughes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bc0ca1963
                    Extra: Last beacon: 852ms ago
                    IE: Unknown: 000D4E6574776F726B487567686573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 68:7F:74:38:C4:5A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"beachbound"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000029e74ffe199
                    Extra: Last beacon: 376ms ago
                    IE: Unknown: 000A6265616368626F756E64
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD670050F204104A00011010440001021041000100103B0001031047001020EF2F9CA0E86F5E8E80ABE3438CE0EF102100074C696E6B737973102300034D3130102400063132333435361042000234321054000800060050F2040001101100034D3130100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
          Cell 04 - Address: 68:7F:74:38:C4:5B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"beachbound-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000029e74fe00a6
                    Extra: Last beacon: 500ms ago
                    IE: Unknown: 00106265616368626F756E642D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
          Cell 05 - Address: 00:1E:58:EF:A4:29
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"whaleynetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000029e75eef180
                    Extra: Last beacon: 696ms ago
                    IE: Unknown: 000D7768616C65796E6574776F726B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340600050000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160600010000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: 68:7F:74:BD:83:39
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"RichEagle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002754103d6f0
                    Extra: Last beacon: 1120ms ago
                    IE: Unknown: 0009526963684561676C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B00010310470010F18AA0CADB9E8BB6835E3C2108E9BDE710210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 07 - Address: 68:7F:74:BD:83:3B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"RichEagle-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000275410403fa
                    Extra: Last beacon: 1112ms ago
                    IE: Unknown: 000F526963684561676C652D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 08 - Address: AC:81:12:2A:71:1F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"MOTOROLA-6AB6A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000671b596189
                    Extra: Last beacon: 1224ms ago
                    IE: Unknown: 000E4D4F544F524F4C412D3641423641
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 09 - Address: 00:23:69:35:52:BB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"0684"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s


``````
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

``````
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ dmesg | egrep 'b43|firm|wlan0'
[    1.346412] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   31.581161] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   31.712303] Registered led device: b43-phy0::radio
[   32.544067] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   32.610566] ADDRCONF(NETDEV_UP): wlan0: link is not ready
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43

```I saw somewhere in there that it listed DUDE. Thats my wireless network name.
I'll go ahead and post this and then read back through the code.
Seems like we're getting ever so close.

---

### Post by bkratz on 2011-09-29
Also noticed that there are 3 other networks on the same channel as yours. They are weaker, but you still may want to consider changing your channel.

---

### Post by wildmanne39 on 2011-09-29
Hi, the channel is one thing that I see, I believe you should change it to 14 in your router and see if that helps, also please post the results of this command:
```
sudo cat /var/log/syslog | grep etwork | tail -n25
```
Thank you

---

### Post by everenlightened on 2011-09-29
trying to remember the admin username and password for the router, damn CRS. 

here is requested info

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ sudo cat /var/log/syslog | grep etwork | tail -n25
[sudo] password for everenlightened: 
Sep 29 20:54:04 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[489]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Sep 29 20:54:07 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[489]: <info> (eth0): carrier now ON (device state 8)

```

Working on getting channel changed

---

### Post by everenlightened on 2011-09-29
wife is getting pissy, gonna have to figure out how to reset the router later. The factory reset doesn't seem to be working and can't find the old login. 

seems like changing channels on router won't affect the wireless issue i'm having though. I'll try it to be sure but shouldn't my card be recognizing the network? It obviously does using the terminal commands I posted, why won't it allow me to connect to it?
grrr...

thanks for the help!

---

### Post by wildmanne39 on 2011-09-29
Hi, is that all of the information? it should have had 25 lines.
Thank you

---

### Post by wildmanne39 on 2011-09-29
Hi, well that is what we are trying to figure out.

The channel can make a difference sometimes in this last week, I have helped 2 people that could not connect using channel 1 and when they changed it they connected, but that may not be your problem.
Thank you

---

### Post by everenlightened on 2011-09-30
sorry i was getting frustrated last night. 

here is the code again, looks right this time.

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ sudo cat /var/log/syslog | grep etwork | tail -n25
[sudo] password for everenlightened: 
Sep 30 06:18:54 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 30 06:18:54 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA kernel: [   38.260630] type=1400 audit(1317377935.040:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=643 comm="apparmor_parser"
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> Activation (eth0) successful, device activated.
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:06.0/net/eth0, iface: eth0)
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:06.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 30 06:18:55 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/hp-wmi/rfkill/rfkill0) (driver hp-wmi)
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/ieee80211/phy0/rfkill1) (driver <unknown>)
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): now managed
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): bringing up device.
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): preparing device.
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): deactivating device (reason: 2).
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/net/wlan0, iface: wlan0)
Sep 30 06:18:56 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Sep 30 06:18:57 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): supplicant interface state:  starting -> ready
Sep 30 06:18:57 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[480]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
```

I should be able to get the router channel changed this evening, channel 14 was the suggestion?

thanks again!

---

### Post by everenlightened on 2011-09-30
Hello again. Reset Router, and finally was able to login. Channel 14 is not an option with my N600 Netgear apparently. Channels 1-11 are the only options. I saw that no other networks seemed to be on channel 9 so I set the router to that and according to iwlist scan I'm now broadcasting on channel 9.

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ sudo iwlist scan
[sudo] password for everenlightened: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 68:7F:74:38:C4:5A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"beachbound"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b192f1eb31
                    Extra: Last beacon: 484ms ago
                    IE: Unknown: 000A6265616368626F756E64
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD670050F204104A00011010440001021041000100103B0001031047001020EF2F9CA0E86F5E8E80ABE3438CE0EF102100074C696E6B737973102300034D3130102400063132333435361042000234321054000800060050F2040001101100034D3130100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
          Cell 02 - Address: 68:7F:74:38:C4:5B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"beachbound-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b192f1f487
                    Extra: Last beacon: 484ms ago
                    IE: Unknown: 00106265616368626F756E642D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
          Cell 03 - Address: 00:1C:10:86:9A:31
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"NetworkHughes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004edec21c46
                    Extra: Last beacon: 848ms ago
                    IE: Unknown: 000D4E6574776F726B487567686573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: E0:91:F5:D8:FC:90
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"DUDE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000bc9bd62
                    Extra: Last beacon: 492ms ago
                    IE: Unknown: 000444554445
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B0001031047001054CD33343579FF542A3181D3786D837F1021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

Sadly still cannot detect in "Network Connections"

---

### Post by wildmanne39 on 2011-09-30
Hi, we are close. I need you to unplug your wired connection then run these commands, the last log command showed mostly your wired connection.
```
sudo cat /var/log/syslog | grep etwork | tail -n50
``` 
```
rfkill list All
```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
cat /etc/network/interfaces
```
Thank you

---

### Post by everenlightened on 2011-10-01
here we go

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ sudo cat /var/log/syslog | grep etwork | tail -n50
[sudo] password for everenlightened: 
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> dhclient started with pid 539
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA kernel: [   30.784120] type=1400 audit(1317485929.522:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=594 comm="apparmor_parser"
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): DHCPv4 state changed preinit -> bound
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info>   address 192.168.1.3
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info>   prefix 24 (255.255.255.0)
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info>   gateway 192.168.1.1
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info>   nameserver '192.168.1.1'
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Scheduling stage 5
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Done scheduling stage 5
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Oct  1 12:18:49 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Oct  1 12:18:50 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) successful, device activated.
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/net/wlan0, iface: wlan0)
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/hp-wmi/rfkill/rfkill0) (driver hp-wmi)
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/ieee80211/phy0/rfkill1) (driver <unknown>)
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): now managed
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): bringing up device.
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): preparing device.
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): deactivating device (reason: 2).
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): supplicant interface state:  starting -> ready
Oct  1 12:18:51 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Oct  1 12:22:06 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Oct  1 12:22:11 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): device state change: 8 -> 2 (reason 40)
Oct  1 12:22:11 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): deactivating device (reason: 40).
Oct  1 12:22:11 everenlightened-Pavilion-dv8000-EZ581UA-ABA NetworkManager[456]: <info> (eth0): canceled DHCP transaction, DHCP client pid 539

```

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by wildmanne39 on 2011-10-01
Hi, it looks like an issue with network manager, I would open synaptic and type wicd into the search box then install it, and after you install it remove network manager but only after you install wicd, and see if you can connect with wicd, it is another network manager.
Thank you

---

### Post by everenlightened on 2011-10-01
Installed wicd and removed network manager. The eth0 is still working but when I removed network manager the light indicating wireless card is on turned off. And in wicd i still see no wireless networks.

Will check again after reboot but heading to dinner now.

Thanks!

---

### Post by everenlightened on 2011-10-02
yup, rebooted and still nothing. thoughts? is my card just not going to work with ubuntu?

---

### Post by wildmanne39 on 2011-10-02
Hi, post the results of these commands now that wicd is insalled.
```
rfkill list all
```
```
lsmod
```
Thank you

---

### Post by everenlightened on 2011-10-03
```
verenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ rfkill lis all
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

```

```
everenlightened@everenlightened-Pavilion-dv8000-EZ581UA-ABA:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
arc4                   12473  2 
radeon                900494  3 
snd_atiixp             19400  2 
b43                   296610  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 b43
snd_atiixp_modem       18624  5 
snd_via82xx_modem      18305  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_intel8x0m          18493  0 
ttm                    65184  1 radeon
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_ac97_codec        105614  4 snd_atiixp,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  7 snd_atiixp,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec
pcmcia                 39671  0 
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  5 radeon,ttm,drm_kms_helper
hp_wmi                 13418  0 
cfg80211              156212  2 b43,mac80211
sparse_keymap          13666  1 hp_wmi
yenta_socket           27230  0 
tifm_7xx1              12898  0 
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
snd                    55295  22 snd_atiixp,snd_rawmidi,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 radeon
psmouse                73312  0 
k8temp                 12872  0 
video                  18951  0 
soundcore              12600  1 snd
serio_raw              12990  0 
shpchp                 32345  0 
i2c_piix4              13095  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14073  5 snd_atiixp,snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
ati_agp                13202  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
ssb                    45942  1 b43
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
pata_atiixp            12968  2 

```

---

### Post by everenlightened on 2011-10-03
thought that looked wrong

```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by wildmanne39 on 2011-10-03
Hi, please run this command again, just copy and paste.
```
rfkill list All
```
Thank you

---

### Post by wildmanne39 on 2011-10-03
Hi, that is what I needed, thank you.
It says your wireless is hard blocked.

Find the button or the fn f5 key or some other key that turns it on.
Thank you

---

### Post by everenlightened on 2011-10-04
I tried the dedicated wireless on/off button this morning with no luck. I'll see if there's a function key as well. Should I go back in bios and check also? I'm afraid something is turning it off so I'm not sure bios would be a permanent fix.

---

### Post by rock100 on 2011-10-04
Only difficulty is that I can only use the cyberspace when the ethernet fabric is direct obstructed into my router. I hold wireless in the sanctuary and an 802.11b card that was operating pulverized before the HD crashed. I arrogate it is hopefully conscionable a driver issuing.







      [barstool](http://www.barstool-shop.com.au/)       [bars   stools](http://www.barstool-shop.com.au/)

---

### Post by wildmanne39 on 2011-10-04
Hi, yes you can look in the bios sometimes it is off in there.

The keys that turn wireless on and off on some HP laptops, may not be the expected key. A recent case was not Fn+f12; it was Alt+F12 that activated the wireless. You should experiment and run ```
rfkill list all
``` to confirm.
Thank you

---

