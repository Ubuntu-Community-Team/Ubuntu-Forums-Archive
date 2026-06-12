---
title: "Hi, I'm new to ubuntu and my computer is semi rejecting it."
date: 2009-12-01
forum: General Help
---

### Post by Winged56 on 2009-12-01
So I've installed the latest version of ubuntu on my desktop. My desktop is a couple years old I think I got it in Christmas 2005. It's an Emachines and I'm not sure what make and model but I'm sure I could get it with a little work. Anyways onto my problem. My problem is that everytime my computer starts to do a little hard work it glitches and freezes up along with a weird screen. It sorta looks like those hidden picture pictures. So this has happened when I try to watch a video, play a flash game, or use my computer too much such as having too many programs open or having too many tabs open in firefox. I've never experienced this problem with this computer before. I was running Windows XP before this and did not have any problems. Please help? Thank you.

---

### Post by ed-koala on 2009-12-01
Open a terminal and type in the following command and post the output here.

```
lspci
```

This will tell us about your system.  Sounds like a graphics driver issue at first glance to me.

---

### Post by Winged56 on 2009-12-01
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)


Btw I should mention that only when I tried to watch videos that were on my harddrive did I have problems. I actually watched an episode of chuck earlier just fine on a streaming website.

---

### Post by zaphod777 on 2009-12-01
Sounds like you might need to install the media extras to play the video files you want to play

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

it could also be that the machine or HDD is quite old and not able to play high definition videos.

I know when I had an older laptop I couldn't play mkv files because my machine was too slow. 

you might try downloading some lower res videos that are formated for IPOD video or psp.

---

### Post by ed-koala on 2009-12-01
Hmmm, I have some suspicions, but I'll need to ask a few more questions to narrow this down.

You mentioned hard work. Does the problem happen when NOT doing something video related?  Such as just too many programs open (but none a video program or one using flash)?

How much memory does your PC have?

Go to System - Administration - Gparted. (If it isn't there, you can install gparted using Synaptic).  Look around for linux-swap partition and tell me what size it is.

Do you have restricted video drivers installed?  Go to System - Administration - Hardware Drivers to check.

---

### Post by sloggerkhan on 2009-12-01
VIA graphics can be troublesome. Last I checked there were multiple drivers from different sources, none of which quite worked how I'd have liked. Though that was a while ago.

---

### Post by Winged56 on 2009-12-02
The linux swap is 1.96 gigabytes. My ram should be at like 1 gig. I shouldn't have a problem with hi-res considering I watched the same videos back on windows xp just fine with no problems. I have no proprietary drivers in use on the system. And that is pretty much verbatim. And it does happen when I'm not watching videos. Like I said flash games cause problems and also when I was refreshing on this site I got glitched out. And I was only running firefox.

---

### Post by ed-koala on 2009-12-02
I think this is what you need:

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

All the things you mention are video related. Including refreshing the browser screen. So, getting your drivers straightened out should do the trick.

---

### Post by Winged56 on 2009-12-02
Well it says I've already got open chrome downloaded and installed. Should I edit it in some way?

---

### Post by Winged56 on 2009-12-02
Ok I see what my problem is and what to do but how to I edit?

---

### Post by running_rabbit07 on 2009-12-02
I don't know if this would be helpful, but have you installed ubuntu-restricted-extras? It is in Synaptic Package Manager or you can enter this command in a terminal. ```
sudo apt-get install ubuntu-restricted-extras
```

This installs, flash, codecs and fonts that weren't included during the install because of legal reasons.

---

### Post by ed-koala on 2009-12-02
Go to that link I gave you above, and scroll down to manual installation (no, we are not going to manually install) ... go to number 3, editing xorg. Make sure it says openchrome like it tells you.

Now, there are some Via proprietary drivers that may help you, but I'm just speculating here.  Go to this page:

[http://www.via.com.tw/en/support/drivers.jsp]("http://www.via.com.tw/en/support/drivers.jsp")

Put in:

1. Linux - Current
2. Ubuntu 9.04
3. Integrated Graphics
4. K8M800/K8N800 UniChrome Pro

Download and install the driver.  Hopefully that'll clear up all your troubles. If not, I'm not sure what to do.

---

