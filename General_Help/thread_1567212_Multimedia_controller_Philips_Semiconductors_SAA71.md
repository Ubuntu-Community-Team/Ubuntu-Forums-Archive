---
title: "Multimedia controller: Philips Semiconductors SAA7130 driver ?"
date: 2010-09-03
forum: General Help
---

### Post by alaukikyo on 2010-09-03
I just was able to install mythtv  but it didn't recognize my tv tuner 

my tvtuner information is

04:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
    Subsystem: Philips Semiconductors Device 0000
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (3750ns min, 9500ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d0100000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134


PLease help it is urgent 
[-o<

---

### Post by sikander3786 on 2010-09-03
I have the same card and I got it working by using the following commands under Ubuntu but it doesn't work with mythtv, instead I use TVTime to view channels. Try it, check it in TVTime if it is working and then go for mythtv I suggest.

```

sudo modprobe -vr saa7134_dvb

sudo modprobe -vr saa7134_alsa

sudo modprobe -vr saa7134

sudo modprobe -v saa7134 card=21

```

---

### Post by sikander3786 on 2010-09-03
Here is a list of all tuners for Linux. If the above commands don't work, change the card = 21 to whatever number corresponds your card.

```

0 -> UNKNOWN/GENERIC
1 -> Proteus Pro [philips reference design] [1131:2001,1131:2001]
2 -> LifeView FlyVIDEO3000 [5168:0138,4e42:0138]
3 -> LifeView/Typhoon FlyVIDEO2000 [5168:0138,4e42:0138]
4 -> EMPRESS [1131:6752]
5 -> SKNet Monster TV [1131:4e85]
6 -> Tevion MD 9717
7 -> KNC One TV-Station RDS / Typhoon TV Tuner RDS [1131:fe01,1894:fe01]
8 -> Terratec Cinergy 400 TV [153b:1142]
9 -> Medion 5044
10 -> Kworld/KuroutoShikou SAA7130-TVPCI
11 -> Terratec Cinergy 600 TV [153b:1143]
12 -> Medion 7134 [16be:0003]
13 -> Typhoon TV+Radio 90031
14 -> ELSA EX-VISION 300TV [1048:226b]
15 -> ELSA EX-VISION 500TV [1048:226a]
16 -> ASUS TV-FM 7134 [1043:4842,1043:4830,1043:4840]
17 -> AOPEN VA1000 POWER [1131:7133]
18 -> BMK MPEX No Tuner
19 -> Compro VideoMate TV [185b:c100]
20 -> Matrox CronosPlus [102B:48d0]
21 -> 10MOONS PCI TV CAPTURE CARD [1131:2001]
22 -> AverMedia M156 / Medion 2819 [1461:a70b]
23 -> BMK MPEX Tuner
24 -> KNC One TV-Station DVR [1894:a006]
25 -> ASUS TV-FM 7133 [1043:4843]
26 -> Pinnacle PCTV Stereo (saa7134) [11bd:002b]
27 -> Manli MuchTV M-TV002
28 -> Manli MuchTV M-TV001
29 -> Nagase Sangyo TransGear 3000TV [1461:050c]
30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card(PAL-BG,FM) [1019:4cb4]
31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card (NTSC,FM) [1019:4cb5]
32 -> AVACS SmartTV
33 -> AVerMedia DVD EZMaker [1461:10ff]
34 -> Noval Prime TV 7133
35 -> AverMedia AverTV Studio 305 [1461:2115]
36 -> UPMOST PURPLE TV [12ab:0800]
37 -> Items MuchTV Plus / IT-005
38 -> Terratec Cinergy 200 TV [153b:1152]
39 -> LifeView FlyTV Platinum Mini [5168:0212,4e42:0212]
40 -> Compro VideoMate TV PVR/FM [185b:c100]
41 -> Compro VideoMate TV Gold+ [185b:c100]
42 -> Sabrent SBT-TVFM (saa7130)
43 -> :Zolid Xpert TV7134
44 -> Empire PCI TV-Radio LE
45 -> Avermedia AVerTV Studio 307 [1461:9715]
46 -> AVerMedia Cardbus TV/Radio (E500) [1461:d6ee]
47 -> Terratec Cinergy 400 mobile [153b:1162]
48 -> Terratec Cinergy 600 TV MK3 [153b:1158]
49 -> Compro VideoMate Gold+ Pal [185b:c200]
50 -> Pinnacle PCTV 300i DVB-T + PAL [11bd:002d]
51 -> ProVideo PV952 [1540:9524]
52 -> AverMedia AverTV/305 [1461:2108]
53 -> ASUS TV-FM 7135 [1043:4845]
54 -> LifeView FlyTV Platinum FM / Gold [5168:0214,5168:5214,1489:0214,5168:0304]
55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere Duo [5168:0306,4E42:0306]
56 -> Avermedia AVerTV 307 [1461:a70a]
57 -> Avermedia AVerTV GO 007 FM [1461:f31f]
58 -> ADS Tech Instant TV (saa7135) [1421:0350,1421:0351,1421:0370,1421:1370]
59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Cardbus [5168:0502,4e42:0502,1489:0502]
61 -> Philips TOUGH DVB-T reference design [1131:2004]
62 -> Compro VideoMate TV Gold+II
63 -> Kworld Xpert TV PVR7134
64 -> FlyTV mini Asus Digimatrix [1043:0210]
65 -> V-Stream Studio TV Terminator
66 -> Yuan TUN-900 (saa7135)
67 -> Beholder BeholdTV 409 FM [0000:4091]
68 -> GoTView 7135 PCI [5456:7135]
69 -> Philips EUROPA V3 reference design [1131:2004]
70 -> Compro Videomate DVB-T300 [185b:c900]
71 -> Compro Videomate DVB-T200 [185b:c901]
72 -> RTD Embedded Technologies VFG7350 [1435:7350]
73 -> RTD Embedded Technologies VFG7330 [1435:7330]
74 -> LifeView FlyTV Platinum Mini2 [14c0:1212]
75 -> AVerMedia AVerTVHD MCE A180 [1461:1044]
76 -> SKNet MonsterTV Mobile [1131:4ee9]
77 -> Pinnacle PCTV 40i/50i/110i (saa7133) [11bd:002e]
78 -> ASUSTeK P7131 Dual [1043:4862,1043:4857]
79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO25 Rev:2B)
80 -> ASUS Digimatrix TV [1043:0210]
81 -> Philips Tiger reference design [1131:2018]
82 -> MSI TV@Anywhere plus [1462:6231,1462:8624]
83 -> Terratec Cinergy 250 PCI TV [153b:1160]
84 -> LifeView FlyDVB Trio [5168:0319]
85 -> AverTV DVB-T 777 [1461:2c05,1461:2c05]
86 -> LifeView FlyDVB-T / Genius VideoWonder DVB-T [5168:0301,1489:0301]
87 -> ADS Instant TV Duo Cardbus PTV331 [0331:1421]
88 -> Tevion/KWorld DVB-T 220RF [17de:7201]
89 -> ELSA EX-VISION 700TV [1048:226c]
90 -> Kworld ATSC110/115 [17de:7350,17de:7352]
91 -> AVerMedia A169 B [1461:7360]
92 -> AVerMedia A169 B1 [1461:6360]
93 -> Medion 7134 Bridge #2 [16be:0005]
94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV @nywhere A/D NB [5168:3306,5168:3502,5168:3307,4e42:3502]
95 -> LifeView FlyVIDEO3000 (NTSC) [5169:0138]
96 -> Medion Md8800 Quadro [16be:0007,16be:0008,16be:000d]
97 -> LifeView FlyDVB-S /Acorp TV134DS [5168:0300,4e42:0300]
98 -> Proteus Pro 2309 [0919:2003]
99 -> AVerMedia TV Hybrid A16AR [1461:2c00]
100 -> Asus Europa2 OEM [1043:4860]
101 -> Pinnacle PCTV 310i [11bd:002f]
102 -> Avermedia AVerTV Studio 507 [1461:9715]
103 -> Compro Videomate DVB-T200A
104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid [0070:6700,0070:6701,0070:6702,0070:6703,0070:6704,0070:6705]
105 -> Terratec Cinergy HT PCMCIA [153b:1172]
106 -> Encore ENLTV [1131:2342,1131:2341,3016:2344]
107 -> Encore ENLTV-FM [1131:230f]
108 -> Terratec Cinergy HT PCI [153b:1175]
109 -> Philips Tiger - S Reference design
110 -> Avermedia M102 [1461:f31e]
111 -> ASUS P7131 4871 [1043:4871]
112 -> ASUSTeK P7131 Hybrid [1043:4876]
113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card (PAL,FM) [1019:4cb6]
114 -> KWorld DVB-T 210 [17de:7250]
115 -> Sabrent PCMCIA TV-PCB05 [0919:2003]
116 -> 10MOONS TM300 TV Card [1131:2304]
117 -> Avermedia Super 007 [1461:f01d]
118 -> Beholder BeholdTV 401 [0000:4016]
119 -> Beholder BeholdTV 403 [0000:4036]
120 -> Beholder BeholdTV 403 FM [0000:4037]
121 -> Beholder BeholdTV 405 [0000:4050]
122 -> Beholder BeholdTV 405 FM [0000:4051]
123 -> Beholder BeholdTV 407 [0000:4070]
124 -> Beholder BeholdTV 407 FM [0000:4071]
125 -> Beholder BeholdTV 409 [0000:4090]
126 -> Beholder BeholdTV 505 FM/RDS [0000:5051,0000:505B,5ace:5050]
127 -> Beholder BeholdTV 507 FM/RDS / BeholdTV 509 FM [0000:5071,0000:507B,5ace:5070,5ace:5090]
128 -> Beholder BeholdTV Columbus TVFM [0000:5201]
129 -> Beholder BeholdTV 607 / BeholdTV 609 [5ace:6070,5ace:6071,5ace:6072,5ace:6073,5ace:6090,5ace:6091,5ace:6092,5ace:6093
]
130 -> Beholder BeholdTV M6 / BeholdTV M6 Extra [5ace:6190,5ace:6193,5ace:6191]
131 -> Twinhan Hybrid DTV-DVB 3056 PCI [1822:0022]
132 -> Genius TVGO AM11MCE
133 -> NXP Snake DVB-S reference design
134 -> Medion/Creatix CTX953 Hybrid [16be:0010]
135 -> MSI TV@nywhere A/D v1.1 [1462:8625]
136 -> AVerMedia Cardbus TV/Radio (E506R) [1461:f436]
137 -> AVerMedia Hybrid TV/Radio (A16D) [1461:f936]
138 -> Avermedia M115 [1461:a836]
139 -> Compro VideoMate T750 [185b:c900]
140 -> Avermedia DVB-S Pro A700 [1461:a7a1]
141 -> Avermedia DVB-S Hybrid+FM A700 [1461:a7a2]
142 -> Beholder BeholdTV H6 [5ace:6290]

```

---

### Post by alaukikyo on 2010-09-04
21 gives this error 
> 
install /sbin/modprobe --ignore-install saa7134 card=21 && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
insmod /lib/modules/2.6.32-24-generic/kernel/drivers/media/video/saa7134/saa7134.ko card=21
FATAL: Error inserting saa7134 (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134

while 0 gives this error 

> 
install /sbin/modprobe --ignore-install saa7134 card=0 && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
insmod /lib/modules/2.6.32-24-generic/kernel/drivers/media/video/saa7134/saa7134.ko card=0
FATAL: Error inserting saa7134 (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134


---

### Post by sikander3786 on 2010-09-04
My card is named something but not surely 10moons as it appears on the list. I tried repeating the commands posted in my first post, starter from 1 and at 21, I got the result in TVTime. I was not sure which one was my card on the list and not even sure which one you are using. So start from 1 and keep going until your card is detected (if no one else gives a better solution). No better solution in my mind.

---

### Post by alaukikyo on 2010-09-05
Tried but couldn't get it to work.
It is an zebronic pci tv tuner card.
i have also compiled and install the v4l linux drivers for philips saaa173x series drivers from here
can somone please help it is urgent i need to get it working in 2-3 days or i have to install windows:(
 and mess up my system :facepalm

---

### Post by coffeecat on 2010-09-05
Try installing the package linux-firmware-nonfree. Iirc the Phillips chipset DV cards need the nonfree firmware. Only the linux-firmware-free package is installed in a default installation.

Do a cold boot once you have installed the firmware. Sometimes the firmware doesn't load into the device if you do a simple reboot.

---

### Post by alaukikyo on 2010-09-05
> **coffeecat said:**
> Try installing the package linux-firmware-nonfree. Iirc the Phillips chipset DV cards need the nonfree firmware. Only the linux-firmware-free package is installed in a default installation.

Do a cold boot once you have installed the firmware. Sometimes the firmware doesn't load into the device if you do a simple reboot.

Cheers
Will try that out:D

---

### Post by alaukikyo on 2010-09-06
Didn't Work :(

---

### Post by alaukikyo on 2010-09-07
bump!

---

### Post by alaukikyo on 2010-09-12
BUMP Again

---

### Post by Cigla on 2010-09-12
Hello!
I have Tiger Phillips TV card, and I tried the above method, with card id =81 (also with id=109, too), and now I have the picture from the card. But, I don't have the picture in TVtime, I have it in VLC player.(Open capture Device, video source=/dev/video0, set only frequency of the channel, PAL/NTSC, and width/height-mine is 700/400)
I have noticed something; while I was looking for the right card id, I've passed through these numbers once, and didn't get any results. But, I was repeating only the last command, *sudo modprobe -v saa7134 card=109*, but then I tried to repeat ALL the commands from above, again and again, changing id's. Don't know why, but now it is working!
Maybe this will help you, for more details, just ask if you haven't managed with this already.
Meanwhile, I'm looking for way to get sound, because **/dev/dsp dosn't work**. VLC keeps trying to open alsa:///dev/dsp, and not just /dev/dsp. If somebody knows the way how to enable sound, I'm asking for some help please?

---

### Post by alaukikyo on 2011-01-16
Bump

---

### Post by alaukikyo on 2011-01-21
bump

---

### Post by ani0079 on 2011-02-27
Hello guys my problem is quite similar too....
I've got a UMAX UTV8300i internal TV tuner which also has the SAA7130 chip and its not working with kdetv on Lucid...


Every kind of help will be welcome.....
:(:(:(:(:(:(:(:(

---

### Post by Peter J Schoen on 2011-04-26
Has any one got the Compro Videomate T100 working in Ubuntu?
It too! is based on the saa7130 Chip..:(

---

### Post by satish_j on 2011-04-26
you need to first execute foll command:
```

tvtime-scanner

```
which should scan the channels and save it in a configuration file.Then,you try tvtime..

---

### Post by sharan01 on 2011-05-21
hello i have problem with my tv tunner card 

> **sikander3786 said:**
> I have the same card and I got it working by  using the following commands under Ubuntu but it doesn't work with  mythtv, instead I use TVTime to view channels. Try it, check it in  TVTime if it is working and then go for mythtv I suggest.

```

sudo modprobe -vr saa7134_dvb

sudo modprobe -vr saa7134_alsa

sudo modprobe -vr saa7134

sudo modprobe -v saa7134 card=21

```
i have this card and did that but in tv time there is no input 
[SIZE=1]in windows it installs 10 moons driver[/SIZE]
[IMG]http://i.stack.imgur.com/dWlrC.jpg[/IMG]





> **satish_j said:**
> you need to first execute foll command:
```

tvtime-scanner

```which should scan the channels and save it in a configuration file.Then,you try tvtime..
i did that it says
```

Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.
videoinput: Can't get tuner info: Invalid argument
videoinput: Driver refuses to start streaming: Device or resource busy.
videoinput: Driver refuses to stop streaming: Invalid argument.
videoinput: Can't free frame 0: Invalid argument
videoinput: Can't free frame 1: Invalid argument
videoinput: Can't free frame 2: Invalid argument
videoinput: Can't free frame 3: Invalid argument
videoinput: Driver refuses to start streaming: Device or resource busy.
videoinput: Can't get tuner info: Invalid argument

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

videoinput: Driver refuses to stop streaming: Invalid argument.
videoinput: Can't free frame 0: Invalid argument
videoinput: Can't free frame 1: Invalid argument
videoinput: Can't free frame 2: Invalid argument
videoinput: Can't free frame 3: Invalid argument

```



please help

---

### Post by koftis on 2011-12-10
I do have the same tv card 

                         01:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
 
i've installed tvtime but i got some errors



> tvtime uvcvideo: Invalid argument
 Cannot open capure device/dev/video0.
 

> tvtime-scanner 
 Reading configuration from /etc/tvtime/tvtime.xml 
 Reading configuration from /home/okur/.tvtime/tvtime.xml 
 Scanning using TV standard NTSC. 
 videoinput: Driver won't tell us its norm: Invalid argument 
 videoinput: Can't get tuner info: Invalid argument 
  
     Your capture card driver: uvcvideo [USB2.0 PC CAMERA/usb-0000:00:02.0-2/65792] 
     does not support studio-quality colour images required by tvtime. 
     This is a hardware limitation of some cards including many 
     low-quality webcams.  Please select a different video device to use 
     with the command line option --device. 
  
     Message from the card was: Invalid argument 
Any thoughts?:(

---

### Post by koftis on 2011-12-11
Bumb!:)

---

