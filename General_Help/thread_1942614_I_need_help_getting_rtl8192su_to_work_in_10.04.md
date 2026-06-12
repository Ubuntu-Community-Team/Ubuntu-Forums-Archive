---
title: "I need help getting rtl8192su to work in 10.04"
date: 2012-03-17
forum: General Help
---

### Post by mejbr2003 on 2012-03-17
I'm trying to make my usb wireless adapter, that works fine in xp, to also work in lucid. i'm dual booting obviously.

I've tried the ndisgtk thing.

the network manager is detectiing the wireless network, says it is available and shows its signal strength...but won't let me connect

I'm not to linux savvy, so I really need help.

i read in some forum that this driver might not work in 10.04...i hope thats not true
thanks for any and all help

---

### Post by mejbr2003 on 2012-03-17
here are some outputs that I hope, help


j@mydamncomputer:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux mydamncomputer 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 i686
GNU/Linux


j@mydamncomputer:~$ lspci -nnk | grep -iA2 net
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM)
Ethernet Controller [8086:1064] (rev 03)
Kernel driver in use: e100
Kernel modules: e100


j@mydamncomputer:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan2 802.11b/g/n ... ESSID:"Kiyoshi"
Mode:Managed Frequency=2.437 GHz Access Point: 00:21:29:67:4C:5A
Bit Rate=130 Mb/s
Retry min limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=0/100 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0



j@mydamncomputer:~$ rfkill list all (produced no output)


j@mydamncomputer:~$ lsmod
Module Size Used by
nls_iso8859_1 3249 1
nls_cp437 4919 1
vfat 8933 1
fat 47767 1 vfat
binfmt_misc 6587 1
ppdev 5259 0
snd_hda_codec_realtek 203472 1
snd_hda_intel 22069 2
snd_hda_codec 74297 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 5412 1 snd_hda_codec
snd_pcm_oss 35308 0
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70694 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1338 0
snd_seq_oss 26722 0
snd_seq_midi 4557 0
fbcon 35102 71
snd_rawmidi 19056 1 snd_seq_midi
tileblit 1999 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
vga16fb 11385 0
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
vgastate 8961 1 vga16fb
snd_timer 19130 2 snd_pcm,snd_seq
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
i915 289683 3
drm_kms_helper 29329 1 i915
snd 54244 16
snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec, snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pc
m,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_se q_device
drm 163779 4 i915,drm_kms_helper
i2c_algo_bit 5028 1 i915
psmouse 63677 0
soundcore 6620 1 snd
r8192s_usb 346876 0
serio_raw 3978 0
joydev 8740 0
video 17375 1 i915
intel_agp 24375 2 i915
lp 7028 0
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm
output 1871 1 video
agpgart 31724 2 drm,intel_agp
parport 32635 2 ppdev,lp
ohci1394 26950 0
usbhid 36110 0
usb_storage 40033 1
e100 28211 0
mii 4381 1 e100
ieee1394 81181 1 ohci1394
hid 67288 1 usbhid

---

### Post by raja.genupula on 2012-03-17
i think you should see this once 
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by kurt18947 on 2012-03-18
You shouldn't need NDISwrapper.  There's a known bug in 10.04 & 10.10, you can look at the output of dmesg and see if your output matches the bug. The fix is pretty simple.  Here's the bug & fix:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

In essence, you download  file rtl8192sfw.bin and copy it to /lib/firmware/RTL8192SU then restart.  You'll probably want to remove NDISwrapper, it may conflict.  There is another person having trouble with an RTL-8192SU adapter (Dlink DWA-131).  I have 2 RTL-8192SU adapters (same Dlink DWA-131 & TrendNet TEW-649UB) and they are both plug -n- play for me in 11.04 and newer.  Some difference in USB ports? I don't know why.

---

### Post by kurt18947 on 2012-03-18
duplicate deleted.

---

### Post by mejbr2003 on 2012-03-18
it worked
thank you so much!!

---

