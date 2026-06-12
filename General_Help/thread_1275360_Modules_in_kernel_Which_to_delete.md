---
title: "Modules in kernel: Which to delete?"
date: 2009-09-25
forum: General Help
---

### Post by argos3016 on 2009-09-25
I saw googling that ubuntu boots faster if you delete some modules in the kernel. I think it's true , because after installing a cpu frequencer it boots slow.
When I put lsmod i see this:

> Module                  Size  Used by
isofs                  39844  0 
udf                    87716  0 
crc_itu_t              10112  1 udf
cdc_ether              13184  0 
usbnet                 23944  1 cdc_ether
mii                    13312  1 usbnet
rt2860sta             523992  0 
usbhid                 42336  0 
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bnep                   20224  2 
ipt_MASQUERADE         10752  1 
iptable_nat            13700  1 
nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21388  4 iptable_nat,nf_nat
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
xt_state               10112  1 
nf_conntrack           72008  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             11136  2 
xt_tcpudp              11008  4 
iptable_filter         10752  1 
ip_tables              19600  2 iptable_nat,iptable_filter
x_tables               23044  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
bridge                 56212  0 
stp                    10500  1 bridge
input_polldev          11912  0 
joydev                 18368  0 
i2c_i801               17296  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435252  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
psmouse                61972  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_rawmidi            29696  1 snd_seq_midi
serio_raw              13444  0 
pcspkr                 10496  0 
btusb                  19608  2 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
video                  25872  0 
output                 11008  1 video
eeepc_laptop           18452  0 
atl1e                  40212  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

The question is: Which modules can I delete? (are some that aren't using now)
Sorry for my english

---

### Post by clonne4crw on 2009-09-25
Going against all of my philosophies concerning tinkering with things until they break, I wouldn't do this myself or advise it on the current working kernel. 

Instead I would suggest that you look into compiling your own custom kernel, with only the modules that you don't need.

It's been a while since I've needed to do this, so I'm not exactly the right person to ask about that...

---

### Post by argos3016 on 2009-09-26
Thanks. I didn't that you can make own. I'll googling to find how to compile custom kernel.

---

### Post by 3rdalbum on 2009-09-26
> **argos3016 said:**
> I saw googling that ubuntu boots faster if you delete some modules in the kernel. I think it's true , because after installing a cpu frequencer it boots slow.

The Ubuntu kernel comes with such a massive array of modules, that adding one more will not in itself cause any noticable slowdown.

However, a CPU frequency scaling module may cause the CPU to run at at a lower speed, in which case the solution is to remove the CPU frequency scaler, not to remove every other module BUT the scaler.

---

### Post by clonne4crw on 2009-09-26
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

If you're serious about trying this.

---

### Post by argos3016 on 2009-09-27
Thanks

---

