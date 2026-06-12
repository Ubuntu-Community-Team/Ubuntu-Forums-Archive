---
title: "Kernel Panic: HP-Dv3 &amp; Kubuntu 9.10x64"
date: 2010-01-21
forum: General Help
---

### Post by KyleFx on 2010-01-21
Hi Guys,

I'm trying to figure out the cause of intermittent kernel panics on my HP Dv3 laptop.  I'm running Kubuntu 9.10x64 kernel version 2.6.31-17-generic.  The symptoms include the classic caps-lock flashing, unable to do anything but hold in the power button.  There are times when caps-lock doesn't even flash, but the system is clearly frozen.  The magic sysrequest keys don't get me anywhere either.  

I'm not really sure how to diagnose what is causing the problem.  I've looked in /var/logs/messages, and the last thing to occur before panic happens usually has to do with my wireless card becoming ready.  So I kinda think maybe it's the wireless card.  I'm pretty sure I've heard of problems with Intel's Pro/Wireless 5100 AGN, but I thought those problems had been resolved in the more recent kernels.  My sound card and video card (nvidia) needed me to install drivers or modify configurations to get them working, so I suppose they are likely causes as well.

Any advice on the best way to diagnose the problem?  

Here are my PCI devices if that helps:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                           
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)                                                                        
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)                                                                          
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)                                                                          
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)                                                                         
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)                                                                               
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)                                                                                  
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)                                                                                  
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)                                                                                  
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)                                                                                  
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)                                                                          
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)                                                                          
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)                                                                          
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)                                                                         
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)                                                                                                  
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)                                                                                           
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)                                                                                      
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)                                                                                         
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)                                                                                    
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection                                                                         
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)   
```

And my currently loaded modules:
```
Module                  Size  Used by                                                                                                                                   
cryptd                  8008  0                                                                                                                                         
aes_x86_64              8992  1                                                                                                                                         
aes_generic            28480  1 aes_x86_64                                                                                                                              
bridge                 56384  0                                                                                                                                         
stp                     3012  1 bridge                                                                                                                                  
ppdev                   8232  0                                                                                                                                         
bnep                   15168  2                                                                                                                                         
snd_hda_codec_nvhdmi     6048  1                                                                                                                                        
snd_hda_codec_idt      72976  1                                                                                                                                         
snd_hda_intel          31880  2                                                                                                                                         
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel                                                                                    
snd_hwdep               9352  1 snd_hda_codec                                                                                                                           
snd_pcm_oss            44704  0                                                                                                                                         
snd_mixer_oss          18976  1 snd_pcm_oss                                                                                                                             
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss                                                                                                 
snd_seq_dummy           3460  0                                                                                                                                         
snd_seq_oss            33440  0                                                                                                                                         
arc4                    2144  2                                                                                                                                         
ecb                     3296  2                                                                                                                                         
snd_seq_midi            8192  0                                                                                                                                         
snd_rawmidi            27360  1 snd_seq_midi                                                                                                                            
joydev                 13088  0                                                                                                                                         
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi                                                                                                                
hp_accel               12480  0                                                                                                                                         
iptable_filter          3872  0
iwlagn                124832  0
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lis3lv02d               9312  1 hp_accel
ip_tables              21200  1 iptable_filter
snd_timer              26992  2 snd_pcm,snd_seq
iwlcore               133600  1 iwlagn
nvidia              10316904  39
x_tables               25832  1 ip_tables
input_polldev           4720  1 lis3lv02d
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              210008  2 iwlagn,iwlcore
btusb                  14260  2
led_class               5256  2 hp_accel,iwlcore
snd                    77096  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               65260  0
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
lirc_ene0100            9444  0
psmouse                57124  0
cfg80211              109144  3 iwlagn,iwlcore,mac80211
soundcore               9088  1 snd
v4l2_compat_ioctl32    13344  1 videodev
lirc_dev               13928  1 lirc_ene0100
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
serio_raw               6596  0
lp                     11908  0
parport                40528  2 ppdev,lp
usb_storage            66016  0
r8169                  38884  0
mii                     6368  1 r8169
intel_agp              32816  0
video                  23612  0
output                  3680  1 video

```

---

### Post by tamran on 2010-01-23
I'm using the following driver:
Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Nework Connection

I'm also on an HP Laptop using Kubuntu 9.10.  I saw many postings of this problem and I decided to try it with wireless disabled on a wired lan.  After a 1 week uptime I gave the wireless driver a try.  I lasted less than 5 minutes before the kernel panic.

There is definitely an issue with the driver for this wireless card.  I'm going to try the windows 64 bit drivers if I can find them and see if those work.  I'll post back here when I know or find a work around.

Good luck!

Tamran

---

### Post by d3v1150m471c on 2010-01-23
This will not keep your computer from having a kernel panic but it will help it handle them better. Use this command and add the following to the very bottom of your sysctl.conf file. [B]kernel.panic = 20
[/B]
```

gksudo gedit /etc/sysctl.conf

```It will look something like this.

```

#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to 
# readers that are allowed to ptrace() the process
# kernel.maps_protect = 1
kernel.panic = 20

```Save and reboot.

---

### Post by tamran on 2010-01-25
There is a possible fix here:

[http://baheyeldin.com/technology/linux/intel-wireless-wifi-link-5100-iwlagn-kubuntu-karmic-koala-910.html](http://baheyeldin.com/technology/linux/intel-wireless-wifi-link-5100-iwlagn-kubuntu-karmic-koala-910.html)

I'm skeptical to try this yet ... somebody else must have tried this?  I wonder how different this is then installing the backports modules?  I tried the backport thing and it only reduced the frequency of the lockups.

It seems these "Shiloh" chipsets have been causing a lot of people a lot of problems for more than a year now (even as far back as 8.10 Ubuntu).  I'm noticing a pattern of people trying to use wireless-N and WPA.

Any one else want to see if this fixes their problem?

The truly sad part of all this is that it's an Intel wireless card, and Intel is supposed to be all pro-Linux with their stuff.

---

### Post by tamran on 2010-01-26
OK, I think I found a simple workaround (until this is officially fixed).  I read a bunch of posts in other forums where people only ran into this issue after connecting to a WPA/WPA2 network and wireless-N.  All instances were with 2.6.28 and above kernels.

I set up my modem for WEP protocol, and have been running fine for almost two full days of heavy internet use.

Given this, I have a hunch the problem "may" be in the driver code for WPA.  If anyone else has this problem and can confirm this work-around actually provides stability for the same network setup, that would be fantastic.

I'll try to report back when I know more.

Tamran

---

