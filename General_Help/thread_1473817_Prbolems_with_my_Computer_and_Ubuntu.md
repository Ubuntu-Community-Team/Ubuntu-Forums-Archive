---
title: "Prbolems with my Computer and Ubuntu"
date: 2010-05-05
forum: General Help
---

### Post by pedjo386 on 2010-05-05
Hello guys! 

I am new here and I have  ubuntu version 9.10 and a computer HP Pavilion, 
the computer is 
Intel(R) Pentium(R) 4 CPU 3.00 GHz
Nvidia Geforce 6200 
and it has 1 GB of ram, 

I am a new user of ubuntu and I have a lot of problems. 
My older brother also  has  ubuntu and he has no problems with it, 
his friends have it as well and they heve no problems.

The problems are as follows:

first:
Speakers are mounted on the back of the computer and they work ok
but when connected in the front of the computer  
headset and microphone are not working.
There is neither sound in head set nor the microphone is working.

second:
At the beginning when those brief drums that is prompted for a user
and single log in jingle ... there is static music instead,
(SHHHHHHHHH sound)
which is more high-toned bass BN BN
So, no drums and log in jingle, but SSHHHHHHHH
It does not matter if I have speakers or headset,
inserted at the back of my box or at the front of my box.

I love a good game, and I installed Open Arena, 
but it is the same as at the beginning!
Only static sound (SHHHHH), in all frequencies ...
The game works, but the sound is static on the speakers, again,
it does not matter if I have speakers or headset,
inserted at the back of my box or at the front of my box.

third:
The webcam is working on cheese, but not in skype.

fourth:
When I go out for 30 minutes or more my computer goes to standby mode, 
but when I get back I can't seem to make it work so I have to restart it manually, 
(holding power button for 5 seconds to shut it down)
I don't think that is good for computer.

fifth:
A lot of times I am watching a movie or some pictures 
and the computer freezes and it is very annoying.
Again, I have to restart it manually, 
(holding power button for 5 seconds to shut it down)


I know this might be a bit too much for one post, but I am new to ubuntu,
and I have to start somewhere.

Kind regatds, Pedjo386

---

### Post by okplayer02 on 2010-05-05
well for the webcam issue with skype i had to issue this command from terminal to get mine to work

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
 
then try to see if u can view ur cam from skype

what kind of sound card do u have is it 5.1 or just a regular 2 channel sound card give little more information.

---

### Post by pedjo386 on 2010-05-08
I found this in lspci -vv for my sound card.

```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 2a09
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 16 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at ccffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```


```
03:03.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 4842
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (63750ns min, 63750ns max)
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at cffff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```

That command really works. Is there a way to make a short cut so, so I don't need to start skyp from my terminal

---

