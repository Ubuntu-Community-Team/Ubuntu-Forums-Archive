---
title: "usbnet module fails to load"
date: 2011-12-29
forum: General Help
---

### Post by afrodeity on 2011-12-29
I usually use a reverse tethered usb connection to connect my android tablet.

Now suddenly the usbnet module fails to load

```

modprobe usbnet

```

but if I 

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:67:55:f4:0e  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:432931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:437563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155558746 (155.5 MB)  TX bytes:53938515 (53.9 MB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:385470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:385470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34325864 (34.3 MB)  TX bytes:34325864 (34.3 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

There module has been built, it just doesn't load

```

lsmod
Module                  Size  Used by
usbnet                 25214  0 
bridge                 79515  0 
stp                    12811  1 bridge
cdc_acm                22305  0 
nfsd                  253883  11 
lockd                  78804  1 nfsd
nfs_acl                12771  1 nfsd
auth_rpcgss            39545  1 nfsd
sunrpc                205330  17 nfsd,lockd,nfs_acl,auth_rpcgss
rfcomm                 38408  12 
bnep                   17923  2 
vboxnetadp             13328  0 
vboxnetflt             27840  0 
vboxdrv               230133  2 vboxnetadp,vboxnetflt
zram                   18007  2 
kvm_intel              55857  0 
kvm                   336964  1 kvm_intel
decnet                 66297  0 [permanent]
dm_crypt               22565  0 
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
nvidia              10390874  50 
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
btusb                  18160  2 
bluetooth             148839  23 rfcomm,bnep,btusb
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
parport_pc             32114  1 
it87                   29199  0 
hwmon_vid              12658  1 it87
coretemp               13188  0 
ppa                    17396  0 
lp                     17455  0 
parport                40930  4 ppdev,parport_pc,ppa,lp
raid10                 30270  0 
raid456                61518  0 
async_raid6_recov      12906  1 raid456
async_pq               12959  2 raid456,async_raid6_recov
raid6_pq               88205  2 async_raid6_recov,async_pq
async_xor              12738  3 raid456,async_raid6_recov,async_pq
xor                    21860  1 async_xor
async_memcpy           12481  2 raid456,async_raid6_recov
async_tx               13123  5 raid456,async_raid6_recov,async_pq,async_xor,async_memcpy
raid1                  26291  0 
raid0                  17067  0 
multipath              12977  0 
linear                 12792  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
uvesafb                28404  1 
r8169                  43104  0 

```

---

