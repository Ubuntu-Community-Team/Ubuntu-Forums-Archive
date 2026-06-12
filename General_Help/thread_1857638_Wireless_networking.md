---
title: "Wireless networking"
date: 2011-10-10
forum: General Help
---

### Post by Maro848 on 2011-10-10
Hey guys I am a basic noob with linux in general with only a little experience in the past 6 months. I have several linux distros (linux mint, Ubuntu, Lubuntu, etc.) and would like to know where I can find an affordable usb wireless adapter that I can use on both my old laptop (since it doesn't have built in wireless) and my desktop. I don't really care to do much to configure just plug and play if possible. If not then I will need help in setting it up. I hope to get a reply soon as all I have for an adapter right now is a Cisco Valet connector AM10 and no one in the past couple years has successfully made it work that I have found. Thank you for any and all help in advance :)

---

### Post by ohmysql on 2011-10-12
> **Maro848 said:**
> Hey guys I am a basic noob with linux in general with only a little experience in the past 6 months. I have several linux distros (linux mint, Ubuntu, Lubuntu, etc.) and would like to know where I can find an affordable usb wireless adapter that I can use on both my old laptop (since it doesn't have built in wireless) and my desktop. I don't really care to do much to configure just plug and play if possible. If not then I will need help in setting it up. I hope to get a reply soon as all I have for an adapter right now is a Cisco Valet connector AM10 and no one in the past couple years has successfully made it work that I have found. Thank you for any and all help in advance :)

Ah si, I'm writing you on the AM10 as we speak! You can get it.

If you look at my threads about this issue, you can see it took me months, and the help of at least 6-7 real whizzes, but I got it.

I knew just about nothing about linux when I started. So believe me, if you follow the threads I've been starting (just google ohmysql cisco and you'll find them all. People break it down. But here's the short version:

1.) Get the latest version of usb_modeswitch (the guy built a new version just for my problem!). You'll need to compile and install. It's not hard, he breaks down (to me) exactly how to do it here: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4884#4884](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4884#4884)
2.) Download rt3572sta off the ralink website. That's the one you'll need. You'll need to make a few adjustments to the driver as outlined here: [http://ubuntuforums.org/showthread.php?t=1841123&highlight=cisco+valet+connector+AM10](http://ubuntuforums.org/showthread.php?t=1841123&highlight=cisco+valet+connector+AM10)     It won't be hard. You'll also have to compile and install the driver. Instructions should be in that thread.
3.) If network manager isn't working, try wicd. As outlined here: [http://ubuntuforums.org/showthread.php?p=11329031#post11329031](http://ubuntuforums.org/showthread.php?p=11329031#post11329031)

Good luck. Please report back if this works.

OMS writing from the AM10 (which just started working this morning - hopefully this continues).

---

### Post by Maro848 on 2011-10-12
only problem with doing that is that I have no internet useable to any machine other than windows. I'm not a complete noob but all attempts at using linux software downloaded from withing windows has failed miserably for me. And I have found a small usb wireless adapter that quite a few ppl claim to simply plug and play with Ubuntu, Fedora, and a few other distro's for about $10. For that price and that there are multiple people claiming it works I think I will just get it. However, that does not mean I will not try to overcome the Cisco once I have internet to my Linux Mint and Ubuntu machines. I do appreciate the links as I will most likely vistit them a few times

---

### Post by ohmysql on 2011-10-13
That's strange - it seems to me that if you download a .tar file within windows, put it on a USB key or just on the windows drive, you should be ok. Hmm, well, I know that usb_modeswitch and the rt3572sta driver are in .tar format in any case.

Anyway, you're welcome for the info. Have fun.

---

### Post by Maro848 on 2011-11-01
New update on this if anyone is interested is that the new Ubuntu release (11.10) comes with support for the cisco valet connector and I would suspect other devices that require mode switch as well. I have only once had the pc not recognize it and that was fixed by simply unplugging it and plugging it back in and it automatically connected to my home network! So if you put off upgrading to 11.10 because you put work into setting up the mode switch, I'm posting this from my pc which is using the cisco valet.

---

### Post by ohmysql on 2011-11-01
> **Maro848 said:**
> New update on this if anyone is interested is that the new Ubuntu release (11.10) comes with support for the cisco valet connector and I would suspect other devices that require mode switch as well. I have only once had the pc not recognize it and that was fixed by simply unplugging it and plugging it back in and it automatically connected to my home network! So if you put off upgrading to 11.10 because you put work into setting up the mode switch, I'm posting this from my pc which is using the cisco valet.

Whoa, awesome, but wait a minute - I'm on 11.10 and my Cisco Valet Connector (CVC) stopped working ! I had it working on 11.04 using rt3572sta (with several modifications), usb_modeswitch 1.1.9, and wicd.

A few questions for you:

1.) Would you be willing to post the output of these commands in terminal?

```
usb_modeswitch -e
lsmod | grep rt3
lsmod | grep rt2
lsmod | grep ndiswrapper
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
```2.) And then, do ```
modinfo X
``` for whatever you get out of the lsmod commands. For example, let's say when you do ```
lsmod | grep rt2
``` the system lists rt2870sta, please do:

```
modinfo rt2870sta
```3.) You didn't do ANY of the steps I listed above in the previous post did you? You didn't download, modify, or compile any drivers, you didn't update usb_modeswitch, right? Just trying to trace your steps. 
4.) Do you know if you're using network manager or wicd? You can figure this out by opening the Synaptic Package Manager. Search for "network manager" and then sort by what is installed (the green squares). If you tell me what programs have  green squares next to them, I'll know what you're using.

Thanks in advance for your help and thanks for the update. I'll be looking into this. I may just do a fresh install of 11.10. This is very exciting.

Like, ohhhh my SQL!!!

PS That would be pretty awesome if from now on the CVC was compatible out of box with Linux from now on. I had a ton of help - and also, it would be thanks in a big way to my persistence too. That's pretty cool.

---

### Post by Maro848 on 2011-11-01
to answer your questions about the code none of them changed anything as far as my connection and I only got output from two commands.

1. mode_switch version 1.1.9 was installed either from the .iso during installation or from the updates in update manager just after.

2. ndiswrapper is not installed. 

now about my actions after install:

I installed and rebooted as the system suggests and when the pc rebooted it gave me the message that wireless networks were available. I had completely forgotten that the CVC was connected during install. I did not have to make any changes to any packages.

I am using network-manager-gnome and it worked right out of the box with no need for drivers or code. Ubuntu did mount the drive inside yesterday automatically but today i had to do it in disk utility ( you do NOT have to mount for it to work) 

I used the CVC for all updates and installs since ubuntu itself was installed and have yet to need my other usb adapter for this machine. This is not isolated to my desktop as I just tried it on my HP G62 in Ubuntu 11.10 and it works.

Perhaps an install of network-manager-gnome and making sure that mode switch is also version 1.1.9 will get it working for you?

---

### Post by ohmysql on 2011-11-01
> **Maro848 said:**
> to answer your questions about the code none of them changed anything as far as my connection and I only got output from two commands.

1. mode_switch version 1.1.9 was installed either from the .iso during installation or from the updates in update manager just after.

2. ndiswrapper is not installed. 

now about my actions after install:

I installed and rebooted as the system suggests and when the pc rebooted it gave me the message that wireless networks were available. I had completely forgotten that the CVC was connected during install. I did not have to make any changes to any packages.

I am using network-manager-gnome and it worked right out of the box with no need for drivers or code. Ubuntu did mount the drive inside yesterday automatically but today i had to do it in disk utility ( you do NOT have to mount for it to work) 

I used the CVC for all updates and installs since ubuntu itself was installed and have yet to need my other usb adapter for this machine. This is not isolated to my desktop as I just tried it on my HP G62 in Ubuntu 11.10 and it works.

Perhaps an install of network-manager-gnome and making sure that mode switch is also version 1.1.9 will get it working for you?

I definitely have modeswitch 1.1.9 and the modeswitching is working great. I've been using network manager but it hasn't been working.

I think the main question is what driver you're using. Would you mind giving the output of:

```
lsmod
iwconfig
```

None of the "cat" commands gave any output? THAT's interesting!

You didn't upgrade to 11.10, right? You installed fresh? I have another box, I will try it on there. Very interesting - this update is much appreciated and I'm hoping we'll get to the bottom of this.

OMS

---

### Post by Maro848 on 2011-11-01
here is the information on the code (sorry I dont know how to use code boxes):

lsmod:~$ lsmod

Module                  Size  Used by
arc4                   12529  2 
rt2800usb              22684  0 
rt2800lib              54306  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20830  1 rt2800usb
rt2x00lib              50325  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              310872  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
lp                     17799  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
ppdev                  17113  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
joydev                 17693  0 
nouveau               728662  3 
edac_core              53746  0 
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
edac_mce_amd           23709  0 
drm                   236330  5 nouveau,ttm,drm_kms_helper
snd_seq_midi           13324  0 
k10temp                13166  0 
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
psmouse                73882  0 
parport_pc             36962  1 
parport                46562  3 lp,ppdev,parport_pc
snd_rawmidi            30547  1 snd_seq_midi
serio_raw              13166  0 
video                  19412  1 nouveau
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
i2c_nforce2            13058  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usb_storage            57901  0 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 
pata_amd               14121  0 
sata_nv                32305  1 

iwconfig:iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Overdrive-D22"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0B:6C:C6:2D:22   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:45  Invalid misc:95   Missed beacon:0

about the fresh install however the odd thing is that on my desktop I did a fresh install and on my laptop I upgraded from 11.04 to 11.10 and they both work flawlessly with my CVC.

---

### Post by Maro848 on 2011-11-01
another small piece of information you may want to see is that under network connection information the driver is rt2800usb

hope that helps

---

### Post by ohmysql on 2011-11-01
Yes, very helpful! Ok, I'm going to try some things. I'll get back to you later if I have further questions. (I probably will).

And I got your PM, thank you. I'll be in touch if I need more direct help.

OMS

---

### Post by Maro848 on 2011-11-01
no problem just let me know if there is anything I can do to help

---

### Post by ohmysql on 2011-11-01
> **Maro848 said:**
> no problem just let me know if there is anything I can do to help
 
Thanks so much. Would you show me the output of:
 
sudo iwlist scan
 
Thanks!
 
OMS

---

### Post by Maro848 on 2011-11-01
here you go:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:6C:C6:2D:22
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Overdrive-D22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002812234f37
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000D4F76657264726976652D443232
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C

---

### Post by ohmysql on 2011-11-01
> **Maro848 said:**
> here you go:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:6C:C6:2D:22
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Overdrive-D22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002812234f37
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000D4F76657264726976652D443232
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C

Aha, I think that's why we're having different experiences. It looks like you're not using WPA encryption (let me know if at any point you're not following). Let me know if I'm wrong.

And I'd be curious what happens if you try WPA encryption on your router. Do you have any clue how to give that a try?

And thanks again for the print-out.

OMS

---

### Post by Maro848 on 2011-11-01
unfortunately I use WEP at my house and use a mobile hot-spot as a router that cannot change to WPA I will try to get onto a WPA connection as soon as I can though when I can and update you when I find one.

---

### Post by Maro848 on 2011-11-01
ok I was wrong when I said I could not change from WEP to WPA on my router, there isn't a switch for that I had to remotely access it to change those settings but it made no difference in the way the CVC connects. Works automatically with both my installs.

---

### Post by ohmysql on 2011-11-02
I am now writing on the Cisco AM10 Valet Connector :)

That worked!

Good to know that the rt2800usb driver (that's the one that's working) works out of the box. That was very helpful to know. Thanks again. Let's hope this time of working sticks.

I am really excited that this is working and I don't have to be chained to my wall anymore!

Like, ohhhh myyyy SQL!!

---

### Post by Maro848 on 2011-11-03
I'm glad to hear that you were able to find the correct driver! As I mentioned in an earlier post if you have to reboot and the device doesn't activate don't panic as all I have had to do is remove the CVC from the usb port and plug it back in. Once that is done it'll automatically connect faster than I can sit back down in my chair.

---

### Post by Naa Laa on 2012-01-12
I can connect to the internet using Cisco valet AM10 on Ubuntu 11.04 but with slow speed. On the same machine with Win 7 I get close to 15mbps but on Ubuntu I get 0.5mbps speed. Can anyone help? 

Thanks!
[I]
Note: Its been only 2 days with Ubuntu/Linux - newbie here.[/I]

---

### Post by ohmysql on 2012-01-13
> **Naa Laa said:**
> I can connect to the internet using Cisco valet AM10 on Ubuntu 11.04 but with slow speed. On the same machine with Win 7 I get close to 15mbps but on Ubuntu I get 0.5mbps speed. Can anyone help? 

Thanks!
[I]
Note: Its been only 2 days with Ubuntu/Linux - newbie here.[/I]

How are you measuring the mbps on Linux? What command do you use? I have no idea how to do that either on Linux or on Windows.

Best,
OMS

---

### Post by Naa Laa on 2012-01-13
> **ohmysql said:**
> How are you measuring the mbps on Linux? What command do you use? I have no idea how to do that either on Linux or on Windows.

Best,
OMS

[http://speedtest.net/](http://speedtest.net/)

---

### Post by ohmysql on 2012-01-13
> **Naa Laa said:**
> [http://speedtest.net/](http://speedtest.net/)

Oh, I'm definitely getting about 6mbps. Ah well, no clue. I'm also using 11.10

---

