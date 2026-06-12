---
title: "wifi help! acer aspire one netbook"
date: 2011-12-26
forum: General Help
---

### Post by benjiblood on 2011-12-26
i have an acer aspire one netbook and the first thing i did was obtain ubuntu. this is the first time messing with linux as i always wanted to but never had a fresh platform to do so.
here is my problem:
i dual booted? ubuntu with windows xp. in xp wifi works like a charm. but not in ubuntu the physical switch dosent even light up in ubuntu. the "enable wireless" in the top bar is there but as soon as check it it immediately closes again. i tried doing my own lil investigation in terminal trying other peoples ideas but its not working.

let me know what commands to run and id be happy to get em to you. im wired right now. 

any help would be greatly appreciated.

---

### Post by wildmanne39 on 2011-12-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by benjiblood on 2011-12-26
sorry if i mess up the terminal pasting

#benji@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux


#benji@ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022c]
    Kernel driver in use: ATL1E
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e00d]
    Kernel driver in use: ath5k


#benji@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


#benji@ubuntu:~$ rfkill list all
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


#benji@ubuntu:~$ lsmod
Module                  Size  Used by
ath5k                 145100  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
i915                  505108  3 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
drm_kms_helper         32889  1 i915
snd_timer              28932  2 snd_pcm,snd_seq
ath                    19387  1 ath5k
serio_raw              12990  0 
drm                   192226  4 i915,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              272785  1 ath5k
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  3 ath5k,ath,mac80211
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
wmi                    18744  1 acer_wmi
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
ahci                   21634  1 
libahci                25727  1 ahci
atl1e                  32809  0 
benji@ubuntu:~$

---

### Post by wildmanne39 on 2011-12-26
Hi, it shows a hard block and a softblock please try this for the softblock:
```
sudo su
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
```
see if it comes on. 

For the hardblock do this please:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit.
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

---

### Post by benjiblood on 2011-12-26
> **wildmanne39 said:**
> Hi, it shows a hard block and a softblock please try this for the softblock:
```
sudo su
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
```see if it comes on. 

For the hardblock do this please:
```
gksudo gedit /etc/rc.local
```Add your three lines above exit.
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

for the first command is that two seperate commands or one? idk how to enter that into terminal.

---

### Post by wildmanne39 on 2011-12-26
Hi, it is one command just copy and paste just like it is, then you will be asked for your user password as you type it you will not see it in the terminal so when you are done entering it, hit enter and the command will be ran, again it will not show any output unless the command fails for some reason.
Thanks

---

### Post by benjiblood on 2011-12-26
> **wildmanne39 said:**
> Hi, it is one command just copy and paste just like it is, then you will be asked for your user password as you type it you will not see it in the terminal so when you are done entering it, hit enter and the command will be ran, again it will not show any output unless the command fails for some reason.
Thanks

it opens root correct? i entered the second command and a different screen popped up. what do i do with it?

---

### Post by wildmanne39 on 2011-12-26
Hi, yes the second command will open a window type in your password then a file will open and copy and paste the 3 lines just like it says in that post and save,exit and reboot.
Thanks

---

### Post by benjiblood on 2011-12-26
[LEFT]i have not a clue what i did nor did i understand what those commands did but it worked! thank you! 

now i juss have to figure out how to get adobe flash player to work... :P
[/LEFT]

---

### Post by wildmanne39 on 2011-12-26
Hi, that is okay sometimes it is enough just to know it works.

For flash you can open firefox and click on tools, addons, the window that opens will have a small box for searching for plugins type flashaid and install it and follow the directions it is real easy to set up, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

