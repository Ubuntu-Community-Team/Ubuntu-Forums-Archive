---
title: "Ubuntu is running in low-graphics mode with garbage on screen"
date: 2012-02-15
forum: General Help
---

### Post by tomhand on 2012-02-15
I have a media box that has been running strong for a year.  However, when I rebooted this morning the screen now shows:

```
Ubuntu is running in low-graphics mode.  
(EE) NVIDIA(0): No display devices found for this X screen.
(EE) Screen(s) found, but none have a usable configuration.
```
(Please see attachment - note garbage at top, screen not centered and screen wraps oddly [moving mouse left from "ubuntu warning box" wraps around to right side of the screen])

The box has an intel d525 chip with the ion graphics (this seemed to cause some issues when i first set up the box, but it has been running fine since).

I've been hunting around for possible solutions. The most likely fix I found was to purge and re-install the nvidia-current drivers.  Alas, this did nothing.

Hardware has not changed.  Monitor has not changed.  My /etc/X11/xorg.conf file does not appear to have changed.  I am on ubuntu 10.4.

Any ideas?  Thank you.

---

### Post by tomhand on 2012-02-15
This is from /var/log/Xorg.0.log and may provide a bit more information:


```
(**) Feb 15 11:05:43 NVIDIA(0): Enabling 2D acceleration
(II) Feb 15 11:05:44 NVIDIA(0): NVIDIA GPU ION (GT218) at PCI:1:0:0 (GPU-0)
(--) Feb 15 11:05:44 NVIDIA(0): Memory: 524288 kBytes
(--) Feb 15 11:05:44 NVIDIA(0): VideoBIOS: 70.18.5d.00.17
(II) Feb 15 11:05:44 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Feb 15 11:05:44 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Feb 15 11:05:44 NVIDIA(0): Connected display device(s) on ION at PCI:1:0:0
(--) Feb 15 11:05:44 NVIDIA(0):     none
(EE) Feb 15 11:05:44 NVIDIA(0): No display devices found for this X screen.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by imachavel on 2012-02-15
no device attached? Weird. That sounds like no monitor would be attached, but you found that in your logs? You got to the logs, so the monitor resolution is working, the display driver is installed. I wonder wtf is going on, do you have any more information to this problem?

ok I read your post a little better, it would seem the problem is probably a driver. Did you add a graphics card into a pci-e slot recently? Are you using on board display? Some more information might be helpful. What is the model of your computer? If you added a graphics card then you might need to go to the manufacturer of that graphic cards web site, and update a driver. Otherwise go to manufacturer of your computer, then look for a display driver to update. With windows automatic updates usually fixes the problem. But linux updates all the drivers when you do an update, if linux as an OS is missing the compiled drivers for your hardware, your gpu, on board or not, then you need to download drivers, and see if in system settings in additional drivers if there is a restricted driver that linux will allow to be installed. 

Do me this favor, open the terminal: ctrl+alt+t and then type this and press enter:

sudo apt-get update

see what happens, when you are done with that, type this:

lsmod, then please copy and paste the output into this thread, here is my output:

lsmod
Module                  Size  Used by
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31444  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55577  2 vfat,msdos
jfs                   175084  0 
xfs                   746832  0 
reiserfs              230932  0 
ppp_async              17307  0 
crc_ccitt              12595  1 ppp_async
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13489  1 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  19 
xt_addrtype            12596  4 
snd_hda_codec_hdmi     31426  1 
xt_state               12514  14 
binfmt_misc            17292  1 
snd_intel8x0           33318  2 
snd_hda_intel          24262  1 
snd_hda_codec          91859  2 snd_hda_codec_hdmi,snd_hda_intel
snd_ac97_codec        106082  1 snd_intel8x0
snd_usb_audio         100930  1 
ac97_bus               12642  1 snd_ac97_codec
ip6table_filter        12711  1 
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_pcm                80435  6 snd_hda_codec_hdmi,snd_intel8x0,snd_hda_intel,snd_hda_codec,snd_ac97_codec,snd_usb_audio
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
gspca_sonixj           32391  0 
gspca_main             27610  1 gspca_sonixj
videodev               85626  1 gspca_main
r8712u                163310  0 
snd_seq_midi           13132  0 
nf_conntrack_netbios_ns    12585  0 
joydev                 17393  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
snd_seq_midi_event     14475  1 snd_seq_midi
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd                    55902  21 snd_hda_codec_hdmi,snd_intel8x0,snd_hda_intel,snd_hda_codec,snd_ac97_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
lp                     17455  0 
fglrx                2756852  131 
soundcore              12600  1 snd
snd_page_alloc         14115  3 snd_intel8x0,snd_hda_intel,snd_pcm
ppdev                  12849  0 
dcdbas                 14098  0 
parport_pc             32114  1 
psmouse                73673  0 
serio_raw              12990  0 
parport                40930  3 lp,ppdev,parport_pc
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  1 
uas                    17699  0 
e100                   36289  0 
floppy                 60310  0 


that might help a bit, in the future please give more info on the make and model of your computer, the log is very nice though good job posting that

---

### Post by tomhand on 2012-02-15
The computer is a home built HTPC.  Really the only thing in it is an intel d525 board and a few hard drives.  So no new graphics card, just the one built into the MB.

The box boots up to the screen shown in the attachment above (the box is connected to the TV via HDMI).  I leave it at that screen and then SSH into the box to attempt to diagnose the problem.

I will look into trying out different driver versions.  In the mean time, this is the result of sudo apt-get update:

```
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Ign http://ppa.launchpad.net/jcfp/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://ppa.launchpad.net lucid Release
Hit http://ppa.launchpad.net lucid Release
Hit http://ppa.launchpad.net lucid Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
```

This is the result of lsmod:

```
Module                  Size  Used by
l2cap                  30624  2
bluetooth              49892  1 l2cap
binfmt_misc             6587  1
ppdev                   5259  0
snd_hda_codec_nvhdmi    12658  1
snd_hda_codec_realtek   216061  1
ipt_REJECT              1928  1
xt_comment               720  1
ipt_LOG                 4542  5
xt_limit                1382  7
xt_tcpudp               2011  19
ipt_addrtype            1631  4
xt_state                1098  7
ip6table_filter         2343  1
ip6_tables             11227  1 ip6table_filter
snd_hda_intel          20767  0
snd_pcm_oss            34539  0
snd_hda_codec          86936  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_mixer_oss          13897  1 snd_pcm_oss
snd_hwdep               5604  1 snd_hda_codec
snd_pcm                71550  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
nf_nat_irc              1124  0
snd_seq_dummy           1434  0
snd_seq_oss            27242  0
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0
snd_seq_midi            4557  0
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
snd_rawmidi            19077  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nf_conntrack_ipv4      10672  9 nf_nat
coretemp                4417  0
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
fbcon                  35102  72
snd_seq                47530  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack_ftp        5381  1 nf_nat_ftp
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_timer              18646  2 snd_pcm,snd_seq
nf_conntrack           61615  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
bitblit                 4707  1 fbcon
iptable_filter          2271  1
joydev                  8708  0
snd_seq_device          5988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uinput                  6312  1
ip_tables               9991  1 iptable_filter
hid_microsoft           2647  0
softcursor              1189  1 bitblit
psmouse                63245  0
nvidia              10934101  0
snd                    56303  15 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_pcm_oss,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 36110  0
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24119  0
vga16fb                11385  1
serio_raw               3978  0
x_tables               14299  9 ipt_REJECT,xt_comment,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
agpgart                31724  2 nvidia,intel_agp
hid                    67032  2 hid_microsoft,usbhid
vgastate                8961  1 vga16fb
lp                      7060  0
parport                32635  2 ppdev,lp
r8169                  34076  0
pata_jmicron            1843  0
ahci                   32200  1
mii                     4381  1 r8169

```

---

