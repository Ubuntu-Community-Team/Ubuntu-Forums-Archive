---
title: "Wireless Question - How do I know which radio I'm using? (A/G/N)"
date: 2012-03-25
forum: General Help
---

### Post by A4orce84 on 2012-03-25
Hey Guys,

I feel like my Windows 7 partition is a lot more "faster/responsive" when using my wireless. I have a wireless N router at home, and whenever I'm using Ubuntu things load up a lot less snappy.

Is there any command that will tell me which radio the computer is actually using when connected to my home wifi network?

Thanks.



--Asif

---

### Post by Paddy Landau on 2012-03-26
What exactly do you mean? Do you think you might have accidentally connected to a neighbour's wireless?

Click on your network applet (in your panel) and it will tell you to which wireless you have connected.

---

### Post by A4orce84 on 2012-03-27
No I know I am connected to my network. I am saying that I think in Windows 7 it is using the actual "N" radio because everything is a lot faster....and in Ubuntu it's using G most likely because it seems a bit sluggish.

---

### Post by wildmanne39 on 2012-03-28
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
 by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by A4orce84 on 2012-03-28
Here is the output:


cat /etc/lsb-release; uname -a
```

aahmad@aahmad-hdesktop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux aahmad-hdesktop 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:35:26 UTC 2012 i686 GNU/Linux
aahmad@aahmad-hdesktop:~$ 

```
lspci -nnk | grep -iA2 net
```

aahmad@aahmad-hdesktop:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:380c]
	Kernel driver in use: forcedeth
--
08:06.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
	Subsystem: Linksys Device [1737:0060]
	Kernel driver in use: wl
aahmad@aahmad-hdesktop:~$ 

```
lsusb
```

aahmad@aahmad-hdesktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 005: ID 03f0:1604 Hewlett-Packard DeskJet 940c
Bus 001 Device 004: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
aahmad@aahmad-hdesktop:~$ 

```
iwconfig
```

aahmad@aahmad-hdesktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:193  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

aahmad@aahmad-hdesktop:~$ 

```
rfkill list all
```

aahmad@aahmad-hdesktop:~$ rfkill list all
aahmad@aahmad-hdesktop:~$ 

```
lsmod
```

aahmad@aahmad-hdesktop:~$ lsmod
Module                  Size  Used by
michael_mic             1744  4 
arc4                    1165  2 
binfmt_misc             6599  1 
pci_stub                1146  1 
vboxpci                15338  0 
vboxnetadp              6968  0 
vboxnetflt             16556  0 
vboxdrv               250311  4 vboxpci,vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218460  1 
nvidia               9329739  42 
snd_hda_intel          22235  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
joydev                  8767  0 
usblp                  10651  0 
snd_usb_audio          86480  2 
snd_pcm                71475  5 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep               5040  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        17413  1 snd_usb_audio
snd_seq_midi            4588  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            17783  2 snd_usbmidi_lib,snd_seq_midi
uvcvideo               55943  0 
videodev               43194  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
snd_timer              19067  2 snd_pcm,snd_seq
lib80211_crypt_tkip     7736  0 
snd_seq_device          5744  3 snd_seq_midi,snd_seq,snd_rawmidi
wl                   1959533  0 
agpgart                32011  1 nvidia
snd                    49102  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
lib80211                5058  2 lib80211_crypt_tkip,wl
psmouse                59027  0 
serio_raw               4022  0 
soundcore                880  1 snd
shpchp                 29886  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_nforce2             5179  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
hid_logitech            8971  0 
ff_memless              4393  1 hid_logitech
firewire_ohci          21330  0 
usbhid                 36882  1 hid_logitech
hid                    67934  2 hid_logitech,usbhid
firewire_core          46675  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
forcedeth              49433  0 
sata_nv                19420  0 
pata_amd                8746  3 
aahmad@aahmad-hdesktop:~$ 

```

If you need any additional information, please let me know!  Thanks!


--Asif

---

### Post by dcstar on 2012-03-28
> **A4orce84 said:**
> 
.........
iwconfig
```

aahmad@aahmad-hdesktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  **Access Point: Not-Associated**   
          Link Quality:4  Signal level:193  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

aahmad@aahmad-hdesktop:~$ 

```


Tough to rate connectivity when there is no association to the WAP.

---

### Post by Mark Phelps on 2012-03-28
Basically, you're going to be using G or N -- which is determined by the slowest of the two: your PC and your Router.  If they both support N, then you'll be using N by default -- unless you configure your router to only use G.

---

### Post by garvinrick4 on 2012-03-28
Right click on Network icon in upper right select connection info. 54 MB/s is the fastest G will go. If higher
than that using N speeds. 
##As in previous post above me if you are getting G speeds change your router setup to N only in wireless
and will receive N speeds with an N card. You might have router at 2.4 ghz set to G, who knows.

---

### Post by A4orce84 on 2012-03-28
So I right clicked on my connection and it seems very low:


[IMG]http://img.photobucket.com/albums/v405/A4orce84/ConnectionInformation_001.jpg[/IMG]

Is there a way I can do this test in Win7 and see the results as well....to see which radio it is using (G or N) ?


Thanks.


--Asif

---

### Post by garvinrick4 on 2012-03-28
open command line in Windows:
```
netsh wlan show interfaces
```

---

### Post by wildmanne39 on 2012-03-28
Hi, try setting your settings like the screenshots.

Also your wireless is at 40 mb/s so unless you have a real fast connection it being higher is not going to make your speed much faster.

The speed will decrease the weaker your signal is.

The information you posted showed that you did not have a wireless connection at that time, so you must must have been connected with your wired connection.

With ubuntu 10.10 to use your wireless you have to be disconnected from your wired connection.
Thanks

---

