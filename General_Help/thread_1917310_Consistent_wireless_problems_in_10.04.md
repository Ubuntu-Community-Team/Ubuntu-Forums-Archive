---
title: "Consistent wireless problems in 10.04"
date: 2012-01-29
forum: General Help
---

### Post by DocVoodoo on 2012-01-29
Okay, so out of nowhere my wireless disconnected, I went to reconnect, but it didn't appear to be recognising any networks, also, on right-clicking on the network icon, "Wireless Enabled" is greyed out.
This was easily fixed by 'sudo gedit /var/lib/NetworkManager/NetworkManager.state' and changing WirelessEnabled to true.
The thing is, this has happened several times before (perhaps four of five times) and happens seemingly at random.
My question is, why is this happening and how can I remedy it?

---

### Post by varunendra on 2012-01-31
Welcome to the forums DocVoodoo,

> **DocVoodoo said:**
> Okay, so out of nowhere my wireless disconnected, I went to reconnect, but it didn't appear to be recognising any networks, also, on right-clicking on the network icon, **"Wireless Enabled" is greyed out**.
Looks like the wifi adapter is playing tricks. To get some details about it, please post the outputs of:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep -i wlan
ifconfig -a
iwconfig
rfkill list all
```

---

### Post by DocVoodoo on 2012-02-02
Here you go:

```
queebo@QueeboTown:~$ uname -mr
2.6.32-38-generic i686
```

```
queebo@QueeboTown:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
    Kernel driver in use: sky2
    Kernel modules: sky2
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k

```
```
queebo@QueeboTown:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            40033  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
arc4                    1153  2 
pcmcia                 30784  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121632  0 
i915                  289715  3 
drm_kms_helper         29329  1 i915
tifm_7xx1               3690  0 
yenta_socket           20408  1 
mac80211              205434  1 ath5k
ath                     7611  1 ath5k
snd                    54244  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   163747  4 i915,drm_kms_helper
tifm_core               6045  1 tifm_7xx1
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63677  0 
serio_raw               3978  0 
sony_laptop            28248  0 
cfg80211              126528  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32680  2 
sky2                   40807  0 
```

```
queebo@QueeboTown:~$ dmesg | grep -i wlan
[   19.431136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  119.259726] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[  119.260296] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 1)
[  119.262024] wlan0: direct probe responded
[  119.262032] wlan0: authenticate with AP 00:0f:cc:25:a8:2c (try 1)
[  119.263552] wlan0: authenticated
[  119.263582] wlan0: associate with AP 00:0f:cc:25:a8:2c (try 1)
[  119.265620] wlan0: RX AssocResp from 00:0f:cc:25:a8:2c (capab=0x471 status=0 aid=3)
[  119.265626] wlan0: associated
[  119.266570] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  127.696097] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[  127.930451] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[  128.163797] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 1)
[  128.165201] wlan0: direct probe responded
[  128.165209] wlan0: authenticate with AP 00:0f:cc:25:a8:2c (try 1)
[  128.166686] wlan0: authenticated
[  128.166719] wlan0: associate with AP 00:0f:cc:25:a8:2c (try 1)
[  128.168558] wlan0: RX AssocResp from 00:0f:cc:25:a8:2c (capab=0x471 status=0 aid=3)
[  128.168564] wlan0: associated
[  130.133065] wlan0: no IPv6 routers present
[31768.225108] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[31775.365685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[31777.339309] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[31777.576503] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 1)
[31777.577945] wlan0: direct probe responded
[31777.577952] wlan0: authenticate with AP 00:0f:cc:25:a8:2c (try 1)
[31777.579374] wlan0: authenticated
[31777.579412] wlan0: associate with AP 00:0f:cc:25:a8:2c (try 1)
[31777.581217] wlan0: RX AssocResp from 00:0f:cc:25:a8:2c (capab=0x471 status=0 aid=2)
[31777.581225] wlan0: associated
[31777.582653] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[31788.124068] wlan0: no IPv6 routers present
[32663.009141] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 1)
[32663.211366] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 2)
[32663.408056] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 3)
[32663.608055] wlan0: direct probe to AP 00:0f:cc:25:a8:2c timed out
[33177.512039] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 1)
[33177.513378] wlan0: direct probe responded
[33177.513384] wlan0: authenticate with AP 00:0f:cc:25:a8:2c (try 1)
[33177.514935] wlan0: authenticated
[33177.514960] wlan0: associate with AP 00:0f:cc:25:a8:2c (try 1)
[33177.516897] wlan0: RX AssocResp from 00:0f:cc:25:a8:2c (capab=0x471 status=0 aid=2)
[33177.516906] wlan0: associated
[33180.349116] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[33190.796073] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[33191.031415] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 1)
[33191.033273] wlan0: direct probe responded
[33191.033280] wlan0: authenticate with AP 00:0f:cc:25:a8:2c (try 1)
[33191.034741] wlan0: authenticated
[33191.034766] wlan0: associate with AP 00:0f:cc:25:a8:2c (try 1)
[33191.036604] wlan0: RX AssocResp from 00:0f:cc:25:a8:2c (capab=0x471 status=0 aid=2)
[33191.036610] wlan0: associated
[34906.648085] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[34913.300131] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[35012.983504] wlan0: deauthenticating from 00:0f:cc:25:a8:2c by local choice (reason=3)
[35013.215508] wlan0: direct probe to AP 00:0f:cc:25:a8:2c (try 1)
[35013.216850] wlan0: direct probe responded
[35013.216855] wlan0: authenticate with AP 00:0f:cc:25:a8:2c (try 1)
[35013.219103] wlan0: authenticated
[35013.219127] wlan0: associate with AP 00:0f:cc:25:a8:2c (try 1)
[35013.220970] wlan0: RX AssocResp from 00:0f:cc:25:a8:2c (capab=0x471 status=0 aid=2)
[35013.220977] wlan0: associated
[35013.222449] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[35024.024029] wlan0: no IPv6 routers present

```
```
queebo@QueeboTown:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:80:20:4a:28  
          inet6 addr: fe80::21a:80ff:fe20:4a28/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82415 (82.4 KB)  TX bytes:22972 (22.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33723 (33.7 KB)  TX bytes:33723 (33.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:dd:ed:e9  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fedd:ede9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1584042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1197941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1744610427 (1.7 GB)  TX bytes:147806752 (147.8 MB)

```
```
queebo@QueeboTown:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"eircom1132 3740"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0F:CC:25:A8:2C   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
queebo@QueeboTown:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


Thanks for the speedy reply, I really appreciate it.

---

### Post by varunendra on 2012-02-03
First off, please note that whenever you post an output, **do wrap it in [noparse]```
 and 
```[/noparse] tags**. Doing so puts it in the friendly 'code' box that preserves its formatting and makes it easily readable.

Your wireless card and driver:
> **DocVoodoo said:**
> ```

06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k
```

It seems some heavy downloading stuff is going on over the wifi (torrents?):
> **DocVoodoo said:**
> ..
          **[COLOR=DarkRed]RX bytes:1744610427 (1.7 GB)[/COLOR]  TX bytes:147806752 (147.8 MB)**
..

However, the signal quality is not good:
> **DocVoodoo said:**
> ```

wlan0     IEEE 802.11bg  ESSID:**"eircom1132 3740"  **
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0F:CC:25:A8:2C   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=[COLOR=Red]37[/COLOR]/70 ** Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Accordingly, try one or both of these two things:

[LIST]
[*]Run the following commands (DO NOT RESTART after running them):
[/LIST]
```
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k nohwcrypt=1
```
Let the network manager pick up the adapter, then retry connecting and see if it becomes any better. If it does, we'll have to make the change permanent.

[LIST]
[*]Try moving close to the access-point/router to improve the signal quality. 37/70 is not sufficient for a stable connection. I'd say, if possible, make it 70/70 by moving close and see if the connection breaks again. If it still does, at least it'll rule out the chances of signal quality being the problem.
[/LIST]

---

### Post by lisati on 2012-02-03
> **DocVoodoo said:**
> 
Thanks for the speedy reply, I really appreciate it.

You really shoud use the [noparse]```
 and 
```[/noparse] tags, it helps make the listing easier to read.

---

### Post by DocVoodoo on 2012-02-04
> **varunendra said:**
> 
Accordingly, try one or both of these two things:

[LIST]
[*]Run the following commands (DO NOT RESTART after running them):
[/LIST]
```
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k nohwcrypt=1
```

I tried those two commands last night, unfortunately to no avail. I also tried increased proximity to the router, again, no luck.

There have also been some additional happenings. 
Sometimes it will disconnect, as per the beginning of the post, but "Enable Wireless" will not be greyed out and will still be ticked, however, a network won't be detected, if I untick 'Enable Wireless' and attempt to tick it again, it will then grey out and NetworkManager.state will show WirelessEnabled=false. However, if I plug in the wired connection, it will immediately detect the wireless connection.
Also, if I have to use the 'sudo gedit' command to change WirelessEnabled back to 'true' in NetworkManager.state, following the reboot, there will be no option anywhere for wireless, as if there were no wifi card.

Oh, I also attempted to restart network manager, but got these:

```

queebo@QueeboTown:~$ service network-manager restart
restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.75" (uid=1000 pid=7998 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
queebo@QueeboTown:~$ 

```And this:

```

queebo@QueeboTown:~$ service network restart
network: unrecognized service
queebo@QueeboTown:~$ 

```

---

### Post by varunendra on 2012-02-05
> **DocVoodoo said:**
> 
```

queebo@QueeboTown:~$ service network restart
network: unrecognized service
queebo@QueeboTown:~$ 

```
That command is actually *"service network**ing** restart"*. Although I instead use:
```
sudo /etc/init.d/networking restart
```
However, I don't think that would do any good in this case. Are you using WPA/WPA2 mixed mode in your router? If yes, try changing it to WPA2 only, since mixed mode encryption is too hard to cope with for some drivers. If that doesn't help, you may try madwifi driver as suggested in this post:
[http://ubuntuforums.org/showpost.php?p=11089234&postcount=3](http://ubuntuforums.org/showpost.php?p=11089234&postcount=3)

Note that you may have to install "subversion" to use "svn" command:
```
sudo apt-get install subversion
```

Also, you would have to unload the default ath5k driver before modprob'ing ath_pci:
```
sudo modprobe -rfv ath5k
```

After running both these commands, try the madwifi method suggested in the above linked post.

By the way, what is your laptop's brand / model and other specs? Have you tried the latest 11.10 live cd/usb on it? Some people have indicated that some issues with atheros wireless have been fixed in it.

---

### Post by DocVoodoo on 2012-02-07
Yes! The madwifi seems to done the trick, for the moment anyway. I'm going to wait another day just to be sure before I mark it solved.

I tried 11.10 a while ago, but I found it kind of daunting, especially as a first try from Windows.

---

### Post by varunendra on 2012-02-07
> **DocVoodoo said:**
> Yes! The madwifi seems to done the trick, for the moment anyway. I'm going to wait another day just to be sure before I mark it solved.
Good job! :)
I'm eagerly waiting for the feedback. Let's hope for the best!

---

### Post by DocVoodoo on 2012-02-09
Well, I think I can safely say all is well now.
Thank you very much for the help. :D

---

