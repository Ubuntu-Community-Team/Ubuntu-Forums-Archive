---
title: "Serious OS lag without internet"
date: 2011-05-29
forum: General Help
---

### Post by pengper on 2011-05-29
So I recently installed Ubuntu on my laptop- an eMachines D620(AMD 64bit 1.6GHz, 512KB L2 cache, 800MHz FSB, 1gb RAM) previously running vista basic- and it asked me to connect it to the internet when installing, so i went downstairs and connected it to the wifi (i was happy with this because windows had screwed up and refused to connect some months ago). 

As soon as it was set up and installed I took it back up to my room and ran it for the first time. And it lagged. Oh, how it lagged. Every action had about a 3 second delay- usually happened eventually, but had this unbelievable lag. Only the mouse moved instantly- even hover-overs lagged.

My first thought was that it was the crummy laptop couldn't take linux, which was a bit of a bummer. But I went downstairs, connected it to the internet, and downloaded firefox. Instantly when firefox opened bang! Everything worked, real time. Closed firefox and it all worked like a dream- until I disconnected from the wifi. Gone again- instant lag.

So what's going on? It's about a fortnight later and it's still exactly the same. I love Ubuntu and almost everything about it- but I'd just love to actually move my laptop?

Thanks.

---

### Post by linuxinstalledfromhdd on 2011-05-29
You should use a hardwired connection to the internet if you are going to install Ubuntu from a disc or usb stick. 

Do you have an Ethernet cable you can use?

---

### Post by pengper on 2011-05-29
I do- it never worked on Windows, so I never thought to use it now...

It's a bit impractical, as the router resides under my dad's desk, and the only free Ethernet cable in the house is about a metre long :P

Even so- that gives me an alternate means to connect, but will it sort my problem? The problem only occurs when offline...

---

### Post by linuxinstalledfromhdd on 2011-05-29
Yes, if you are going to install Ubuntu it is best to do it from a hardwired connection. That way you don't have to worry about errors, or lag, or any other potentially nasty problems while getting a perfect installation completed.  After you get it completely installed, you can play around with wireless, and hopefully get that running.

---

### Post by pengper on 2011-05-29
Hmmm... Well I've already finished the install- and I'm not entirely sure there weren't any errors. How would I go about repairing this? Wouldn't have to reinstall, would I?

---

### Post by linuxinstalledfromhdd on 2011-05-29
Well if you got it to install, and you are experiening zero problems, I wouldn't worry about it.  If you have a problem, try using a hardwired connection to install Ubuntu from now on.

---

### Post by pengper on 2011-05-29
I will, thanks! I do have the offline problem- do you know how i could repair that in some way?

---

### Post by wildmanne39 on 2011-05-29
> **pengper said:**
> I will, thanks! I do have the offline problem- do you know how i could repair that in some way?HI, type this into a terminal
```
lspci
```and let us see what hardware you have, I know you said you only have 512 ram. Did you activate your video card driver? It is strange that it is only when you are not connected to the internet, I can tell you that you system is not very strong but is should run ubuntu ok as long as you do not use the cube or effects.

---

### Post by 3rdalbum on 2011-05-29
When your computer is not connected to the internet and is experiencing the lag problem, what does the System Monitor say about your CPU use and about what program is using the CPU so much?

Hit the Windows key and start typing 'system monitor'. It will be the first item that appears. Click it and look at the Processes tab. Click on the "CPU %" column to sort the programs by CPU use, and find the one that's got the highest number in that column. Tell us what the name of it is. You could also try right-clicking it and choosing "End Process", but make sure that all your open documents are saved before doing this.

---

### Post by pengper on 2011-06-02
Well, I did the lspci, and I got this:

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

ouch.

as for performance, I would have taken some screenshots but I think the screenshot tool might have augmented the shown results. The CPU skyrocketed 50 seconds before I took the screenshot- I'm certain that's much sooner than when I disconnected.

One thing I did notice is that the Swap of 0.6% rose instantly to about 2.5%, before finally settling at 7.8%. This is strange because it had been steady at 0.6% before. It's now at 10.9%, and I'm obviously reconnected.

It doesn't behave like it's merely running out of memory- it's a regular lag; not just sticky and used up. It's not just freezing- it's like it's meant to do it. It's rather absurd...

The moment I reconnected the computer responded to my commands instantly again.

I took a couple of *free -m*s while I was at it. First when I was connected:
```
             total       used       free     shared    buffers     cached
Mem:           747        722         24          0         63        163
-/+ buffers/cache:        494        252
Swap:          764         83        681

```

And then without a connection:
```
             total       used       free     shared    buffers     cached
Mem:           747        734         12          0         64        174
-/+ buffers/cache:        496        250
Swap:          764         82        682

```

So, as you can see, it's not a matter of memory. It changes instantly when the connection comes or goes. Anyone have a clue?

---

