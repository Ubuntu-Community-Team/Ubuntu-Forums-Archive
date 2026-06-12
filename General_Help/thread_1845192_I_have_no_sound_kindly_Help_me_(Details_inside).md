---
title: "I have no sound kindly Help me (Details inside)"
date: 2011-09-16
forum: General Help
---

### Post by asifnaz on 2011-09-16
I have two sound Cards , One is a built in (C-Media Electronics Inc CM8738 ) which is broken since it is built in I can&#8217;t remove it .
   
  Second one is (ESS Technology ES1969 Solo-1 Audiodrive (rev 01) ) which is working 
   
  But I only hear sound like 3 out of 10 times (only when alsamixer shows ESS Solo )
   
  **Here is output for lspci:    **
   
  

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 21)
  00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
  00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
  00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
  00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
  00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
  00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
  00:0e.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
  01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 21)

```  and output for nano /proc/asound/cards
   
   ```

0 [CMI8738        ]: CMI8738 - C-Media CMI8738
                        C-Media CMI8738 (model 37) at 0x9800, irq 10
   1 [Solo1          ]: ES1938 - ESS ES1938 (Solo-1)
                        ESS ES1938 (Solo-1) rev 0, irq 5

```  I wanted to remove non-working CMI8738 lines from /proc/asound/cards but I can't Edit these lines even with root powers . 
   
  How can I tell ubuntu to Detect and connect to ES1938 - ESS ES1938 (Solo-1)  sound card 
   
  And how to blacklist Broken cmedia 8738..?
   
  I am a new user so I will really appreciate you provide me step by step solution

---

### Post by zero2xiii on 2011-09-16
Hay,

Most BIOS's will allow you to disable onboard hardware. Have you tried looking if you can disable the on board audio in bios? Or set the primary/default card the the PCI slot?

Cherz

---

### Post by asifnaz on 2011-09-18
For those looking for same problem:

echo "blacklist snd-cmipci" >> /etc/modprobe.d/local.conf




worked . Credit to the guy on Debian forums

---

