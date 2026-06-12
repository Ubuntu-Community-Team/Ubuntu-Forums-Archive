---
title: "Ubuntu 11.10 Random Freezing"
date: 2011-10-19
forum: General Help
---

### Post by CrusaderAD on 2011-10-19
Can someone shoot me some instructions on checking the system logs for debugging what's happening here? Are they the logs in /var? Here's the system specs:

Intel® Core™2 Duo CPU E7300 @ 2.66GHz × 2 
RAM 2.0 GiB

Graphics are unknown, but I think it's an ATI card. I have a feeling this is the culprit, however I've been running Ubuntu on this system for the past 3 releases.

---

### Post by Blaqksheep on 2011-10-19
You can see your GPU in System Settings > System Info > Graphics.

Next time your system freezes, try CTRL + ALT + Backspace.  That should be the key combo to restart X.  If that unfreezes you, you'll know your culprit.

---

### Post by dh003i on 2011-12-07
I have very similar problems, random freezes in clusters of a second or so. It is very frustrating.

Except for the GPU, all of my components are server-grade:

Motherboard: Supermicro H8DG6-F
CPUs: 2 x AMD Opteron 6128
RAM: each CPU socket has 4 x 8 GB RAM sticks. RAM is KVR1333D3LD4R9S/8GEC 8GB 1333MHz DDR3 ECC Reg CL9 DIMM Low Voltage Server Memory
GPU: Sapphire Radeon FLEX HD6950 2G DDR5 PCIE (ATI Radeon HD6950)

I'm using the bundled Ubuntu Catalyst standard drivers (no the bundled newer experimental Catalyst drivers).

---

