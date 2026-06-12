---
title: "Problems with file sharing, DVD playback and Media Centre stuff"
date: 2011-07-23
forum: General Help
---

### Post by GaryReggae on 2011-07-23
I am trying to get my new Media Centre PC up and running but I am getting frustrated about things that should be simple not working. I've been using Ubuntu on my laptop for over a year and not had any problems but this machine is a different matter.

First of all, I want to share my Home folder and external HDD (which is plugged into one of the media centre's USB sockets). I am sure this was very easy on my laptop but not so here. I have right-clicked the expansion drive and looked at all the options (such as under Properties) but there is nothing relating to sharing. The Permissions tab says that it was unable to determine the permissions. 

I then looked under System > Preferences > Personal File Sharing and the dialogue box comes up with tick boxes for Bluetooth but under 'Share files over the network' it says that "This feature cannot be enabled because the required packages are not installed on your system.". This is a very helpful message as it doesn't give the option to get the packages nor does it even suggest what packages are needed.

I then downloaded through the Software Centre the Samba package. I have gone into that and set up a share to the home folder and expansion drive but this doesn't seem to be very secure, as there is nowhere to put a password (although my wireless network is supposedly secure). I can access the home folder from my laptop but it doesn't like the expansion drive, saying that it was unable to mount the Windows device. It's not a Windows device and I can access it perfectly well from the machine it's plugged into.

Next on the list is problems playing DVDs. I eventually managed to figure out how to install the restricted plugins and now a DVD will play but the video is totally frozen and the audio very choppy. This is just using the pre-installed Movie Player. Is this a software or hardware issue? It's a brand new PC so should be more than capable of playing a DVD.

Finally (for the moment) I am trying to get some software that will do all of the following:

 - play DVDs and be able to record them to the HDD;
 - play MP3s off the expansion drive and allow creation of playlists and be able to shuffle them;
 - allow the viewing of photos from the HDD, expansion drive and SD cards;
 - play videos off YouTube; and
w- Watch TV from the analogue TV Tuner PCI card.

The last one is the trickiest so I'm not so bothered about that.

I have installed the XBMC media centre software but it doesn't seem to work very well unless I am doing something wrong. I have figured out how to create a music library and it will play the MP3s from that, however, the following things don't appear to be in that:

 - No way of shuffling (playing random songs)
 - No positioning bar (for jumping to a certain point in the track)
 - No next/previous/rewind/fast-forward etc
 - No volume control or mixer (the audio is distorted as it is too loud and needs turning down in the XBMC settings).

It is not very useful for playing DVDs either. Firstly, the only way of playing DVDs is a file manager setup where you have to navigate to the individual VOB files. Doing so causes XBMC to exit without warning or any error message.

I have also tried MythTV but that doesn't seem to have any way of playing music or videos and Watch TV doesn't work because it doesn't like my TV Tuner card.

Should I stick to XBMC or is there a better option anyone could recommend?

My vital stats:

```
garyreggae@garyreggae-mediacentre:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:05.0 Network controller: RaLink Device 3060
03:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
03:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
garyreggae@garyreggae-mediacentre:~$ 

```

Release 10.04 (Lucid)
RAM 3.4 Gb
CPU: AMD Athlon II X2 255 (x2)
HDD space: 856 Gb

Thanks for any suggestions! And sorry for the rather lengthy post.

---

### Post by GaryReggae on 2011-07-25
<BUMP>
Sorry, I still need help with this and I think it has been ignored.

---

