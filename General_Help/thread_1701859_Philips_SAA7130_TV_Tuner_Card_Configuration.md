---
title: "Philips SAA7130 TV Tuner Card Configuration"
date: 2011-03-07
forum: General Help
---

### Post by satish_j on 2011-03-07
Need help configuring TV Tuner Card(PCI) on Ubuntu.The model is Philips SAA7130.It is working fine in Windows with a software,Honestech,that shipped with it.
Command 'lspci' detects it properly in ubuntu.Have installed TVTime from synaptic.Read somewhere that card number and tuner number is required on Ubuntu.
Can someone help how to get these numbers,configure and get it working.

---

### Post by bance on 2011-03-07
Try [_[COLOR=Red]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=876719&highlight=Philips+SAA7130+TV+Tuner+Card") and [_[COLOR=Red]here[/COLOR]_]("http://www.linuxtv.org/wiki/index.php/Saa713x_devices") !


HTH Steve.

---

### Post by satish_j on 2011-03-08
Whenever i try to load the module using
```

sudo modprobe -v saa7134 card=42 tuner=xx

```
where,xx i tried was 37,38,3,17
 i get this Fatal error as:
```

error inserting saa7134_alsa(/lib/modules/2.6.32-28-generic/kernel/drivers/media/video/saa7134/saa7134-alsa.ko):unknown symbol in module, or unknown parameter(see dmesg)

```
I tried for 3 to 4 combinations of tuner as above.Every time, i got the above message.
Iam pretty sure the card number is 42 and i assume the tuner number should also be one of the above mentioned values,but this error is may be preventing loading of module.
Any ideas how to get rid of problem??

---

### Post by bance on 2011-03-08
What does dmesg say?

Perhaps you could post the output ?

---

### Post by satish_j on 2011-03-09
> **bance said:**
> What does dmesg say?

Perhaps you could post the output ?

THe output for dmesg is too large and i think you might b interested in something specific.Iam posting the output for 'dmesg|grep saa7134" as follows:
```

satish@Titan:~$ dmesg | grep saa7134
[   18.882948] saa7134 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.882962] saa7134: <rant>
[   18.882962] saa7134:  Congratulations!  Your TV card vendor saved a few
[   18.882964] saa7134:  cents for a eeprom, thus your pci board has no
[   18.882965] saa7134:  subsystem ID and I can't identify it automatically
[   18.882966] saa7134: </rant>
[   18.882967] saa7134: I feel better now.  Ok, here are the good news:
[   18.882968] saa7134: You can use the card=<nr> insmod option to specify
[   18.882969] saa7134: which board do you have.  The list:
[   18.882972] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   18.882976] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   18.882981] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   18.882986] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   18.882991] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   18.882995] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   18.882998] saa7134:   card=6 -> Tevion MD 9717                          
[   18.883002] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   18.883006] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   18.883010] saa7134:   card=9 -> Medion 5044                             
[   18.883014] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   18.883017] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   18.883021] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   18.883026] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   18.883029] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   18.883033] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   18.883037] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   18.883043] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   18.883047] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   18.883050] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   18.883054] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   18.883058] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   18.883062] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   18.883066] saa7134:   card=23 -> BMK MPEX Tuner                          
[   18.883069] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   18.883073] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   18.883077] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   18.883081] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   18.883085] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   18.883088] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   18.883092] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   18.883096] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   18.883100] saa7134:   card=32 -> AVACS SmartTV                           
[   18.883103] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   18.883107] saa7134:   card=34 -> Noval Prime TV 7133                     
[   18.883110] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   18.883114] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   18.883118] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   18.883121] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   18.883125] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   18.883131] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   18.883135] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   18.883139] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   18.883142] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   18.883146] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   18.883149] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   18.883153] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   18.883157] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   18.883161] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   18.883165] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   18.883169] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   18.883173] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   18.883176] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   18.883180] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   18.883184] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   18.883191] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   18.883196] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   18.883200] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   18.883204] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   18.883211] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   18.883214] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   18.883219] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   18.883223] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   18.883227] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   18.883230] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   18.883234] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   18.883237] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   18.883240] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   18.883244] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   18.883248] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   18.883252] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   18.883256] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   18.883260] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   18.883264] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   18.883268] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   18.883272] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   18.883276] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   18.883280] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   18.883284] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   18.883289] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   18.883292] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   18.883296] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   18.883300] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   18.883304] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   18.883308] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   18.883312] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   18.883317] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   18.883322] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   18.883326] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   18.883330] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   18.883334] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   18.883339] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   18.883343] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   18.883347] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   18.883351] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   18.883358] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   18.883362] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   18.883367] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   18.883372] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   18.883376] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   18.883380] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   18.883384] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   18.883388] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   18.883392] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   18.883395] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   18.883404] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   18.883408] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   18.883413] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   18.883417] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   18.883421] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   18.883425] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   18.883429] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   18.883433] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   18.883437] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   18.883441] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   18.883445] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   18.883449] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   18.883453] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   18.883457] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   18.883461] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   18.883465] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   18.883469] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   18.883473] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   18.883477] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   18.883481] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   18.883485] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   18.883489] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   18.883493] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   18.883497] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   18.883501] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   18.883505] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   18.883509] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   18.883513] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   18.883517] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   18.883520] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   18.883524] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   18.883528] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   18.883532] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   18.883535] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   18.883539] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   18.883543] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   18.883547] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   18.883551] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   18.883555] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   18.883559] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   18.883563] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   18.883568] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   18.883571] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   18.883575] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   18.883579] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   18.883583] saa7134:   card=150 -> Zogis Real Angel 220                    
[   18.883586] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   18.883590] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   18.883594] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   18.883598] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   18.883602] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   18.883607] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   18.883613] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   18.883617] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   18.883621] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   18.883625] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   18.883629] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   18.883633] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   18.883637] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   18.883641] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   18.883645] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   18.883649] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   18.883653] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   18.883656] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   18.883660] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
[   18.883664] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
[   18.883668] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
[   18.883672] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
[   18.883676] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
[   18.883680] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
[   18.992527] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   18.992531] saa7134_alsa: Unknown symbol snd_ctl_add
[   18.992636] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   18.992638] saa7134_alsa: Unknown symbol snd_pcm_new
[   18.992833] saa7134_alsa: disagrees about version of symbol snd_card_register
[   18.992836] saa7134_alsa: Unknown symbol snd_card_register
[   18.993031] saa7134_alsa: disagrees about version of symbol snd_card_free
[   18.993033] saa7134_alsa: Unknown symbol snd_card_free
[   18.993223] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   18.993225] saa7134_alsa: Unknown symbol snd_pcm_stop
[   18.993435] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   18.993437] saa7134_alsa: Unknown symbol snd_ctl_new1
[   18.994013] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   18.994015] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   18.994319] saa7134_alsa: disagrees about version of symbol snd_ctl_notify
[   18.994322] saa7134_alsa: Unknown symbol snd_ctl_notify
[   18.994417] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   18.994419] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   18.994719] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   18.994722] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   18.995179] saa7134_alsa: disagrees about version of symbol snd_card_create
[   18.995181] saa7134_alsa: Unknown symbol snd_card_create
[   18.995275] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   18.995277] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   18.995371] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.995373] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
satish@Titan:~$ 

```
As seen from above,it lists there some *saa7134_alsa:disagees about version.....*
Iam going nuts w/o tv on ubuntu..has to switch to XP and again to linux for work..desperately seeking solution:(:(

---

### Post by satish_j on 2011-03-10
OK,here is dmesg o/p..
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-28-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 (Ubuntu 2.6.32-28.55-generic 2.6.32.27+drm33.12)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f5e0000 (usable)
[    0.000000]  BIOS-e820: 000000003f5e0000 - 000000003f5e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5e3000 - 000000003f5f0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5f0000 - 000000003f600000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3f5e0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CAFFF write-protect
[    0.000000]   CB000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   3 base 03F600000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f5e0000 (usable)
[    0.000000]  modified: 000000003f5e0000 - 000000003f5e3000 (ACPI NVS)
[    0.000000]  modified: 000000003f5e3000 - 000000003f5f0000 (ACPI data)
[    0.000000]  modified: 000000003f5f0000 - 000000003f600000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2f10e000 - 2f8a718a
[    0.000000] ACPI: RSDP 000f6db0 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 3f5e3040 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 3f5e30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 3f5e3180 040E8 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 3f5e0000 00040
[    0.000000] ACPI: HPET 3f5e73c0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 3f5e7440 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: TAMG 3f5e7480 0625A (v01 GBT    GBT   B0 5455312E BG?? 00020101)
[    0.000000] ACPI: APIC 3f5e72c0 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 3f5edd40 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 125MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e0ed8]    TEXT DATA BSS ==> [0000100000 - 00008e0ed8]
[    0.000000]   #4 [002f10e000 - 002f8a718a]          RAMDISK ==> [002f10e000 - 002f8a718a]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008e1000 - 00008e40f6]              BRK ==> [00008e1000 - 00008e40f6]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f53c0] f53c0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f5e0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f5e0
[    0.000000] On node 0 totalpages: 259451
[    0.000000] free_area_init_node: node 0, pgdat c079c8c0, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 252 pages used for memmap
[    0.000000]   HighMem zone: 31974 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f600000 (gap: 3f600000:a0a00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257423
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-generic root=UUID=3b3a0f99-fb76-4d16-970c-5a514fcd22b1 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 5191040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f5e0)
[    0.000000] Memory: 1006880k/1038208k available (4685k kernel code, 30140k reserved, 2125k data, 660k init, 128904k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a7000 - 0xc084c000   ( 660 kB)
[    0.000000]       .data : 0xc05936e7 - 0xc07a6e88   (2125 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05936e7   (4685 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2699.587 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5399.17 BogoMIPS (lpj=10798348)
[    0.004022] Security Framework initialized
[    0.004038] AppArmor: AppArmor initialized
[    0.004045] Mount-cache hash table entries: 512
[    0.004163] Initializing cgroup subsys ns
[    0.004167] Initializing cgroup subsys cpuacct
[    0.004172] Initializing cgroup subsys memory
[    0.004179] Initializing cgroup subsys devices
[    0.004181] Initializing cgroup subsys freezer
[    0.004184] Initializing cgroup subsys net_cls
[    0.004205] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004208] CPU: L2 cache: 2048K
[    0.004211] CPU: Physical Processor ID: 0
[    0.004213] CPU: Processor Core ID: 0
[    0.004217] mce: CPU supports 6 MCE banks
[    0.004225] CPU0: Thermal monitoring enabled (TM2)
[    0.004228] using mwait in idle threads.
[    0.004234] Performance Events: Core2 events, Intel PMU driver.
[    0.004242] ... version:                2
[    0.004244] ... bit width:              40
[    0.004246] ... generic registers:      2
[    0.004248] ... value mask:             000000ffffffffff
[    0.004250] ... max period:             000000007fffffff
[    0.004252] ... fixed-purpose events:   3
[    0.004254] ... event mask:             0000000700000003
[    0.004260] Checking 'hlt' instruction... OK.
[    0.023279] ACPI: Core revision 20090903
[    0.030287] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030295] ftrace: allocating 21796 entries in 43 pages
[    0.032058] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032370] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073656] CPU0: Intel Pentium(R) Dual-Core  CPU      E5400  @ 2.70GHz stepping 0a
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.160106] CPU1: Intel Pentium(R) Dual-Core  CPU      E5400  @ 2.70GHz stepping 0a
[    0.160116] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164020] Brought up 2 CPUs
[    0.164023] Total of 2 processors activated (10799.13 BogoMIPS).
[    0.164615] CPU0 attaching sched-domain:
[    0.164619]  domain 0: span 0-1 level MC
[    0.164622]   groups: 0 1
[    0.164628] CPU1 attaching sched-domain:
[    0.164630]  domain 0: span 0-1 level MC
[    0.164633]   groups: 1 0
[    0.164704] devtmpfs: initialized
[    0.164704] regulator: core version 0.5
[    0.164704] Time: 21:04:24  Date: 03/10/11
[    0.164704] NET: Registered protocol family 16
[    0.164704] Trying to unpack rootfs image as initramfs...
[    0.164704] EISA bus registered
[    0.164704] ACPI: bus type pci registered
[    0.164704] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164704] PCI: MCFG area at e0000000 reserved in E820
[    0.164704] PCI: Using MMCONFIG for extended config space
[    0.164704] PCI: Using configuration type 1 for base access
[    0.172138] bio: create slab <bio-0> at 0
[    0.172826] ACPI: EC: Look up EC in DSDT
[    0.178633] ACPI: Interpreter enabled
[    0.178642] ACPI: (supports S0 S3 S4 S5)
[    0.178668] ACPI: Using IOAPIC for interrupt routing
[    0.185914] ACPI Warning: Incorrect checksum in table [TAMG] - E7, should be E6 (20090903/tbutils-314)
[    0.186041] ACPI: No dock devices found.
[    0.186145] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.186240] pci 0000:00:02.0: reg 10 32bit mmio: [0xfdf00000-0xfdf7ffff]
[    0.186245] pci 0000:00:02.0: reg 14 io port: [0xff00-0xff07]
[    0.186251] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.186257] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.186340] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff8000-0xfdffbfff]
[    0.186386] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.186390] pci 0000:00:1b.0: PME# disabled
[    0.186459] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.186463] pci 0000:00:1c.0: PME# disabled
[    0.186532] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.186536] pci 0000:00:1c.1: PME# disabled
[    0.186588] pci 0000:00:1d.0: reg 20 io port: [0xfe00-0xfe1f]
[    0.186640] pci 0000:00:1d.1: reg 20 io port: [0xfd00-0xfd1f]
[    0.186690] pci 0000:00:1d.2: reg 20 io port: [0xfc00-0xfc1f]
[    0.186742] pci 0000:00:1d.3: reg 20 io port: [0xfb00-0xfb1f]
[    0.186790] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.186963] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.186968] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.186973] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.186977] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.187020] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.187028] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.187035] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.187042] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.187049] pci 0000:00:1f.1: reg 20 io port: [0xf800-0xf80f]
[    0.187091] pci 0000:00:1f.2: reg 10 io port: [0xf700-0xf707]
[    0.187098] pci 0000:00:1f.2: reg 14 io port: [0xf600-0xf603]
[    0.187104] pci 0000:00:1f.2: reg 18 io port: [0xf500-0xf507]
[    0.187111] pci 0000:00:1f.2: reg 1c io port: [0xf400-0xf403]
[    0.187117] pci 0000:00:1f.2: reg 20 io port: [0xf300-0xf30f]
[    0.187142] pci 0000:00:1f.2: PME# supported from D3hot
[    0.187146] pci 0000:00:1f.2: PME# disabled
[    0.187194] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.187262] pci 0000:00:1c.0: bridge io port: [0xc000-0xcfff]
[    0.187266] pci 0000:00:1c.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
[    0.187273] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
[    0.187332] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdec0000-0xfdefffff]
[    0.187342] pci 0000:02:00.0: reg 18 io port: [0xbf00-0xbf7f]
[    0.187407] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.187412] pci 0000:02:00.0: PME# disabled
[    0.187468] pci 0000:00:1c.1: bridge io port: [0xb000-0xbfff]
[    0.187473] pci 0000:00:1c.1: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.187480] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.187517] pci 0000:03:01.0: reg 10 32bit mmio: [0xfdbff000-0xfdbff3ff]
[    0.187568] pci 0000:03:01.0: supports D1 D2
[    0.187616] pci 0000:00:1e.0: transparent bridge
[    0.187620] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.187625] pci 0000:00:1e.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.187631] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
[    0.187647] pci_bus 0000:00: on NUMA node 0
[    0.187652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.187845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.187908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.187983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.200545] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.200651] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.200753] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.200855] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.200955] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.201058] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.201162] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.201264] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.201392] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.201405] vgaarb: loaded
[    0.201540] SCSI subsystem initialized
[    0.201738] libata version 3.00 loaded.
[    0.201738] usbcore: registered new interface driver usbfs
[    0.201739] usbcore: registered new interface driver hub
[    0.201768] usbcore: registered new device driver usb
[    0.201905] ACPI: WMI: Mapper loaded
[    0.201908] PCI: Using ACPI for IRQ routing
[    0.202077] NetLabel: Initializing
[    0.202079] NetLabel:  domain hash size = 128
[    0.202081] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.202096] NetLabel:  unlabeled traffic allowed by default
[    0.202129] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.202135] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.212029] Switching to clocksource tsc
[    0.214351] AppArmor: AppArmor Filesystem Enabled
[    0.214367] pnp: PnP ACPI init
[    0.214389] ACPI: bus type pnp registered
[    0.217396] pnp: PnP ACPI: found 16 devices
[    0.217399] ACPI: ACPI bus type pnp unregistered
[    0.217405] PnPBIOS: Disabled by ACPI PNP
[    0.217418] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.217421] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.217424] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.217427] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.217431] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.217441] system 00:0c: ioport range 0x400-0x4cf could not be reserved
[    0.217448] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.217454] system 00:0e: iomem range 0xcb400-0xcbfff has been reserved
[    0.217457] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[    0.217460] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.217463] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.217467] system 00:0e: iomem range 0x3f5e0000-0x3f5fffff could not be reserved
[    0.217470] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.217473] system 00:0e: iomem range 0x100000-0x3f5dffff could not be reserved
[    0.217476] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.217480] system 00:0e: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.217483] system 00:0e: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.217486] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.217489] system 00:0e: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.217492] system 00:0e: iomem range 0xfff00000-0xffffffff has been reserved
[    0.217495] system 00:0e: iomem range 0xe0000-0xeffff has been reserved
[    0.252236] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.252240] pci 0000:00:1c.0:   IO window: 0xc000-0xcfff
[    0.252246] pci 0000:00:1c.0:   MEM window: 0xfd900000-0xfd9fffff
[    0.252251] pci 0000:00:1c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.252258] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.252261] pci 0000:00:1c.1:   IO window: 0xb000-0xbfff
[    0.252267] pci 0000:00:1c.1:   MEM window: 0xfde00000-0xfdefffff
[    0.252271] pci 0000:00:1c.1:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.252278] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.252282] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.252287] pci 0000:00:1e.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.252292] pci 0000:00:1e.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.252312]   alloc irq_desc for 16 on node -1
[    0.252314]   alloc kstat_irqs on node -1
[    0.252323] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.252329] pci 0000:00:1c.0: setting latency timer to 64
[    0.252337]   alloc irq_desc for 17 on node -1
[    0.252339]   alloc kstat_irqs on node -1
[    0.252343] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.252348] pci 0000:00:1c.1: setting latency timer to 64
[    0.252355] pci 0000:00:1e.0: setting latency timer to 64
[    0.252360] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.252363] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.252366] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.252369] pci_bus 0000:01: resource 1 mem: [0xfd900000-0xfd9fffff]
[    0.252372] pci_bus 0000:01: resource 2 pref mem [0xfd800000-0xfd8fffff]
[    0.252374] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.252377] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.252380] pci_bus 0000:02: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.252383] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.252386] pci_bus 0000:03: resource 1 mem: [0xfdb00000-0xfdbfffff]
[    0.252389] pci_bus 0000:03: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.252392] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.252394] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.252437] NET: Registered protocol family 2
[    0.252558] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.252918] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.253408] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.253627] TCP: Hash tables configured (established 131072 bind 65536)
[    0.253630] TCP reno registered
[    0.253733] NET: Registered protocol family 1
[    0.253756] pci 0000:00:02.0: Boot video device
[    0.254054] cpufreq-nforce2: No nForce2 chipset.
[    0.254085] Scanning for low memory corruption every 60 seconds
[    0.254209] audit: initializing netlink socket (disabled)
[    0.254221] type=2000 audit(1299791064.251:1): initialized
[    0.265352] highmem bounce pool size: 64 pages
[    0.265359] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.267092] VFS: Disk quotas dquot_6.5.2
[    0.267160] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.267822] fuse init (API version 7.13)
[    0.267914] msgmni has been set to 1716
[    0.268147] alg: No test for stdrng (krng)
[    0.268205] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.268208] io scheduler noop registered
[    0.268210] io scheduler anticipatory registered
[    0.268213] io scheduler deadline registered
[    0.268255] io scheduler cfq registered (default)
[    0.268399]   alloc irq_desc for 24 on node -1
[    0.268401]   alloc kstat_irqs on node -1
[    0.268412] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.268422] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.268546]   alloc irq_desc for 25 on node -1
[    0.268548]   alloc kstat_irqs on node -1
[    0.268555] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.268564] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.268655] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.268735] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.268832] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.268836] ACPI: Power Button [PWRB]
[    0.268897] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.268900] ACPI: Power Button [PWRF]
[    0.269401] ACPI: SSDT 3f5ed720 0022A (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.269640] processor LNXCPU:00: registered as cooling_device0
[    0.269858] ACPI: SSDT 3f5edbe0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.270070] processor LNXCPU:01: registered as cooling_device1
[    0.273569] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.273668] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.274067] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.275308] brd: module loaded
[    0.275848] loop: module loaded
[    0.275934] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.276034] ata_piix 0000:00:1f.1: version 2.13
[    0.276048]   alloc irq_desc for 18 on node -1
[    0.276051]   alloc kstat_irqs on node -1
[    0.276058] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.276097] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.276177] scsi0 : ata_piix
[    0.276252] scsi1 : ata_piix
[    0.276957] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf800 irq 14
[    0.276960] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf808 irq 15
[    0.276984]   alloc irq_desc for 19 on node -1
[    0.276986]   alloc kstat_irqs on node -1
[    0.276991] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.276996] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.277024] isapnp: Scanning for PnP cards...
[    0.277033] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.277306] scsi2 : ata_piix
[    0.277362] scsi3 : ata_piix
[    0.277937] ata3: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf300 irq 19
[    0.277940] ata4: SATA max UDMA/133 cmd 0xf500 ctl 0xf400 bmdma 0xf308 irq 19
[    0.278304] Fixed MDIO Bus: probed
[    0.278342] PPP generic driver version 2.4.2
[    0.278380] tun: Universal TUN/TAP device driver, 1.6
[    0.278382] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.278474] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.278492]   alloc irq_desc for 23 on node -1
[    0.278494]   alloc kstat_irqs on node -1
[    0.278499] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.278513] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.278517] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.278550] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.278567] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.282459] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.282492] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    0.295964] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.296074] usb usb1: configuration #1 chosen from 1 choice
[    0.296109] hub 1-0:1.0: USB hub found
[    0.296117] hub 1-0:1.0: 8 ports detected
[    0.296187] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.296204] uhci_hcd: USB Universal Host Controller Interface driver
[    0.296243] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.296251] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.296255] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.296295] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.296320] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fe00
[    0.296416] usb usb2: configuration #1 chosen from 1 choice
[    0.296444] hub 2-0:1.0: USB hub found
[    0.296451] hub 2-0:1.0: 2 ports detected
[    0.296502] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.296508] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.296511] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.296544] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.296567] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fd00
[    0.296655] usb usb3: configuration #1 chosen from 1 choice
[    0.296682] hub 3-0:1.0: USB hub found
[    0.296689] hub 3-0:1.0: 2 ports detected
[    0.296732] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.296738] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.296741] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.296773] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.296803] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[    0.296894] usb usb4: configuration #1 chosen from 1 choice
[    0.296921] hub 4-0:1.0: USB hub found
[    0.296931] hub 4-0:1.0: 2 ports detected
[    0.296974] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.296980] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.296983] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.297020] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.297049] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[    0.297144] usb usb5: configuration #1 chosen from 1 choice
[    0.297171] hub 5-0:1.0: USB hub found
[    0.297178] hub 5-0:1.0: 2 ports detected
[    0.297287] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.297711] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.297717] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.297797] mice: PS/2 mouse device common for all mice
[    0.297915] rtc_cmos 00:04: RTC can wake from S4
[    0.297954] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.297978] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.298089] device-mapper: uevent: version 1.0.3
[    0.314387] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.326338] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.339945] device-mapper: multipath: version 1.1.0 loaded
[    0.339948] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.340108] EISA: Probing bus 0 at eisa.0
[    0.340138] EISA: Detected 0 cards.
[    0.355915] cpuidle: using governor ladder
[    0.355919] cpuidle: using governor menu
[    0.356396] TCP cubic registered
[    0.356576] NET: Registered protocol family 10
[    0.357113] lo: Disabled Privacy Extensions
[    0.357500] NET: Registered protocol family 17
[    0.359378] Using IPI No-Shortcut mode
[    0.359492] PM: Resume from disk failed.
[    0.359506] registered taskstats version 1
[    0.359805]   Magic number: 3:473:95
[    0.359877] rtc_cmos 00:04: setting system clock to 2011-03-10 21:04:24 UTC (1299791064)
[    0.359881] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.359883] EDD information not available.
[    0.401212] Freeing initrd memory: 7780k freed
[    0.631187] isapnp: No Plug & Play device found
[    0.667925] ata1.00: HPA unlocked: 312579695 -> 312581808, native 312581808
[    0.667931] ata1.00: ATA-7: ST3160215A, 3.AAD, max UDMA/100
[    0.667934] ata1.00: 312581808 sectors, multi 16: LBA48 
[    0.677582] ata1.01: ATA-7: WDC WD1600AABB-22PUA0, 00.07H00, max UDMA/100
[    0.677588] ata1.01: 312581808 sectors, multi 16: LBA48 
[    0.718935] ata1.00: configured for UDMA/100
[    0.724601] ata1.01: configured for UDMA/100
[    0.724777] scsi 0:0:0:0: Direct-Access     ATA      ST3160215A       3.AA PQ: 0 ANSI: 5
[    0.724925] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.724974] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.724977] sd 0:0:0:0: [sda] Write Protect is off
[    0.724980] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.725005] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.725116] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1600AABB-2 00.0 PQ: 0 ANSI: 5
[    0.725164]  sda:
[    0.725217] sd 0:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.725236] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    0.725262] sd 0:0:1:0: [sdb] Write Protect is off
[    0.725265] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    0.725300] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.725421]  sdb: sdb1 sdb2 sdb3
[    0.766817]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    0.781070] sd 0:0:1:0: [sdb] Attached SCSI disk
[    0.781401] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.781417] Freeing unused kernel memory: 660k freed
[    0.781856] Write protecting the kernel text: 4688k
[    0.781901] Write protecting the kernel read-only data: 1844k
[    0.799170] udev: starting version 151
[    0.887071] Floppy drive(s): fd0 is 1.44M
[    0.907573] FDC 0 is a post-1991 82077
[    6.289208] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   18.012156] udev: starting version 151
[   18.064174] Linux agpgart interface v0.103
[   18.113356] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   18.114160] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   18.259570] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   18.264512] [drm] Initialized drm 1.1.0 20060810
[   18.267630] intel_rng: FWH not detected
[   18.273641] atl1c 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.273655] atl1c 0000:02:00.0: setting latency timer to 64
[   18.294900] parport_pc 00:09: reported by Plug and Play ACPI
[   18.294949] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   18.308040] Linux video capture interface: v2.00
[   18.314372] ppdev: user-space parallel port driver
[   18.321262] lp: driver loaded but no devices found
[   18.346361] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.346368] i915 0000:00:02.0: setting latency timer to 64
[   18.351614] type=1505 audit(1299771282.488:2):  operation="profile_load" pid=587 name="/sbin/dhclient3"
[   18.352584] type=1505 audit(1299771282.492:3):  operation="profile_load" pid=587 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.353025] type=1505 audit(1299771282.492:4):  operation="profile_load" pid=587 name="/usr/lib/connman/scripts/dhclient-script"
[   18.356637]   alloc irq_desc for 26 on node -1
[   18.356640]   alloc kstat_irqs on node -1
[   18.356650] i915 0000:00:02.0: irq 26 for MSI/MSI-X
[   18.356657] [drm] set up 7M of stolen space
[   18.357211] [drm] initialized overlay support
[   18.370960] saa7130/34: v4l2 driver version 0.2.15 loaded
[   18.371009] saa7134 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.371016] saa7130[0]: found at 0000:03:01.0, rev: 1, irq: 19, latency: 32, mmio: 0xfdbff000
[   18.371022] saa7134: <rant>
[   18.371023] saa7134:  Congratulations!  Your TV card vendor saved a few
[   18.371024] saa7134:  cents for a eeprom, thus your pci board has no
[   18.371025] saa7134:  subsystem ID and I can't identify it automatically
[   18.371027] saa7134: </rant>
[   18.371027] saa7134: I feel better now.  Ok, here are the good news:
[   18.371029] saa7134: You can use the card=<nr> insmod option to specify
[   18.371030] saa7134: which board do you have.  The list:
[   18.371033] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   18.371036] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   18.371042] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   18.371046] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   18.371051] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   18.371055] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   18.371059] saa7134:   card=6 -> Tevion MD 9717                          
[   18.371062] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   18.371067] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   18.371071] saa7134:   card=9 -> Medion 5044                             
[   18.371074] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   18.371077] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   18.371081] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   18.371086] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   18.371089] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   18.371093] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   18.371097] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   18.371103] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   18.371107] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   18.371110] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   18.371114] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   18.371118] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   18.371122] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   18.371126] saa7134:   card=23 -> BMK MPEX Tuner                          
[   18.371129] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   18.371133] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   18.371137] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   18.371141] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   18.371144] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   18.371147] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   18.371151] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   18.371155] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   18.371159] saa7134:   card=32 -> AVACS SmartTV                           
[   18.371162] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   18.371166] saa7134:   card=34 -> Noval Prime TV 7133                     
[   18.371169] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   18.371173] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   18.371177] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   18.371180] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   18.371184] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   18.371190] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   18.371194] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   18.371198] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   18.371201] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   18.371204] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   18.371207] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   18.371211] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   18.371215] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   18.371219] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   18.371223] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   18.371227] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   18.371231] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   18.371235] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   18.371239] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   18.371243] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   18.371250] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   18.371254] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   18.371258] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   18.371262] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   18.371269] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   18.371272] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   18.371278] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   18.371282] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   18.371285] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   18.371288] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   18.371292] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   18.371295] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   18.371298] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   18.371302] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   18.371306] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   18.371310] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   18.371314] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   18.371318] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   18.371322] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   18.371326] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   18.371330] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   18.371334] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   18.371338] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   18.371342] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   18.371346] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   18.371349] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   18.371353] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   18.371357] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   18.371362] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   18.371366] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   18.371370] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   18.371375] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   18.371379] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   18.371383] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   18.371387] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   18.371391] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   18.371396] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   18.371400] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   18.371404] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   18.371408] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   18.371414] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   18.371418] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   18.371424] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   18.371429] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   18.371433] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   18.371437] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   18.371441] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   18.371445] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   18.371449] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   18.371452] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   18.371460] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   18.371464] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   18.371469] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   18.371473] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   18.371478] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   18.371481] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   18.371485] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   18.371488] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   18.371493] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   18.371497] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   18.371501] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   18.371505] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   18.371509] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   18.371512] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   18.371516] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   18.371520] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   18.371524] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   18.371528] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   18.371532] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   18.371536] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   18.371540] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   18.371544] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   18.371548] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   18.371553] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   18.371557] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   18.371560] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   18.371565] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   18.371569] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   18.371572] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   18.371575] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   18.371579] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   18.371583] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   18.371587] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   18.371591] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   18.371595] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   18.371598] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   18.371602] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   18.371606] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   18.371610] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   18.371614] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   18.371618] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   18.371623] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   18.371626] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   18.371630] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   18.371634] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   18.371638] saa7134:   card=150 -> Zogis Real Angel 220                    
[   18.371641] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   18.371645] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   18.371649] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   18.371653] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   18.371657] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   18.371662] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   18.371668] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   18.371672] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   18.371676] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   18.371680] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   18.371684] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   18.371688] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   18.371692] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   18.371696] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   18.371700] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   18.371704] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   18.371708] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   18.371712] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   18.371716] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
[   18.371720] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
[   18.371724] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
[   18.371728] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
[   18.371732] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
[   18.371736] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
[   18.371741] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   18.371756] saa7130[0]: board init: gpio is 4000
[   18.371761] IRQ 19/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   18.376205] lp0: using parport0 (interrupt-driven).
[   18.377333] atl1c 0000:02:00.0: version 1.0.0.1-NAPI
[   18.422874]   alloc irq_desc for 27 on node -1
[   18.422878]   alloc kstat_irqs on node -1
[   18.422893] atl1c 0000:02:00.0: irq 27 for MSI/MSI-X
[   18.423262] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.472847] saa7130[0]: Huh, no eeprom present (err=-5)?
[   18.472852] i2c i2c-1: Invalid 7-bit address 0x7a
[   18.473444] saa7130[0]: registered device video0 [v4l2]
[   18.473475] saa7130[0]: registered device vbi0
[   18.476424] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   18.476428] saa7134_alsa: Unknown symbol snd_ctl_add
[   18.476551] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   18.476554] saa7134_alsa: Unknown symbol snd_pcm_new
[   18.476750] saa7134_alsa: disagrees about version of symbol snd_card_register
[   18.476752] saa7134_alsa: Unknown symbol snd_card_register
[   18.476948] saa7134_alsa: disagrees about version of symbol snd_card_free
[   18.476950] saa7134_alsa: Unknown symbol snd_card_free
[   18.477145] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   18.477147] saa7134_alsa: Unknown symbol snd_pcm_stop
[   18.477357] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   18.477359] saa7134_alsa: Unknown symbol snd_ctl_new1
[   18.477935] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   18.477937] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   18.478237] saa7134_alsa: disagrees about version of symbol snd_ctl_notify
[   18.478240] saa7134_alsa: Unknown symbol snd_ctl_notify
[   18.478334] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   18.478337] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   18.478633] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   18.478636] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   18.479078] saa7134_alsa: disagrees about version of symbol snd_card_create
[   18.479080] saa7134_alsa: Unknown symbol snd_card_create
[   18.479174] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   18.479176] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   18.479270] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.479273] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   18.521088] fb0: inteldrmfb frame buffer device
[   18.521091] registered panic notifier
[   18.521114] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.521154] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.521191]   alloc irq_desc for 28 on node -1
[   18.521194]   alloc kstat_irqs on node -1
[   18.521206] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X
[   18.521230] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.523916] vga16fb: initializing
[   18.523920] vga16fb: mapped to 0xc00a0000
[   18.523924] vga16fb: not registering due to another framebuffer present
[   18.525613] psmouse serio1: ID: 10 00 64
[   18.573339] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4
[   18.577350] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.577409] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.588112] Console: switching to colour frame buffer device 128x48
[   18.627311] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.633333] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.639274] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.742975] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.749217] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.756853] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.765251] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.772834] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.780982] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.788942] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.797609] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.805152] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   18.806191] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.815508] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.825551] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.833264] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.840868] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.848808] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.856076] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.865747] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.873546] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.880756] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.888790] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.896812] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.904820] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.911709] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.918358] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.925484] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.937111] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.943322] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.953777] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.960695] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.970010] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.980852] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.987457] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.996831] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.004787] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.011350] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.016941] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.028792] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.036815] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.043398] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.052815] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.060783] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   19.918780] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   19.919025] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.240583] type=1505 audit(1299771284.380:5):  operation="profile_replace" pid=959 name="/sbin/dhclient3"
[   20.241379] type=1505 audit(1299771284.380:6):  operation="profile_replace" pid=959 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.241960] type=1505 audit(1299771284.380:7):  operation="profile_replace" pid=959 name="/usr/lib/connman/scripts/dhclient-script"
[   20.242860] type=1505 audit(1299771284.380:8):  operation="profile_load" pid=958 name="/usr/share/gdm/guest-session/Xsession"
[   20.249641] type=1505 audit(1299771284.388:9):  operation="profile_load" pid=1024 name="/usr/lib/cups/backend/cups-pdf"
[   20.250606] type=1505 audit(1299771284.388:10):  operation="profile_load" pid=1024 name="/usr/sbin/cupsd"
[   20.254055] type=1505 audit(1299771284.392:11):  operation="profile_load" pid=1025 name="/usr/sbin/tcpdump"
[   21.027668] CPU0 attaching NULL sched-domain.
[   21.027674] CPU1 attaching NULL sched-domain.
[   21.048586] CPU0 attaching sched-domain:
[   21.048590]  domain 0: span 0-1 level MC
[   21.048593]   groups: 0 1
[   21.048600] CPU1 attaching sched-domain:
[   21.048602]  domain 0: span 0-1 level MC
[   21.048605]   groups: 1 0
[   22.384943] CPU0 attaching NULL sched-domain.
[   22.384949] CPU1 attaching NULL sched-domain.
[   22.404574] CPU0 attaching sched-domain:
[   22.404578]  domain 0: span 0-1 level MC
[   22.404580]   groups: 0 1
[   22.404588] CPU1 attaching sched-domain:
[   22.404590]  domain 0: span 0-1 level MC
[   22.404593]   groups: 1 0
[   30.616017] eth0: no IPv6 routers present

```
Can anyone help me wid this???

---

### Post by satish_j on 2011-03-11
no one!!!:(:(

---

### Post by johntaylor1887 on 2011-03-11
Did you check on linuxtv.org for possible answers?

---

### Post by wkulecz on 2011-03-11
> Did you check on linuxtv.org for possible answers?

Good luck with that!  What he needs is glaringly missing from the site -- a mapping of physical cards/devices that you can actually buy to the drivers that work with them.  USB devices are in even worse shape!  At least the SAA driver dumps a list of the possibilities you can view with dmesg.


You have to try to map the name of the card you actually have to one of the 174 card= numbers dumped in the SAA dmesg printout.

If you find it, and get the Composite or S-Video inputs to work you can worry about the finding the tuner ID number.

This is a mess -- the whole video4linux thing is pretty poor, and v4l2 seems to have made it worse not better.

---

### Post by satish_j on 2011-03-12
> **johntaylor1887 said:**
> Did you check on linuxtv.org for possible answers?

I have checked number of threads on this and found that a working combination of Card number and tuner number has to be provided at time of loading module through 'modprobe'
Bu,whenevr i try to load module saa7134 wth different combinations of card and tuner number, i always get this  'error inserting saa7134_alsa' error(pls see my prev post),so,i suspect whether this error is what is preventing the saa7134 module to load and thus making further testing with tvtime useless.
I have tried NUMBER OF COMBINATIONS for card and tuner number,but have still not got the picture in tvtime..
Is there no other way to get the correct card and tuner number???
May be from XP though some registry hack(apologize for asking XP related )

---

### Post by bance on 2011-03-14
There is a bug in relation to this. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/603536](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/603536)

I don't know if this helps any.....

Maybe if you could post more info on the card, there are lots that use the saa713x chip

---

### Post by satish_j on 2011-03-15
> **bance said:**
> There is a bug in relation to this. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/603536](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/603536)

I don't know if this helps any.....

Maybe if you could post more info on the card, there are lots that use the saa713x chip

Thanks for the follow-up..However,i saw that bug,but it is related to audio part of saa7134 chip.Iam not even getting the video in Tvtime.
One thing that is confirmed now is that the message 'error inserting saa7134_alsa' that comes on loading the saa7134 module has got nothing to do with Video part.
Now,the trickiest part is how to do i get video running.
I want to confirm one more thing:
Every time i load saa7134 with varying combination of card and tuner number,i start TVtime and switch to all modes(TV,Composite,etc..)to check video.I always get this 'No Signal' message in TVTime.I have tried 50 such combinations(card & tuner) and sometimes,i do get to hear some audio(with lots of noise)on loading the module
I DO NOT SCAN THE FREQUENCIES.Do i need to scan after loading the module everytime?

---

### Post by johntaylor1887 on 2011-03-15
No slight to the good people here, but maybe the members over at MythTV forums could also help. They have a lot of experience with tuner cards in linux.

---

### Post by satish_j on 2011-03-19
Now,this is strange..Iam using XP,Fedora14 along with Ubuntu.
Installed TVTime in fedora,used card=10 in /etc/modprobe.d/saa7134.rebooted and got the video running in TVTime.
Although i cannot scan for more channels as it gives some error on 'tvtime-scanner',but atleast it detected one channel and shows the video.
BUT,the same CARD=10 in Ubuntu is still giving me 'No Signal' message.
I suppose both Linux OS should work with same set of card and tuner settings.:confused::confused::confused:
Any inputs now???

---

### Post by johntaylor1887 on 2011-03-19
What did you do to scan for channels?
```
tvtime-scanner
```
is what should be done.

---

### Post by satish_j on 2011-03-20
> **johntaylor1887 said:**
> What did you do to scan for channels?
```
tvtime-scanner
```
is what should be done.

I used this same command ,but it gives error as _' No tuner found on input 0.  If you have a tuner, please select a different input using --input=<num>.'_

---

### Post by satish_j on 2011-03-29
OK..that 'No tuner found on input 0' message is gone now.
tvtime-scanner starts scanning for channels,but could not find any channel.
It shows this 'No Signal' message at command prompt.TVTime application also displays this same message.
Does this give any clue to anyone??What should i do to get tvtime scan for channels.

---

### Post by s.fox on 2011-03-29
Thread moved to [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331") at original posters request.

---

### Post by wolfen69 on 2011-03-31
[This]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux") person was able to get it going. Good luck.

---

### Post by satish_j on 2011-04-07
> **wolfen69 said:**
> [This]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux") person was able to get it going. Good luck.

I have tried that suggestion with no success.
Eventually,it seems that the TV Tuner card iam using has not come shipped with EEPROM address and thus i have to do trial method for card and tuner number.Problem is:--i have already tried very large number of card/tuner combinations..
This TV card is working fine in Windows..i was wondering whether i find the card and tuner number from windows using any registry hack...

---

### Post by satish_j on 2011-04-13
okay,i have solved this problem by adding foll in /etc/modprobe.d/saa7134.conf
```

 options saa7134 card=42 **gbuffers=4**

```
earlier i was trying various tuner and card number combinations w/o any success.But,when i added this 'gbuffers=4' and rebooted and scanned for channels,it started detecting channels properly.
At that point,i concluded that gbuffers=4 was the answer to my problem.As a test,i removed gbuffers again expecting TVTime to stop working.But,after rebooting,TVtime was showing all channels that were scanned earlier(something that amazed me)
So,i know not the exact cause of the problem.
I have now one more problem,which is related to remote control,for which i have raised a separate thread at [http://ubuntuforums.org/showthread.php?t=1726324](http://ubuntuforums.org/showthread.php?t=1726324)
It would be help me if anyone can shed some input on remote configuration..;)

---

### Post by Peter J Schoen on 2011-04-26
> **wolfen69 said:**
> [This]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux") person was able to get it going. Good luck.

Been there done that!
Followed instructions to the letter, except in between suggested attempts, I shut down and removed the Power cord for 30 seconds or more!..

I tried all card numbers for my Compro Videomate T100 but it just wont pick up an Australian Pal signal..

---

### Post by radiobuzzer on 2012-01-31
Is there any tip on how to use FM radio of this particular card with Ubuntu?

---

### Post by takien on 2012-02-25
how to find card number?

---

