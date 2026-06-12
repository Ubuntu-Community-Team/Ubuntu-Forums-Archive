---
title: "Ubuntu doesnt Hibernate"
date: 2009-07-30
forum: General Help
---

### Post by MichealH on 2009-07-30
Yesterday I installed the latest version of Ubuntu (9.04) on my laptop and instead of shutting down I am more comfortable with my laptop hibernating but when I click "Hibernate" it sends me to my screen saver without turning the laptop off. Why?

---

### Post by MichealH on 2009-07-30
Please , I really need help on this and I remember it does the same for "Suspend":confused::confused::confused:[SIZE=4]](*,)[/SIZE]

---

### Post by MichealH on 2009-07-30
Really need Help PLEASE people Help!!!!!!!!!!!

---

### Post by sarfarazkazi on 2009-07-30
Can you post the output of /var/log/pm-suspend.log? What make/model is your laptop?

---

### Post by MichealH on 2009-07-30
Here is the pm-suspend.log file:
```
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Wed Jul 29 19:50:03 BST 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux micheal-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    58272  1 vfat
usb_storage            82880  0 
sis                    13952  1 
drm                    96296  2 sis
sisfb                 251988  1 sis
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
arc4                    9856  2 
ecb                    10752  2 
uvcvideo               63240  0 
ath5k                 107008  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32          9344  1 uvcvideo
mac80211              217208  1 ath5k
soundcore              15200  1 snd
videodev               41600  1 uvcvideo
sis_agp                15360  1 
sis190                 26116  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
pcspkr                 10496  0 
v4l1_compat            21764  2 uvcvideo,videodev
cfg80211               38032  2 ath5k,mac80211
shpchp                 40212  0 
agpgart                42696  2 drm,sis_agp
mii                    13312  1 sis190
psmouse                61972  0 
serio_raw              13316  0 
asus_laptop            24440  0 
led_class              12036  2 ath5k,asus_laptop
video                  25360  0 
output                 11008  1 video
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       1414508    1270572     143936          0      75104     745960
-/+ buffers/cache:     449508     965000
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/45iwlist hibernate hibernate: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90chvt hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: not applicable.
/etc/pm/sleep.d/99laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Wed Jul 29 19:50:05 BST 2009: performing hibernate
Wed Jul 29 19:50:16 BST 2009: Awake.
Wed Jul 29 19:50:16 BST 2009: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/etc/pm/sleep.d/99laptop-mode thaw hibernate: Laptop mode disabled, not active
success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: /usr/lib/pm-utils/sleep.d/95hdparm-apm: 50: get_power_status: not found

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
success.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90chvt thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci thaw hibernate: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/45iwlist thaw hibernate: /sbin/iwlist
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:8C:23:4E
                    ESSID:"SKY86312"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=7/100  Signal level:-99 dBm  Noise level=-104 dBm
                    Encryption key:on
                    IE: Unknown: 0008534B593836333132
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000091f45971b7
                    Extra: Last beacon: 1732ms ago
          Cell 02 - Address: 00:1E:74:77:02:77
                    ESSID:"SKY00630"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=10/100  Signal level:-96 dBm  Noise level=-103 dBm
                    Encryption key:on
                    IE: Unknown: 0008534B593030363330
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000377841b97d3
                    Extra: Last beacon: 3548ms ago
          Cell 03 - Address: 00:1F:33:7F:D4:4E
                    ESSID:"SKY25265"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=76/100  Signal level:-55 dBm  Noise level=-104 dBm
                    Encryption key:on
                    IE: Unknown: 0008534B593235323635
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000148a87c609
                    Extra: Last beacon: 1740ms ago
          Cell 04 - Address: 00:23:48:60:EC:45
                    ESSID:"SKY60484"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/100  Signal level:-99 dBm  Noise level=-104 dBm
                    Encryption key:on
                    IE: Unknown: 0008534B593630343834
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000003b8119700a
                    Extra: Last beacon: 580ms ago
          Cell 05 - Address: 00:01:E3:EE:C4:04
                    ESSID:"OrangeEEC402"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=14/100  Signal level:-94 dBm  Noise level=-103 dBm
                    Encryption key:on
                    IE: Unknown: 000C4F72616E6765454543343032
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000018ecdeab0e
                    Extra: Last beacon: 828ms ago
          Cell 06 - Address: 00:24:2C:5F:3F:75
                    ESSID:"BTHomeHub2-PKMP"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/100  Signal level:-101 dBm  Noise level=-101 dBm
                    Encryption key:on
                    IE: Unknown: 000F4254486F6D65487562322D504B4D50
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081100000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000073d2c973b
                    Extra: Last beacon: 1312ms ago

success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
```

My make/model is a Packard Bell MX 66

---

### Post by sarfarazkazi on 2009-07-30
What's the amount of swap memory on your system?

---

### Post by MichealH on 2009-07-30
I have no swap doh!:rolleyes:


How do I make a swap volume without reinstalling Ubuntu 9.04

---

### Post by davidds on 2009-07-30
I guess you got lots of spare RAM or you do not know much about Linux. ;-)

---

### Post by MichealH on 2009-07-30
I have 1.5 GB of RAM I thought that was enough.

---

### Post by sarfarazkazi on 2009-07-30
Use Gparted to resize one of your existing partitons and free up some space for swap and then assign that space as swap partition.

---

### Post by davidds on 2009-07-30
More than enough. I have 1GB of RAM, but I do have a 2GB swap partition. Anyway, I think that the new idea of using a file for swapping is much better than the partition.

---

### Post by MichealH on 2009-07-30
I have downloaded and installed GParted and How do I access it from Ubuntu:confused:

---

### Post by sarfarazkazi on 2009-07-30
Have you installed it through Add/Remove Programs? Usually, it appears under Applications>System Tools or System>Administration menu.

---

### Post by MichealH on 2009-07-30
Thankyou I am adding it now I will tell u what happened

---

### Post by MichealH on 2009-07-30
THE PROBLEM IS NOT SOLVED I have 1.5GB and 20GB swap and It was struggling to wake up!!! HELP

[COLOR=Red]Edit- I did do a complete reinstall[/COLOR]

---

### Post by MichealH on 2009-07-30
Please can someone help as last time it nearly trashed my laptop :(

---

### Post by zzzBrett on 2009-07-30
> **MichealH said:**
> Please can someone help as last time it nearly trashed my laptop :(
I'm fairly new to ubuntu, but as far as I can tell, suspend / hibernation is quite flaky -- I still haven't gotten mine working.  But what I can tell you is a 20GB swap is very large.  With 1.5GB ram, you probably would need something like a 2 or 2.5GB swap (and I think that would be fairly large too).

Now as far as hibernation, have you tried searching google / these forums?  I found lots of tutorials (that didn't work for me) when I searched, but they seemed to be working for some.

Good Luck

---

### Post by danxx on 2009-07-30
perhaps this workaround will make the trick (at least it did for me),

sudo apt-get install hibernate

it is a little program, then in a terminal  digit

sudo hibernate -f -v0

if it works make a launcher with this command

gksu -u root "hibernate -f -v0"

---

### Post by MichealH on 2009-07-30
> **danxx said:**
> perhaps this workaround will make the trick (at least it did for me),

sudo apt-get install hibernate

it is a little program, then in a terminal  digit

sudo hibernate -f -v0

if it works make a launcher with this command

gksu -u root "hibernate -f -v0"
```
mike@mike-laptop:~$ sudo apt-get install hibernate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hibernate
mike@mike-laptop:~$ 

```

---

### Post by zzzBrett on 2009-07-30
> **MichealH said:**
> ```
mike@mike-laptop:~$ sudo apt-get install hibernate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hibernate
mike@mike-laptop:~$ 

```

Try this, then the install command.

```
sudo apt-get update
```

---

### Post by MichealH on 2009-07-30
> **zzzBrett said:**
> Try this, then the install command.

```
sudo apt-get update
```
  Trying it out now
[COLOR=Red][/COLOR]

---

### Post by hibliss on 2009-07-30
That means that you have update manager or synaptic open. Only one instance of Synaptic can be in use at a time.

You should be fine with 2-3gb swap, I recommend 2gb.

---

### Post by MichealH on 2009-07-30
> **danxx said:**
> perhaps this workaround will make the trick (at least it did for me),

sudo apt-get install hibernate

it is a little program, then in a terminal  digit

sudo hibernate -f -v0

if it works make a launcher with this command

gksu -u root "hibernate -f -v0"
Thanks for the help guys I can hibernate and resume :D.
Few Glitches:
says KUBUNTU instead of UBUNTU
when I resume i have no internet this is a major problem for me as i am constantly on and get  I have to restart which I really technically i need to  shut it down to it up and running :(

How do I mark this a SOLVED:confused::confused::confused:

---

### Post by stlsaint on 2009-07-30
> **MichealH said:**
> I have no swap doh!:rolleyes:


How do I make a swap volume without reinstalling Ubuntu 9.04


im amazed you were even able to install without setting a swap part...in ultimate you cant even move past the partition stage without setting up swap!

---

### Post by hibliss on 2009-07-30
You can run without swap. I did so on my Eee for months with no issues. It just takes away your ability to hibernate, you can still suspend to ram though.

---

### Post by danxx on 2009-07-30
perhaps you did not stop internet connection before hibernating, I think that is the cause of the problem when you resume, I am right?

---

