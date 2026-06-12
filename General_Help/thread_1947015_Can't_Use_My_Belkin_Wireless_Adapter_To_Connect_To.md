---
title: "Can't Use My Belkin Wireless Adapter To Connect To The Internet In Ubuntu"
date: 2012-03-25
forum: General Help
---

### Post by thesandwichman on 2012-03-25
**Problem:** I have the latest Desktop version of Ubuntu (just downloaded it onto a USB Stick with Pendrive). My Belkin Wireless Adapter SAYS it's only compatible with Windows XP, Vista and Windows 7 (I didn't know I'd ever need Ubuntu when I got the adapter). So, now I need to find a way to get the driver in Ubuntu. Also, I am a COMPLETE beginner in any Linux/GNU whatsoever (but not afraid to learn the ways of the command line).

Also, I have googled the problem but usually what comes up is something requiring lots of command line knowledge or something about ndiswrapper (which I know NOTHING about).


Right now I think my options are
a. Stick to Windows
b. Consult every forum I know of for a solution
c. Get some other Linux Distro (doubt it would help)
d. Find an adapter compatible with Ubuntu (I reeaallllyy don't wanna do this, because I'm only learning to use Ubuntu for my sake and I'd rather not spend ANYTHING on it if I don't absolutely have to).


Thanks in advance, guys. :-({|=

---

### Post by Rodney9 on 2012-03-26
What model is your Belkin and which version of Ubuntu are you using ?

Rodney

---

### Post by Mark Phelps on 2012-03-26
Basically, ALL of the wireless adapters make that same claim -- because their suppliers don't want to bother to write Linux drivers for them.

As a start, you should search both the Hardware forum and the Networking forum to see if there are any existing threads for your adapter.  If there are, there might already be the solution posted.

---

### Post by wildmanne39 on 2012-03-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by thesandwichman on 2012-03-26
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you


```
ubuntu@ubuntu:~$ cat /etc/lab-release; uname -a
cat: /etc/lab-release: No such file or directory
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
ubuntu@ubuntu:~$ lspci -nnk | grep -1A2 net
    Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  02)
    Subsystem: Dell Device [1028:02e0]
    Kernel driver in use: r8169
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102  Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 002: ID 050d:945a Belkin Components 
Bus 002 Device 004: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 006 Device 002: ID 046d:c52e Logitech, Inc. 
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ubuntu@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
udf                    83826  1 
crc_itu_t              12627  1 udf
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ath9k                 112711  0 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
mac80211              272785  1 ath9k
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
r8712u                163310  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13599  1 ath9k
ath9k_hw              293893  2 ath9k,ath9k_common
snd_timer              28932  2 snd_pcm,snd_seq
joydev                 17393  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  2 ath9k,ath9k_hw
snd                    55902  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  3 ath9k,mac80211,ath
psmouse                73673  0 
serio_raw              12990  0 
dcdbas                 14098  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  1 
uas                    17699  0 
r8169                  43104  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915


```

These are the results I got from entering those commands.

> What model is your Belkin and which version of Ubuntu are you using ?

The belkin USB adapter model is n150. Ubuntu version is the latest desktop version. 11.10 I think...

---

### Post by Mark Phelps on 2012-03-26
It looks like you're looking for a simple solution -- which, based on MY search of the Networking forums (something I suggested that YOU do back in my earlier post), is not going to be available.

The only solution that folks said works was to build the necessary drivers from source -- in effect, compiling the module.

In the Networking forum, you will find threads mentioning how to do that.  You will have to download the RealTek Linux driver source and build the drivers from that.

---

### Post by wildmanne39 on 2012-03-26
Hi, you have the driver you need installed but there is also another driver conflicting, please do:
```
sudo rmmod -f ath9k
sudo modprobe r8712u
```
with the adapter plugged in give it a few seconds does it come on? do not reboot your computer this is only for this boot.
Thanks

---

### Post by scphan on 2012-04-23
Just wanted to add the specific Belkin adapter you're using is F9L1001.  From all my searching it seems there's different ones branded as the N150 and the F9L1001 is the most recent according to the one they sell on amazon: [http://www.amazon.com/Belkin-Wireless-Adapter-Latest-Generation/dp/B004N625BE]("http://www.amazon.com/Belkin-Wireless-Adapter-Latest-Generation/dp/B004N625BE")

I can tell because you're vendor:device_id is 050d:[COLOR="Red"]945a[/COLOR] from the lsusb output and I also bought the same one :p.

wildmanne39's suggestion (#7) works for me.  Though I didn't have a ath9k driver running so I only used the modprobe command.  Did modprobe and adapter ran successfully at full speed it seems and WPA security.

Now I need to find out how to make it do that on bootup. Btw I'm also running 11.10.

---

### Post by wildmanne39 on 2012-04-23
Hi scphan, just do:
```
sudo su 
echo ath9k >> /etc/modules 
exit

```
if the ath9k is your driver if not just put your driver in its place.
Thanks

---

### Post by scphan on 2012-04-25
> **wildmanne39 said:**
> Hi scphan, just do:
```
sudo su 
echo ath9k >> /etc/modules 
exit

```
if the ath9k is your driver if not just put your driver in its place.
Thanks

Yep that works, I meant r8712u.  Appended to /etc/modules and at bootup works fine.

Thanks

---

### Post by wildmanne39 on 2012-04-25
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

