---
title: "Please help with Graphics Problem"
date: 2009-07-22
forum: General Help
---

### Post by cottfcfan on 2009-07-22
This is my last Jaunty issue and I need help.
Ive posted this in other threads but can`t seem to get anywhere.
I`m running Jaunty with an ATI radeon HD2400 Pro Graphics card.
 After install i`m prompted to install Propriety FGLRX Driver which I do.
Everything fine. Responsive Desktop, Full screen streaming fine etc etc..
 But once I reboot i lose system responsiveness, get choppy video, high CPU usage and so on.
 So I unintalled fglrx, and installed from ATI website. Same result.
Perfect graphics until I reboot.
 Everytime i install FGLRX, its fine till i reboot.
 Either somethings not reloading at reboot, or I`m doing something wrong.
Please can someone help!!

ps If i suspend its fine, only when I reboot.

---

### Post by prshah on 2009-07-22
> **cottfcfan said:**
> 
Perfect graphics until I reboot.
 Everytime i install FGLRX, its fine till i reboot.
 Either somethings not reloading at reboot,

Can you post a list of modules in use, both after an install (when everything works fine) and after a reboot (when problems start). You can get a list of modules in use with the command```
lsmod
```  in a terminal (Applications-Accessories-Terminal).

Can you also post the output for the following commands (before problem and after problem)```
cat /var/log/Xorg.0.log | grep -i direct
glxinfo | grep -i direct
```

---

### Post by cottfcfan on 2009-07-22
Thanx for your reply prshah.

here is lsmod when working fine:

lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
ipt_REJECT             11136  1 
ipt_LOG                13700  1 
xt_limit               10116  2 
xt_tcpudp              11008  7 
xt_state               10112  5 
ipt_addrtype           10496  4 
ip6table_filter        10624  1 
ip6_tables             20880  1 ip6table_filter
nf_nat_irc             10240  0 
nf_conntrack_irc       13220  1 nf_nat_irc
nf_nat_ftp             10752  0 
nf_nat                 25876  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      21388  7 nf_nat
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
nf_conntrack_ftp       15652  1 nf_nat_ftp
nf_conntrack           72008  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         10752  1 
ip_tables              19472  1 iptable_filter
x_tables               23044  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
rt73usb                33412  0 
crc_itu_t              10112  1 rt73usb
snd_hda_intel         434100  3 
k8temp                 12416  0 
fglrx                2131680  27 
rt2500usb              27904  0 
rt2x00usb              18688  2 rt73usb,rt2500usb
rt2x00lib              37888  3 rt73usb,rt2500usb,rt2x00usb
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
agpgart                42696  1 fglrx
usb_storage            99520  0 
i2c_nforce2            14980  0 
led_class              12036  1 rt2x00lib
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217464  2 rt2x00usb,rt2x00lib
cfg80211               38288  2 rt2x00lib,mac80211
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
psmouse                61972  0 
serio_raw              13316  0 
usbhid                 42336  0 
pcspkr                 10496  0 
dcdbas                 15264  0 
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


Here is lsmod when not working properly:

 lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
ipt_REJECT             11136  1 
ipt_LOG                13700  1 
xt_limit               10116  2 
xt_tcpudp              11008  7 
xt_state               10112  5 
ipt_addrtype           10496  4 
ip6table_filter        10624  1 
ip6_tables             20880  1 ip6table_filter
nf_nat_irc             10240  0 
nf_conntrack_irc       13220  1 nf_nat_irc
nf_nat_ftp             10752  0 
nf_nat                 25876  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      21388  7 nf_nat
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
nf_conntrack_ftp       15652  1 nf_nat_ftp
nf_conntrack           72008  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         10752  1 
ip_tables              19472  1 iptable_filter
x_tables               23044  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
rt73usb                33412  0 
crc_itu_t              10112  1 rt73usb
snd_hda_intel         434100  3 
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
rt2500usb              27904  0 
rt2x00usb              18688  2 rt73usb,rt2500usb
rt2x00lib              37888  3 rt73usb,rt2500usb,rt2x00usb
psmouse                61972  0 
usb_storage            99520  0 
led_class              12036  1 rt2x00lib
serio_raw              13316  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
mac80211              217464  2 rt2x00usb,rt2x00lib
cfg80211               38288  2 rt2x00lib,mac80211
usbhid                 42336  0 
fglrx                2131680  27 
agpgart                42696  1 fglrx
k8temp                 12416  0 
pcspkr                 10496  0 
dcdbas                 15264  0 
i2c_nforce2            14980  0 
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

I have noticed that the fglrx has moved.
Don`t know if this is making the difference?

The second command gave me  - directory does not exist.
The third command - direct rendering = yes.

Hope you can help.

---

### Post by cottfcfan on 2009-07-22
Sorry havent copied and pasted very well.


Wouldnt upload as attachments either.

Just keep getting invalid file when trying to upload as an attachment.

---

### Post by cottfcfan on 2009-07-22
Just a bit more info.
Ive now realised that if I modify the xorg.conf file in any way and then run the commands:

sudo aticonfig --initial -f

followed by:

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

then reboot, no problems.
Its as if it needs configuring for every boot.
Don`t know if this helps with a solution, but i`m out of my depth on this one.

---

### Post by cottfcfan on 2009-07-23
Ive realised ive been wasting my time, and everyone elses.
 This isnt an ubuntu problem, kernel problem or anything else.
Its an Adobe Flash problem.
 Sometimes it works, sometimes it just maxes your CPU, and causes problems, especially in Fullscreen.

See this thread:

[http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

Hope they resolve it soon.:

---

