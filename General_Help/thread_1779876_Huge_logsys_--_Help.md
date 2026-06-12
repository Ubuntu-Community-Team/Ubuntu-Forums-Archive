---
title: "Huge logsys -- Help"
date: 2011-06-11
forum: General Help
---

### Post by JCM_Pico on 2011-06-11
Hi there there is a problem in my pc that is writen in the logsys file and I cant understand what it is...
Can you give me some help?

```
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.586999] mmc0: Unexpected interrupt 0x04000000.
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587002] sdhci: =========== REGISTER DUMP (mmc0)===========
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587007] sdhci: Sys addr: 0xffffffff | Version:  0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587011] sdhci: Blk size: 0x0000ffff | Blk cnt:  0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587016] sdhci: Argument: 0xffffffff | Trn mode: 0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587021] sdhci: Present:  0xffffffff | Host ctl: 0x000000ff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587025] sdhci: Power:    0x000000ff | Blk gap:  0x000000ff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587030] sdhci: Wake-up:  0x000000ff | Clock:    0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587034] sdhci: Timeout:  0x000000ff | Int stat: 0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587039] sdhci: Int enab: 0xffffffff | Sig enab: 0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587044] sdhci: AC12 err: 0x0000ffff | Slot int: 0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587049] sdhci: Caps:     0xffffffff | Caps_1:   0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587053] sdhci: Cmd:      0x0000ffff | Max curr: 0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587058] sdhci: ADMA Err: 0xffffffff | ADMA Ptr: 0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587060] sdhci: ===========================================

```

---

### Post by JCM_Pico on 2011-06-11
bump

---

### Post by wildmanne39 on 2011-06-11
> **JCM_Pico said:**
> Hi there there is a problem in my pc that is writen in the logsys file and I cant understand what it is...
Can you give me some help?

```
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.586999] mmc0: Unexpected interrupt 0x04000000.
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587002] sdhci: =========== REGISTER DUMP (mmc0)===========
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587007] sdhci: Sys addr: 0xffffffff | Version:  0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587011] sdhci: Blk size: 0x0000ffff | Blk cnt:  0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587016] sdhci: Argument: 0xffffffff | Trn mode: 0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587021] sdhci: Present:  0xffffffff | Host ctl: 0x000000ff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587025] sdhci: Power:    0x000000ff | Blk gap:  0x000000ff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587030] sdhci: Wake-up:  0x000000ff | Clock:    0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587034] sdhci: Timeout:  0x000000ff | Int stat: 0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587039] sdhci: Int enab: 0xffffffff | Sig enab: 0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587044] sdhci: AC12 err: 0x0000ffff | Slot int: 0x0000ffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587049] sdhci: Caps:     0xffffffff | Caps_1:   0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587053] sdhci: Cmd:      0x0000ffff | Max curr: 0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587058] sdhci: ADMA Err: 0xffffffff | ADMA Ptr: 0xffffffff
Jun 11 09:20:09 weather-pirate-laptop kernel: [  154.587060] sdhci: ===========================================

```Hi, I dont think there is enough information there to tell if there is a problem or not. What exactly is happening? I am concerned that the kernel says pirate I have never seen one like that before.

---

