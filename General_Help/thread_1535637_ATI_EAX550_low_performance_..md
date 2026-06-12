---
title: "ATI EAX550 low performance ."
date: 2010-07-21
forum: General Help
---

### Post by j0shm4n on 2010-07-21
Hello , i recently switched from windows to ubuntu 10.04. Im still newbie but here is my problem . I installed Alien Arena from synaptic 20 min ago and started it but it runs like slideshow . I once screwed up my OS yesterday so i don't want to do it again . Can you please tell me what to do . Should i install drivers from ATI website ? Here is info for my video controller: 
02:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
    Subsystem: ASUSTeK Computer Inc. Device 0155
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: Memory at fdde0000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>

---

### Post by cascade9 on 2010-07-21
ATI dropped support for the X550 (and various other ATI video cards) a fair while ago. 

The only drivers that will work are the open source drivers, and they should be installed by default.

---

### Post by j0shm4n on 2010-07-21
So there's nothing i can do about improving performance in some games ?

---

### Post by j0shm4n on 2010-07-21
bump

---

### Post by Mark Phelps on 2010-07-21
> **j0shm4n said:**
> So there's nothing i can do about improving performance in some games ?

Quit bumping ... the answer is NO.  

Driver support with hardware 3D acceleration was dropped by ATI over a year ago for your card.

What you have now in the open source drivers is all that is available.

---

### Post by j0shm4n on 2010-07-21
did you read my question ? im asking can i improve my FPS in games somehow ..  i did install these drivers and this did improve performance in alien arena but it's now what i expect .. are there any other ways to get more fps ?
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on RV370
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20

---

### Post by j0shm4n on 2010-07-21
Also i just tried to run Counter Strike under wine and i get this message when trying to start it.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f348,0x00000000), stub!
Can anyone help me ?

---

