---
title: "HP IR Receiver 5188-1667/harmony one and lirc"
date: 2011-11-23
forum: General Help
---

### Post by brodos1 on 2011-11-23
Hi
I am trying to configure my HP IR Receiver 5188-1667 with harmony one and lirc.
I have read a lot of threads, but cant get it to work.
if someone have the config files for this configuration (hardware.conf and lircd.conf) a copy would be very appriciated!!
I have my harmony one set up as a MCE profile and I can send commands to the reciver (tested with irw) and all commands are correct. the problem is that XBMC does not repond to the remote.

lsmod
Module Size Used by
parport_pc 32114 0
ppdev 12849 0
vesafb 13489 1
nvidia 10390874 33
bnep 17923 2
rfcomm 38408 0
bluetooth 148839 10 bnep,rfcomm
nfs 297750 3
lockd 78804 1 nfs
fscache 50674 1 nfs
auth_rpcgss 39545 1 nfs
nfs_acl 12771 1 nfs
sunrpc 205330 20 nfs,lockd,auth_rpcgss,nfs_acl
snd_hda_codec_hdmi 31426 4
joydev 17393 0
binfmt_misc 17292 1
ir_lirc_codec 12770 0
arc4 12473 2
lirc_dev 18700 1 ir_lirc_codec
usbhid 41905 0
hid 77367 1 usbhid
ir_sony_decoder 12493 0
sparse_keymap 13658 0
snd_hda_codec_idt 60049 1
ir_jvc_decoder 12490 0
ir_rc6_decoder 12490 0
ir_rc5_decoder 12490 0
snd_hda_intel 28358 3
snd_hda_codec 91754 3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
rc_rc6_mce 12454 0
snd_hwdep 13276 1 snd_hda_codec
ir_nec_decoder 12490 0
mceusb 17602 0
snd_pcm 80468 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rc_core 25797 9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc 6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder ,mceusb
snd_seq_midi 13132 0
rtl8192ce 75448 0
rtl8192c_common 69519 1 rtl8192ce
rtlwifi 95614 1 rtl8192ce
snd_rawmidi 25241 1 snd_seq_midi
psmouse 63474 0
mac80211 393459 3 rtl8192ce,rtl8192c_common,rtlwifi
wmi 18744 0
serio_raw 12990 0
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event
cfg80211 172392 2 rtlwifi,mac80211
snd_timer 28932 2 snd_pcm,snd_seq
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
snd 55902 16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel ,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_s eq,snd_timer,snd_seq_device
video 18908 0
jmb38x_ms 17406 0
memstick 15857 1 jmb38x_ms
soundcore 12600 1 snd
snd_page_alloc 14108 2 snd_hda_intel,snd_pcm
lp 17455 0
parport 40930 3 parport_pc,ppdev,lp
ahci 21634 2
libahci 25761 1 ahci
jme 40330 0
sdhci_pci 13658 0
sdhci 27360 1 sdhci_pci


lsusb
Bus 003 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver


part of hardware.conf:

#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""



Thanks for all help
torleif is online now Add to torleif's Reputation Report Post Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
Reply

---

### Post by brodos1 on 2011-11-24
solved :grin:

Thanks to this thread: [http://forum.xbmc.org/showthread.php?t=45972](http://forum.xbmc.org/showthread.php?t=45972)

The problem was lircmap.xml and keymap.xml

---

