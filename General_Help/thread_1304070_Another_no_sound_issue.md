---
title: "Another no sound issue"
date: 2009-10-28
forum: General Help
---

### Post by sickly on 2009-10-28
Ive Been sitting here for three hours trying to figure this out going from thread to thread but no luck. I have a hp pavillion dv4-2045dx notebook that has 9.10 currently installed. Ive tried 9.04 to try to get this sound issue to work too but no go.
heres what it says for "alsamixer"

Card: HDA ATI SB                                                             
&#9474; Chip: IDT 92HD71B7X                                                          
&#9474; View: [Playback] Capture  All                                                
&#9474; Item: Master [dB gain=-10.50]



and "lshw -C multimedia"

*-multimedia            
       description: Audio device
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:19 memory:f2410000-f2413fff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:f2500000-f2503fff

for the hell of it "lspci"

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
01:05.1 Audio device: ATI Technologies Inc Device 970f
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)



Thanks for any replies. I feel like a zombie

---

### Post by fluffman86 on 2009-10-28
well, for me, deleting ~/.pulse-cookie worked.  It was then recreated and pulse audio started working fine again.

a few other things to try:
make sure all of your sound levels are up and not muted by running alsa-mixer in terminal
alt+f2 and run gnome-volume-control and check settings there.
create a new user and see if sound works for them.  That's how I discovered the .pulse-cookie file, but maybe you need to remove some pulse folders in .local or somewhere else as well.

---

### Post by sickly on 2009-10-28
thanks for the reply. I tried deleting the .pulse-cookie but it did nothing. But now i dont have the cookie lol.

---

### Post by fluffman86 on 2009-10-28
What about other users? Do they have sound?

---

### Post by sickly on 2009-10-28
no, i loged in as root and ther was no sound

---

### Post by sickly on 2009-10-30
I have finally found the solution to this problem. I had to open /etc/modprobe.d/alsa-base.conf  and add these lines to the end

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1 
then do a reboot and my sound is fine.

then did a reeboot and my audio was fine

---

### Post by brhokla on 2009-12-06
I have this same computer and I'm trying to get this to work but I'm a new using to Ubuntu.  Do you have a step by step on how to do this? Thanks

---

### Post by kage52124 on 2009-12-07
Hi, I'm also suffering this problem and I tried your solution, but it gave me some errors about removing hardware... did you experience this as well?

Same computer running Kubuntu 9.10 via WUBI installer

---

### Post by belboz on 2009-12-07
I had a sound issue on a relatives PC after he did the 9.10 upgrade himself.

I noticed on his system that grub was still only showing the older 9.04 kernels in menu.lst

Also noticed that an update-grub would list the new kernels, but it wasn't changing the menu.lst file.

So I renamed menu.lst to menu.lst.backup

reran update-grub (sudo update-grub) 

The new menu.lst had the proper entries in it now for the new kernel that was installed during the distro upgrade.

I did have to copy the entry for Windows from menu.lst.backup and paste it into the new menu.lst .  If your not multi booting this probably isn't an issue.

Rebooted and the proper kernel was loaded and sound worked again.

So the core problem for him was the distro upgrade from 9.04 to 9.10 failed to update the grub menu.lst file

---

### Post by kage52124 on 2009-12-07
Status update: I was able to get the sound working with two of the lines listed above:

> 
#Keep snd-pcsp from beeing loaded as first soundcard
#options snd-pcsp index=-2
#alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
#options snd-hda-intel enable_msi=1
This allowed me to get the sound working without the prior error about hardware not working.  Once again this is for Kubuntu 9.10 but I imagine this isn't dependent on the desktop environment.

---

### Post by pab39193 on 2010-01-02
> **sickly said:**
> I have finally found the solution to this problem. I had to open /etc/modprobe.d/alsa-base.conf  and add these lines to the end

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1 
then do a reboot and my sound is fine.

then did a reeboot and my audio was fine




Thanks, works great know.

---

### Post by abqhandyman on 2010-01-02
before all sound issues in the upgrade comes a simple gotcha: that the upgrade sets the sound to zero and the volume icon gets moved to the corner.  One has to click the muted volume icon in the far right corner and set it to some non-zero setting.  Lots of peoplehave sound issues upgrading to 9.10.  I've gone back to 9.04.  Cheers,

---

