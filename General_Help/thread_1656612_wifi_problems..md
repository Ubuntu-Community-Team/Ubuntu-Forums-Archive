---
title: "wifi problems."
date: 2010-12-31
forum: General Help
---

### Post by ruben_linux on 2010-12-31
hey guys,

I have a problem with NetworkManager , wpa_supplicant.

I have ubuntu 10.04 LTS, 2.6.32-24-generic in a laptop HP Pavilion dv6 2145es. 64 bit, AMD Turion(tm) II Dual-Core Mobile M520, network: AR9285 Wireless Network Adapter (PCI-Express), memory 6GB.

And my syslog saidme: 

> Dec 30 20:50:03 CoYoTe NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto C54BRS4A' requires no security.  No secrets needed.
Dec 30 20:50:03 CoYoTe NetworkManager: <info>  Config: added 'ssid' value 'C54BRS4A'
Dec 30 20:50:03 CoYoTe NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec 30 20:50:03 CoYoTe NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Dec 30 20:50:03 CoYoTe NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 30 20:50:03 CoYoTe NetworkManager: <info>  Config: set interface ap_scan to 1
Dec 30 20:50:03 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 30 20:50:10 CoYoTe wpa_supplicant[1171]: Trying to associate with 00:80:5a:5c:cf:4c (SSID='C54BRS4A' freq=2437 MHz)
Dec 30 20:50:10 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 30 20:50:10 CoYoTe wpa_supplicant[1171]: Association request to the driver failed
Dec 30 20:50:10 CoYoTe kernel: [  318.991659] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 30 20:50:10 CoYoTe kernel: [  319.193794] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 30 20:50:10 CoYoTe kernel: [  319.390209] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 30 20:50:11 CoYoTe kernel: [  319.590190] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out
Dec 30 20:50:15 CoYoTe wpa_supplicant[1171]: Authentication with 00:80:5a:5c:cf:4c timed out.
Dec 30 20:50:15 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 30 20:50:15 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 30 20:50:16 CoYoTe wpa_supplicant[1171]: Trying to associate with 00:80:5a:5c:cf:4c (SSID='C54BRS4A' freq=2437 MHz)
Dec 30 20:50:16 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 30 20:50:16 CoYoTe wpa_supplicant[1171]: Association request to the driver failed
Dec 30 20:50:16 CoYoTe kernel: [  325.140704] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 30 20:50:16 CoYoTe kernel: [  325.340175] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 30 20:50:17 CoYoTe kernel: [  325.542695] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 30 20:50:17 CoYoTe kernel: [  325.740253] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out
Dec 30 20:50:21 CoYoTe wpa_supplicant[1171]: Authentication with 00:80:5a:5c:cf:4c timed out.
Dec 30 20:50:21 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 30 20:50:21 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 30 20:50:22 CoYoTe wpa_supplicant[1171]: Trying to associate with 00:80:5a:5c:cf:4c (SSID='C54BRS4A' freq=2437 MHz)
Dec 30 20:50:22 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 30 20:50:22 CoYoTe wpa_supplicant[1171]: Association request to the driver failed
Dec 30 20:50:22 CoYoTe kernel: [  331.251403] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 30 20:50:23 CoYoTe kernel: [  331.452569] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 30 20:50:23 CoYoTe kernel: [  331.652562] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 30 20:50:23 CoYoTe kernel: [  331.852689] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out
Dec 30 20:50:27 CoYoTe wpa_supplicant[1171]: Authentication with 00:80:5a:5c:cf:4c timed out.
Dec 30 20:50:27 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 30 20:50:27 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 30 20:50:28 CoYoTe wpa_supplicant[1171]: Trying to associate with 00:80:5a:5c:cf:4c (SSID='C54BRS4A' freq=2437 MHz)
Dec 30 20:50:28 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 30 20:50:28 CoYoTe wpa_supplicant[1171]: Association request to the driver failed
Dec 30 20:50:28 CoYoTe kernel: [  337.372563] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 30 20:50:29 CoYoTe kernel: [  337.573002] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 30 20:50:29 CoYoTe kernel: [  337.772692] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 30 20:50:29 CoYoTe kernel: [  337.970185] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out
Dec 30 20:50:31 CoYoTe NetworkManager: <info>  wlan0: link timed out.
Dec 30 20:50:33 CoYoTe wpa_supplicant[1171]: Authentication with 00:80:5a:5c:cf:4c timed out.
Dec 30 20:50:33 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 30 20:50:33 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 30 20:50:35 CoYoTe wpa_supplicant[1171]: Trying to associate with 00:80:5a:5c:cf:4c (SSID='C54BRS4A' freq=2437 MHz)
Dec 30 20:50:35 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 30 20:50:35 CoYoTe wpa_supplicant[1171]: Association request to the driver failed
Dec 30 20:50:35 CoYoTe kernel: [  343.471607] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 30 20:50:35 CoYoTe kernel: [  343.672696] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 30 20:50:35 CoYoTe kernel: [  343.870109] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 30 20:50:35 CoYoTe kernel: [  344.070274] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out
Elsewhere of the log, saidme:

[http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889) 

I have been reading in this ofrum and others, and i dont get solve this problem.
I update my system and then began the problems. Currently i have wpasupplicant 0.6.10-2, and network-manager/lucid uptodate 0.8-0ubuntu3.

This output: "wpa_supplicant[1171]: Association request to the driver failed" made me think the problem was the driver. But the output of lsmod is: 
> Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxnetadp              5235  0 
vboxnetflt             12242  0 
vboxdrv              1768311  2 vboxnetadp,vboxnetflt
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_idt      61450  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25677  4 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_seq_dummy           1782  0 
snd_pcm                87882  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
arc4                    1473  2 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath_pci               219819  0 
bridge                 53184  0 
stp                     2171  1 bridge
snd_timer              23649  2 snd_pcm,snd_seq
radeon                740262  3 
wlan                  247516  1 ath_pci
joydev                 11072  0 
**ath9k**                 328989  0 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    60847  1 radeon
drm_kms_helper         30742  1 radeon
snd                    71187  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath_hal               327978  1 ath_pci
**mac80211 **             238448  1 ath9k
**ath **                    9723  1 ath9k
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11956  1 videodev
lirc_ene0100            7532  0 
hp_accel               12168  0 
lirc_dev               11302  1 lirc_ene0100
lis3lv02d               7648  1 hp_accel
input_polldev           3106  1 lis3lv02d
video                  20623  0 
output                  2503  1 video
psmouse                64576  0 
serio_raw               4918  0 
drm                   198948  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
edac_core              45423  0 
edac_mce_amd            9278  0 
i2c_piix4               9639  0 
cfg80211              148546  3 ath9k,mac80211,ath
led_class               3764  2 ath9k,hp_accel
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            49833  1 
ahci                   37870  1 
r8169                  39650  0 
mii                     5237  1 r8169
Then i think all right.

Can you help? i dont understant why dont conneting?
i dont understant this:

Dec 30 20:50:28 CoYoTe kernel: [  337.372563] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 30 20:50:29 CoYoTe kernel: [  337.573002] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 30 20:50:29 CoYoTe kernel: [  337.772692] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 30 20:50:29 CoYoTe kernel: [  337.970185] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out
Dec 30 20:50:31 CoYoTe NetworkManager: <info>  wlan0: link timed out.
Dec 30 20:50:33 CoYoTe wpa_supplicant[1171]: Authentication with 00:80:5a:5c:cf:4c timed out.
Dec 30 20:50:33 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 30 20:50:33 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 30 20:50:35 CoYoTe wpa_supplicant[1171]: Trying to associate with 00:80:5a:5c:cf:4c (SSID='C54BRS4A' freq=2437 MHz)
Dec 30 20:50:35 CoYoTe NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 30 20:50:35 CoYoTe wpa_supplicant[1171]: Association request to the driver failed

help [-o<

---

### Post by ruben_linux on 2010-12-31
this is my last update: 
> Start-Date: 2010-12-24  12:41:59
Install: linux-image-2.6.32-27-generic (2.6.32-27.49), linux-headers-2.6.32-27-generic (2.6.32-27.49), linux-headers-2.6.32-27 (2.6.32-27.49)
Upgrade: libsmbclient (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2),
 lib32bz2-1.0 (1.0.5-4, 1.0.5-4ubuntu0.1),
 dmsetup (1.02.39-1ubuntu4, 1.02.39-1ubuntu4.1),
 python-packagekit (0.5.7-0ubuntu2.1, 0.5.7-0ubuntu2.2),
 libkrb5-3 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 libpurple0 (2.6.6-1ubuntu4, 2.6.6-1ubuntu4.2),
 libk5crypto3 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 apt-transport-https (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3),
 libpackagekit-qt-12 (0.5.7-0ubuntu2.1, 0.5.7-0ubuntu2.2),
 dnsmasq-base (2.52-1, 2.52-1ubuntu0.1),
 bzip2 (1.0.5-4, 1.0.5-4ubuntu0.1),
 filezilla (3.3.1-1ubuntu1, 3.3.1-1ubuntu2),
 libc-bin (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.6),
 libgutenprint2 (5.2.5-0ubuntu1, 5.2.5-0ubuntu1.1),
 erlang-crypto (13.b.3-dfsg-2ubuntu2, 13.b.3-dfsg-2ubuntu2.1),
 libcupsppdc1 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 ttf-thai-tlwg (0.4.13-4, 0.4.13-4ubuntu0.1),
 libqt4-qt3support (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 libwebkit-1.0-common (1.2.0-1, 1.2.5-0ubuntu0.10.04.1),
 libpurple-bin (2.6.6-1ubuntu4, 2.6.6-1ubuntu4.2),
 bind9-host (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),
 libcupsimage2 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 python-mako (0.2.5-2ubuntu1, 0.2.5-2ubuntu1.3),
 python-avahi (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 nspluginwrapper (1.2.2-0ubuntu6, 1.2.2-0ubuntu6.10.04.1),
 libcupscgi1 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 libgudev-1.0-0 (151-12, 151-12.3),
 poppler-utils (0.12.4-0ubuntu5, 0.12.4-0ubuntu5.1),
 libcomerr2 (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1),
 erlang-xmerl (13.b.3-dfsg-2ubuntu2, 13.b.3-dfsg-2ubuntu2.1),
 smbclient (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2),
 libcupsdriver1 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 linux-image-2.6.32-24-generic (2.6.32-24.41, 2.6.32-24.43),
 cheese (2.30.1-0ubuntu1, 2.30.1-0ubuntu2),
 libmagickcore2 (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1),
 gdebi (0.6.0ubuntu1, 0.6.0ubuntu2),
 libxml2-utils (2.7.6.dfsg-1ubuntu1, 2.7.6.dfsg-1ubuntu1.1),
 dnsutils (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),
 mysql-server (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8),
 comerr-dev (2.1-1.41.11-1ubuntu2, 2.1-1.41.11-1ubuntu2.1),
 wine1.2 (1.1.42-0ubuntu4, 1.2-0ubuntu6~lucid5),
 libbz2-1.0 (1.0.5-4, 1.0.5-4ubuntu0.1),
 update-inetd (4.35, 4.35ubuntu0.1),
 gnome-settings-daemon (2.30.1-0ubuntu1, 2.30.1-0ubuntu1.1),
 libqt4-test (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 libqt4-script (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 libqt4-designer (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 erlang-syntax-tools (13.b.3-dfsg-2ubuntu2, 13.b.3-dfsg-2ubuntu2.1),
 xserver-xorg-core (1.7.6-2ubuntu7.3, 1.7.6-2ubuntu7.4),
 libqt4-network (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 libqt4-dbus (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 bogofilter-bdb (1.2.1-0ubuntu1, 1.2.1-0ubuntu1.1),
 libavahi-glib-dev (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 python-imaging (1.1.7-1, 1.1.7-1ubuntu0.1),
 xserver-common (1.7.6-2ubuntu7.3, 1.7.6-2ubuntu7.4),
 libapparmor-perl (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.1),
 empathy-common (2.30.2-0ubuntu1, 2.30.3-0ubuntu1),
 libmagickwand2 (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1),
 phonon (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 libdevmapper1.02.1 (1.02.39-1ubuntu4, 1.02.39-1ubuntu4.1),
 libcheese-gtk18 (2.30.1-0ubuntu1, 2.30.1-0ubuntu2),
 gnome-terminal (2.29.6-0ubuntu5, 2.30.2-0ubuntu1),
 hpijs (3.10.2-2ubuntu2, 3.10.2-2ubuntu2.1),
 linux-generic (2.6.32.24.25, 2.6.32.27.29),
 smbfs (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2),
 python-software-properties (0.75.10, 0.75.10.1),
 cups-client (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 mobile-broadband-provider-info (20100407-1, 20100716-1ubuntu0.1),
 screen (4.0.3-14ubuntu1, 4.0.3-14ubuntu1.2),
 libdns64 (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),
 hplip (3.10.2-2ubuntu2, 3.10.2-2ubuntu2.1),
 libwbclient0 (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2),
 icedtea-6-jre-cacao (6b18-1.8.1-0ubuntu1, 6b20-1.9.2-0ubuntu1~10.04.1),
 empathy (2.30.2-0ubuntu1, 2.30.3-0ubuntu1),
 libnspr4-0d (4.8.4-0ubuntu1, 4.8.6-0ubuntu0.10.04.2),
 usb-creator-gtk (0.2.22, 0.2.22.1),
 gdebi-core (0.6.0ubuntu1, 0.6.0ubuntu2),
 libavahi-glib1 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 libkrb5-dev (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 libcouchdb-glib-1.0-2 (0.6.3-0ubuntu1, 0.6.3-0ubuntu2),
 mysql-server-core-5.1 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8),
 plymouth-label (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.1),
 libavahi-client-dev (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 openjdk-6-jre-lib (6b18-1.8.1-0ubuntu1, 6b20-1.9.2-0ubuntu1~10.04.1),
 libfreetype6 (2.3.11-1ubuntu2.2, 2.3.11-1ubuntu2.4),
 firefox-branding (3.6.8+build1+nobinonly-0ubuntu0.10.04.1,
 3.6.13+build3+nobinonly-0ubuntu0.10.04.1),
 e2fsprogs (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1),
 plymouth-theme-ubuntu-logo (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.1),
 libqt4-opengl (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 grub-pc (1.98-1ubuntu7, 1.98-1ubuntu9),
 libmagickcore2-extra (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1),
 libmysqlclient16 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8),
 libisccc60 (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),
 avahi-utils (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 libc6-i386 (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.6),
 libgssrpc4 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 apt-utils (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3),
 libqt4-xmlpatterns (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 update-manager (0.134.10, 0.134.11),
 indicator-sound (0.2.3-0ubuntu1, 0.2.6-0ubuntu1),
 erlang-runtime-tools (13.b.3-dfsg-2ubuntu2,
 13.b.3-dfsg-2ubuntu2.1),
 update-manager-core (0.134.10, 0.134.11),
 openjdk-6-jre-headless (6b18-1.8.1-0ubuntu1,
 6b20-1.9.2-0ubuntu1~10.04.1),
 libavahi-common-data (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 libavahi-core6 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 samba-common (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2),
 app-install-data-partner (12.10.04.3, 12.10.04.4),
 udev (151-12, 151-12.3),
 python-aptdaemon (0.11+bzr345-0ubuntu4, 0.11+bzr345-0ubuntu4.1),
 libqt4-help (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 apt (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3),
 firefox (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.13+build3+nobinonly-0ubuntu0.10.04.1),
 libpango1.0-common (1.28.0-0ubuntu2, 1.28.0-0ubuntu2.1),
 python-desktopcouch (0.6.4-0ubuntu3, 0.6.4-0ubuntu3.1),
 apparmor-utils (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.1),
 cups-common (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 libhpmud0 (3.10.2-2ubuntu2, 3.10.2-2ubuntu2.1),
 liblwres60 (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),
 bogofilter-common (1.2.1-0ubuntu1, 1.2.1-0ubuntu1.1),
 linux-headers-2.6.32-24 (2.6.32-24.41, 2.6.32-24.43),
 libcups2 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 gdm (2.30.2.is.2.30.0-0ubuntu3, 2.30.2.is.2.30.0-0ubuntu4),
 libqtcore4 (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 libavahi-ui0 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 libkrb5support0 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 sudo (1.7.2p1-1ubuntu5.1, 1.7.2p1-1ubuntu5.2),
 mysql-client-core-5.1 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8),
 cups-driver-gutenprint (5.2.5-0ubuntu1, 5.2.5-0ubuntu1.1),
 libssl-dev (0.9.8k-7ubuntu8, 0.9.8k-7ubuntu8.5),
 ttf-symbol-replacement (1.1.42-0ubuntu4, 1.2-0ubuntu6~lucid5),
 xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.13+build3+nobinonly-0ubuntu0.10.04.1),
 tzdata-java (2010k-0ubuntu0.10.04, 2010o-0ubuntu0.10.04),
 icoutils (0.26.0-4ubuntu1, 0.29.1-0ubuntu1~lucid),
 erlang-mnesia (13.b.3-dfsg-2ubuntu2, 13.b.3-dfsg-2ubuntu2.1),
 libpoppler5 (0.12.4-0ubuntu5, 0.12.4-0ubuntu5.1),
 software-properties-gtk (0.75.10, 0.75.10.1),
 cheese-common (2.30.1-0ubuntu1, 2.30.1-0ubuntu2),
 software-properties-kde (0.75.10, 0.75.10.1),
 linux-headers-generic (2.6.32.24.25, 2.6.32.27.29),
 dpkg (1.15.5.6ubuntu4.1, 1.15.5.6ubuntu4.4),
 erlang-public-key (13.b.3-dfsg-2ubuntu2, 13.b.3-dfsg-2ubuntu2.1),
 aptdaemon (0.11+bzr345-0ubuntu4, 0.11+bzr345-0ubuntu4.1),
 libxml2 (2.7.6.dfsg-1ubuntu1, 2.7.6.dfsg-1ubuntu1.1),
 libbind9-60 (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),
 linux-image-generic (2.6.32.24.25, 2.6.32.27.29),
 gnome-terminal-data (2.29.6-0ubuntu5, 2.30.2-0ubuntu1),
 cups (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 libpoppler-glib4 (0.12.4-0ubuntu5, 0.12.4-0ubuntu5.1),
 bogofilter (1.2.1-0ubuntu1, 1.2.1-0ubuntu1.1),
 libxml2-dev (2.7.6.dfsg-1ubuntu1, 2.7.6.dfsg-1ubuntu1.1),
 libqt4-sql (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 flashplugin-installer (10.1.82.76ubuntu0.10.04.2, 10.1.102.65ubuntu0.10.04.1),
 libqt4-svg (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 python-aptdaemon-gtk (0.11+bzr345-0ubuntu4, 0.11+bzr345-0ubuntu4.1),
 python-desktopcouch-records (0.6.4-0ubuntu3, 0.6.4-0ubuntu3.1),
 wine (1.1.42-0ubuntu4, 1.2-0ubuntu6~lucid5),
 tar (1.22-2, 1.22-2ubuntu1),
 libpango1.0-dev (1.28.0-0ubuntu2, 1.28.0-0ubuntu2.1),
 libfreetype6-dev (2.3.11-1ubuntu2.2, 2.3.11-1ubuntu2.4),
 dpkg-dev (1.15.5.6ubuntu4.1, 1.15.5.6ubuntu4.4),
 gwibber-service (2.30.1-0ubuntu1, 2.30.3-0ubuntu1),
 libphonon4 (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 e2fslibs (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1),
 libqt4-xml (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 packagekit (0.5.7-0ubuntu2.1, 0.5.7-0ubuntu2.2),
 fglrx-modaliases (8.723.1-0ubuntu4, 8.723.1-0ubuntu5),
 mysql-client (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8),
 filezilla-common (3.3.1-1ubuntu1, 3.3.1-1ubuntu2),
 cups-bsd (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 libqt4-assistant (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 gdebi-kde (0.6.0ubuntu1, 0.6.0ubuntu2),
 desktopcouch (0.6.4-0ubuntu3, 0.6.4-0ubuntu3.1),
 erlang-inets (13.b.3-dfsg-2ubuntu2, 13.b.3-dfsg-2ubuntu2.1),
 libkadm5clnt-mit7 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 libapparmor1 (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.1),
 libudev0 (151-12, 151-12.3),
 update-manager-kde (0.134.10, 0.134.11),
 libpq-dev (8.4.4-0ubuntu10.04, 8.4.5-0ubuntu10.04),
 libplymouth2 (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.1),
 libwebkit-1.0-2 (1.2.0-1, 1.2.5-0ubuntu0.10.04.1),
 libisccfg60 (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),
 usb-creator-common (0.2.22, 0.2.22.1),
 libkadm5srv-mit7 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 libc6-dev (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.6),
 libqtgui4 (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 plymouth-x11 (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.1),
 apparmor (2.5-0ubuntu3, 2.5.1-0ubuntu0.10.04.1),
 tzdata (2010k-0ubuntu0.10.04, 2010o-0ubuntu0.10.04),
 libpackagekit-glib2-12 (0.5.7-0ubuntu2.1, 0.5.7-0ubuntu2.2),
 avahi-daemon (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 plymouth-theme-ubuntu-text (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.1),
 libavahi-client3 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 libgksu2-0 (2.0.13~pre1-1ubuntu4, 2.0.13~pre1-1ubuntu4.1),
 libssl0.9.8 (0.9.8k-7ubuntu8, 0.9.8k-7ubuntu8.5),
 libpq5 (8.4.4-0ubuntu10.04, 8.4.5-0ubuntu10.04),
 man-db (2.5.7-2, 2.5.7-2ubuntu1),
 python-papyon (0.4.8-0ubuntu1, 0.4.8-0ubuntu2),
 libqt4-webkit (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 imagemagick (6.5.7.8-1ubuntu1, 6.5.7.8-1ubuntu1.1),
 openssl (0.9.8k-7ubuntu8, 0.9.8k-7ubuntu8.5),
 erlang-ssl (13.b.3-dfsg-2ubuntu2, 13.b.3-dfsg-2ubuntu2.1),
 libpango1.0-0 (1.28.0-0ubuntu2, 1.28.0-0ubuntu2.1),
 rsyslog (4.2.0-2ubuntu8, 4.2.0-2ubuntu8.1),
 libkdb5-4 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 libss2 (1.41.11-1ubuntu2, 1.41.11-1ubuntu2.1),
 linux-libc-dev (2.6.32-24.41, 2.6.32-27.49),
 libdesktopcouch-glib-1.0-2 (0.6.3-0ubuntu1, 0.6.3-0ubuntu2),
 samba-common-bin (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2),
 libwww-perl (5.834-1, 5.834-1ubuntu0.1),
 libqt4-sql-mysql (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 winbind (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2),
 grub-common (1.98-1ubuntu7, 1.98-1ubuntu9),
 krb5-multidev (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 ureadahead (0.100.0-4.1.2, 0.100.0-4.1.3),
 libqt4-scripttools (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1),
 libisc60 (9.7.0.dfsg.P1-1, 9.7.0.dfsg.P1-1ubuntu0.1),
 libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.4),
 libavahi-gobject0 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 libcupsmime1 (1.4.3-1ubuntu1.2, 1.4.3-1ubuntu1.3),
 libc-dev-bin (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.6),
 libavahi-common-dev (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 mountall (2.15, 2.15.3),
 libc6 (2.11.1-0ubuntu7.2, 2.11.1-0ubuntu7.6),
 gzip (1.3.12-9ubuntu1, 1.3.12-9ubuntu1.1),
 python-lazr.restfulclient (0.9.11-1ubuntu1, 0.9.11-1ubuntu1.1),
 avahi-autoipd (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 libaprutil1 (1.3.9+dfsg-3build1, 1.3.9+dfsg-3ubuntu0.10.04.1),
 openjdk-6-jre (6b18-1.8.1-0ubuntu1, 6b20-1.9.2-0ubuntu1~10.04.1),
 libavahi-common3 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1),
 mysql-common (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8),
 icedtea6-plugin (6b18-1.8.1-0ubuntu1, 6b20-1.9.2-0ubuntu1~10.04.1),
 mysql-server-5.1 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8),
 libnss3-1d (3.12.6-0ubuntu3, 3.12.8-0ubuntu0.10.04.1),
 firefox-gnome-support (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.13+build3+nobinonly-0ubuntu0.10.04.1),
 nautilus-sendto-empathy (2.30.2-0ubuntu1, 2.30.3-0ubuntu1),
 python-libxml2 (2.7.6.dfsg-1ubuntu1, 2.7.6.dfsg-1ubuntu1.1),
 plymouth (0.8.2-2ubuntu2, 0.8.2-2ubuntu2.1),
 libgdiplus (2.4.2-1build1, 2.4.2-1ubuntu0.10.04.1),
 mysql-client-5.1 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.8),
 hplip-data (3.10.2-2ubuntu2, 3.10.2-2ubuntu2.1),
 erlang-base (13.b.3-dfsg-2ubuntu2, 13.b.3-dfsg-2ubuntu2.1),
 lftp (4.0.2-1, 4.0.2-1ubuntu0.1),
 packagekit-backend-apt (0.5.7-0ubuntu2.1, 0.5.7-0ubuntu2.2)
End-Date: 2010-12-24  12:49:11

---

### Post by ruben_linux on 2011-01-01
aptitude show wpasupplicant

Paquete: wpasupplicant
Estado: instalado
Instalado automáticamente: no
Versión: 0.6.10-2
Prioridad: opcional
Sección: net
Desarrollador: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Tamaño sin comprimir: 971k
Depende de: libc6 (>= 2.4), libdbus-1-3 (>= 1.1.1), libnl1 (>= 1.1), libpcsclite1 (>= 1.5.3), libreadline6 (>= 6.0), libssl0.9.8 (>= 0.9.8m-1), lsb-base (>= 3.0-6),
            adduser
Sugiere: wpagui, libengine-pkcs11-openssl
Descripción: client support for WPA and WPA2 (IEEE 802.11i)
 WPA and WPA2 are methods for securing wireless networks, the former using IEEE 802.1X, and the latter using IEEE 802.11i. This software provides key negotiation with
 the WPA Authenticator, and controls association with IEEE 802.11i networks.
Página de inicio: [http://w1.fi/wpa_supplicant/](http://w1.fi/wpa_supplicant/)

when i read this output, i found that i dont have installed "libdbus-1-3". when i search in ubuntu i didnt found. i download by web debian and install without a problem, now i will reboot and then post my result

---

