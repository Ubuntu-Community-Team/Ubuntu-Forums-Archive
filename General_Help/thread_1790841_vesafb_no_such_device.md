---
title: "vesafb: no such device"
date: 2011-06-25
forum: General Help
---

### Post by 11ghjones on 2011-06-25
In the process of trying to use plymouth on startup as opposed to the general text startup, I've done several things with grub's configuration to set the proper resolution, etc, with uvesafb.  The problem I run into now is on startup, I get a very brief message that reads

 FATAL:Error processing /lib/<path to vesafb>/vesafb.ko No such device.

(note, I'm guessing at this.  I'm trying to read this over 10 or so boots.  The message only displays for a half second or so.)

The computer continues then to boot with the text start up, showing Ubuntu 11.04 and a few moving dots, which is then interrupted by all sorts of boot messages.  Everything boots fine, but it's an aesthetic problem I'd like to fix.  I know plymouth is working, as on shutdown the custom theme I've chosen is working.  I simply am looking for a way to get the startup splash screen to show.  I'm using a Nvidia GTX460 SE card, with Nvidia's drivers from their website.  I encountered the same problems when using Ubuntu's package of official Nvidia drivers.

Any ideas?

---

### Post by 11ghjones on 2011-07-09
bump

---

### Post by wildmanne39 on 2011-07-09
> **11ghjones said:**
> In the process of trying to use plymouth on startup as opposed to the general text startup, I've done several things with grub's configuration to set the proper resolution, etc, with uvesafb.  The problem I run into now is on startup, I get a very brief message that reads

 FATAL:Error processing /lib/<path to vesafb>/vesafb.ko No such device.

(note, I'm guessing at this.  I'm trying to read this over 10 or so boots.  The message only displays for a half second or so.)

The computer continues then to boot with the text start up, showing Ubuntu 11.04 and a few moving dots, which is then interrupted by all sorts of boot messages.  Everything boots fine, but it's an aesthetic problem I'd like to fix.  I know plymouth is working, as on shutdown the custom theme I've chosen is working.  I simply am looking for a way to get the startup splash screen to show.  I'm using a Nvidia GTX460 SE card, with Nvidia's drivers from their website.  I encountered the same problems when using Ubuntu's package of official Nvidia drivers.

Any ideas?Hi, open sysnaptic and see if vesa is installed it is a generic video card driver, if it is installed you might right click on it and choose to remove completely then reinstall it.

---

### Post by 11ghjones on 2011-07-09
OK, tried that to no avail.  My guess is that the root filesystem isn't mounted yet when it comes time to load the vesafb module.  Is there any way to put it into the initramfs?

---

### Post by wildmanne39 on 2011-07-09
> **11ghjones said:**
> OK, tried that to no avail.  My guess is that the root filesystem isn't mounted yet when it comes time to load the vesafb module.  Is there any way to put it into the initramfs?Hi, run this command in a terminal
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by 11ghjones on 2011-07-09
Modules currently in kernel:

```
aesni_intel            55161  2 
cryptd                 20510  1 aesni_intel
aes_x86_64             17208  1 aesni_intel
aes_generic            38279  2 aesni_intel,aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  4 
nvidia              11989520  50 
snd_hda_codec_realtek   336693  1 
ipt_REJECT             12576  1 
xt_comment             12504  4 
ipt_LOG                17016  5 
xt_multiport           12597  2 
xt_limit               12711  7 
xt_tcpudp              12603  10 
ipt_addrtype           12599  4 
xt_state               12578  7 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         112426  1 
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
rt2860sta             543010  0 
snd_hwdep              13604  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_seq_midi           13324  0 
arc4                   12529  2 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
rt2800pci              18535  0 
rt2800lib              45181  1 rt2800pci
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt              12667  2 rt2860sta,rt2800lib
ip6table_filter        12815  1 
rt2x00pci              14322  1 rt2800pci
snd                    67382  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
ip6_tables             27845  1 ip6table_filter
nf_nat_irc             12643  0 
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12649  0 
nf_nat                 25736  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19640  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13359  1 nf_nat_ftp
uvcvideo               72195  0 
nf_conntrack           81956  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
cfg80211              178528  2 rt2x00lib,mac80211
iptable_filter         12810  1 
videodev               82052  1 uvcvideo
ip_tables              27456  1 iptable_filter
shpchp                 37297  0 
soundcore              12680  1 snd
v4l2_compat_ioctl32    17078  1 videodev
x_tables               29581  12 ipt_REJECT,xt_comment,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
eeprom_93cx6           12725  1 rt2800pci
lp                     17825  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46458  3 parport_pc,ppdev,lp
uvesafb                29163  1 
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  1 
uas                    17996  0 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  48022  0 

```

---

### Post by 11ghjones on 2011-07-09
My only reason for using vesa is just temporarily during the boot process, to display the splash screen.  Not for normal use.

---

### Post by wildmanne39 on 2011-07-09
> **11ghjones said:**
> My only reason for using vesa is just temporarily during the boot process, to display the splash screen.  Not for normal use.
Hi, yes I understood that from the start. I am including a screenshot, do you have the one installed that is high lighted in blue? Looking at your lsmod output I see a uvesafb but it is different from mine, mine is just veasfb.

---

### Post by 11ghjones on 2011-07-09
Yes, I have GRUB version 2 installed.  And I've messed with the GRUB settings slightly to load uvesafb as suggested in this guide: 

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by 11ghjones on 2011-07-09
Well, I've managed to fix it.  Apparently the line blacklisting vesafb was for some reason commented, causing it to load at startup when it shouldn't.  Uncommented it, ran a depmod, updated the initramfs, and problem solved.

---

### Post by wildmanne39 on 2011-07-09
> **11ghjones said:**
> Well, I've managed to fix it.  Apparently the line blacklisting vesafb was for some reason commented, causing it to load at startup when it shouldn't.  Uncommented it, ran a depmod, updated the initramfs, and problem solved.Hi, thats good I thought it probably was  a problem in the modules loading that is where I was headed.

---

