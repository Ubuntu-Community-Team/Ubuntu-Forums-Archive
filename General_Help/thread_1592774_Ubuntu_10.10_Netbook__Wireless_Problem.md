---
title: "Ubuntu 10.10 Netbook  Wireless Problem"
date: 2010-10-10
forum: General Help
---

### Post by derricklongley on 2010-10-10
Having a problem finding networks and connecting. It works with a wired connection. I have an ACER 4520 and I'm running Ubuntu 10.10 only. Let me know if you need more than the information below, and I will need a walk through if you need more info, thanks in advance.



lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
07:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth2      no wireless extensions.

---

### Post by derricklongley on 2010-10-10
Any suggestions?

---

### Post by derricklongley on 2010-10-11
?

---

### Post by JackNocturne on 2010-10-11
Hi,
Do you have the drivers for Broadcom Corporation BCM4311 installed?

If not, go under **System> Administration> Synaptic Package manager**

Search for the following packages& install them

1)b43-fwcutter (install this **first**)

2)bcmwl-kernel-source

---

### Post by derricklongley on 2010-10-11
They both say installed.

---

### Post by JackNocturne on 2010-10-11
Ok, and it still doesn't work?

Try the following command at terminal and see if it can detect **wireless** networks
```
iwlist scan
```

---

### Post by derricklongley on 2010-10-11
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

---

### Post by slammer2x on 2010-10-11
I've tried to solve following method but it also doesn't work with me too. (My notebook is ACER 4520) Anyone else?:confused:

---

### Post by derricklongley on 2010-10-11
what should I do next?

---

### Post by derricklongley on 2010-10-11
?

---

### Post by JackNocturne on 2010-10-11
I don't know what to say, i'd assume if the drivers were installed it would work but not in your case:(

The command output said your **none** of your interfaces support scanning (so the wireless cannot detect anything because it cannot scan yet)

My suggestion is to** reinstall the drivers **and also search threads with people with similar driver as yours aka BCM4311 802.11b/g WLAN (rev 01)

---

### Post by JackNocturne on 2010-10-11
Here is extra material

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by wsims2 on 2010-10-11
What happens when you try and bring the wlan0 up?

```
sudo ifconfig wlan0 up
```

---

### Post by derricklongley on 2010-10-11
wlan0: ERROR while getting interface flags: No such device

---

### Post by darkstaar on 2010-10-11
The BCM4311 doesn't use the B43 driver. You'll need to install the WL (STA( driver for that adapter.

---

### Post by darkstaar on 2010-10-11
The BCM4311 doesn't use the B43 driver. You'll need to install the WL (STA) driver for that adapter.

---

### Post by darkstaar on 2010-10-11
Triplicate post deleted.

---

### Post by darkstaar on 2010-10-11
Duplicate post deleted.

---

### Post by derricklongley on 2010-10-11
> **darkstaar said:**
> The BCM4311 doesn't use the B43 driver. You'll need to install the WL (STA) driver for that adapter.
  How do I do that?

---

### Post by darkstaar on 2010-10-11
Should be an option under **System --> Administration --> Additional Drivers**. If it's not there, you may have to install the bcmwl-kernel-source from the CD (it'll be in Synaptic if you've enabled the CD as a software source.

Once that's installed, the STA driver should be available.

---

### Post by derricklongley on 2010-10-11
installed it and nothing happened

---

### Post by darkstaar on 2010-10-11
You've activated the STA driver successfully (under **System --> Administration --> Additional Drivers**) and still no wireless?

---

### Post by derricklongley on 2010-10-11
correct, what else could it be?

---

### Post by darkstaar on 2010-10-11
You might try bringing the wireless up manually.

```
sudo ifconfig eth1 up
```

If no such device, try replacing eth1 with eth0.

---

### Post by derricklongley on 2010-10-11
nothing on eth1 and this below on eth0

eth0      Link encap:Ethernet  HWaddr 00:1e:68:13:0a:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000

---

### Post by darkstaar on 2010-10-12
Okay. Looks like your wireless device is eth1 and it's up and running but (I'm assuming) it doesn't detect any wireless networks. If the STA driver is installed and activated, wireless is enabled in the Network manager and the wireless adapter switch on your laptop is on, it should work.

You might try rebooting, then checking to make certain that the STA driver is still active.

---

### Post by derricklongley on 2010-10-12
Firstoff thanks for all the help to everyone so far. 
 
Next, the STA driver is installed and active and Network manager seems to be up (what's the wireless adapter switch?) and its correct I seem to be finding no wireless networks. The network I'm looking for is secured if that makes any difference.

---

### Post by derricklongley on 2010-10-12
?

---

### Post by JackNocturne on 2010-10-12
hi again,

By the way have you tried your wireless interface with any other OS? I assume you had some other Operating System before you settled on Ubuntu 10.10?

Also can you give output of

```
lsmod
```   This lists the loaded kernel modules

---

### Post by spin498 on 2010-10-12
I'm going to throw my 2 cents in here. Not that it will help, but I've upgraded two separate systems to 10.10 both had wireless up and running before the upgrade. After the upgrade neither wireless would work. One was an Ubuntu Studio the other was a vanilla version of 10.10. Both are PC's. In my case on both machines it says the wireless is there but it won't run. I think there's a bug here, since it appears the same issue on multiple machines.

Oh, on both machines wireless works if I boot into the old Kernel associated with 10.04

---

### Post by derricklongley on 2010-10-12
lsmod
Module                  Size  Used by
cdc_ether               4052  0 
usbnet                 17312  1 cdc_ether
mii                     4425  1 usbnet
nls_utf8                1069  1 
udf                    79366  1 
usb_storage            40172  0 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
binfmt_misc             6599  1 
nvidia               7088432  27 
joydev                  8735  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7736  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           184207  0 
wl                   1959533  0 
video                  18712  0 
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
output                  1883  1 video
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               55847  0 
mtd                    18877  2 sm_common,nand
lib80211                5058  2 lib80211_crypt_tkip,wl
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
agpgart                32011  1 nvidia
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
k8temp                  3132  0 
i2c_nforce2             5179  0 
psmouse                59033  0 
lp                      7342  0 
serio_raw               4022  0 
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21106  0 
sdhci_pci               6339  0 
ahci                   19013  0 
firewire_core          46643  1 firewire_ohci
sdhci                  15890  1 sdhci_pci
crc_itu_t               1383  2 udf,firewire_core
led_class               2633  1 sdhci
libahci                21667  3 ahci
forcedeth              49433  0 
pata_amd                8746  1

---

### Post by JackNocturne on 2010-10-12
[PHP]wl                   1959533  0 [/PHP]  and this [PHP]lib80211                5058  2 lib80211_crypt_tkip,wl[/PHP]shows that the wireless driver modules are **loaded** so it should work, at this point i really don't know whats the problem:(   Try connecting to other networks not just that one. 

In the end it could be your wireless interface itself.

---

### Post by derricklongley on 2010-10-12
it isn't showing any networks to connect with.

---

### Post by derricklongley on 2010-10-16
I reinstalled 10.10 and it still didn't work even after making some  changes. Then I downloaded and installed 10.4 and went to  system>administration> hardware then when it showed the two  Braodcom drivers weren't installed I activated them rebooted and b it  found my wireless networks.

---

### Post by ArgusVision on 2010-10-16
I installed 10.10 on a friend's Acer 4520 last Wednesday. I believe it has the same specs.(I'll have to get them later to verify.) I know it has the same broadcom card and is having similar connectivity issues. It worked for a few hours, then strangely enough stopped. I think it may have to do with the interface being assigned as eth1 and not being seen as a wireless interface. When she went to System > Administration > Network Tools and Selected the eth1 interface it was listed as an ethernet interface (hardwire) instead of wireless. There's a post from back in 2007 that seems like it maybe interesting. 
        [http://ubuntuforums.org/archive/index.php/t-338332.html](http://ubuntuforums.org/archive/index.php/t-338332.html)
The intermittent name change experienced by this user could be similar to what we're experiencing. (Although that's purely conjecture at this point.)
I won't be able to get my hands on her PC again until tomorrow at the earliest. But could you post your /etc/network/interfaces file contents?
Thank's

---

### Post by ArgusVision on 2010-10-16
Guess I should have read further. So you just reinstalled 10.04?

---

### Post by kioni09 on 2010-10-17
> **ArgusVision said:**
> Guess I should have read further. So you just reinstalled 10.04?
Here is the solution, i had the same problem and now Im using my bcm43 

[http://ubuntuforums.org/showthread.php?t=1425993](http://ubuntuforums.org/showthread.php?t=1425993)

PS.: This is the same problem but with different driver, but you only need the replace the terms
PS2: I recommend you install STA, I think is ( kml:...something xD)

---

### Post by jamelt on 2010-10-18
> **kioni09 said:**
> Here is the solution, i had the same problem and now Im using my bcm43 

[http://ubuntuforums.org/showthread.php?t=1425993](http://ubuntuforums.org/showthread.php?t=1425993)

PS.: This is the same problem but with different driver, but you only need the replace the terms
PS2: I recommend you install STA, I think is ( kml:...something xD)


This solutions may not work for you, It didn't work for me. If you have already activated your driver in Additional Drivers, this will not do anything, because I believe this command does what you would do in the GUI for Additional Drivers.

---

### Post by choochoousmc on 2010-10-19
> **derricklongley said:**
> ?

your thread says solved. But what did you do to solve it?
Other people may gain from the knowledge.

---

### Post by derricklongley on 2010-10-27
> **ArgusVision said:**
> Guess I should have read further. So you just reinstalled 10.04?

Yup, installing 10.4 then system>adminstration>hadrware drivers and installing the Broadcom STA wireless driver and it worked immediately.

---

### Post by uwe.koch.k on 2010-11-09
> **derricklongley said:**
> Yup, installing 10.4 then system>adminstration>hadrware drivers and installing the Broadcom STA wireless driver and it worked immediately.

Well, that's really no solution. You asked for a solution on 10.10. I have not seen any solution here. I did something similar you did: I installed 10.10, but when booting, via grub, launch any 2.6.32-* flavour, which, in turn, are 10.04 equivalent. Of course, the wireless connection will do it, as it did before. But the question remains: what happens on 10.10?

---

### Post by derricklongley on 2010-11-26
10.10 didn't have a solution back when I started this thread, and I'm not sure if anyone else has worked with it and figured out what the problem is.

---

### Post by uwe.koch.k on 2010-11-26
I placed a question regarding the matter in launchpad, on the following link:

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/134483](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/134483)

I did not follow the suggested solution, because of lack of time to do so in the laptop, but will give a try in the near future. If it works for you, great. Please place your results here if it does.

---

### Post by frank4360 on 2011-03-27
Don't know if your problem is solved, but I lost WiFi connection when upgrading to Ubuntu 10.10 on a dual boot Netbook.

I was looking for drivers in Synaptic Package Manager when I noticed there is a tab for Additional Drivers: System>>Administration>>Additional Drivers

And it was as simple as that - the drivers for my Broadcom BCM4313 were offered, and I installed with no problem at all.

Hope this helps.

---

