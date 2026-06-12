---
title: "Unable to install windows xp"
date: 2011-05-21
forum: General Help
---

### Post by kandreas87 on 2011-05-21
I am really sorry if I'm posting this in the wrong section of the forums (which I probably am...).. 
However, let me cut to the chase. I installed Ubuntu 10.04 in January on my old stationary computer (which is 6 years old..something like that anyway..). After trying it out, I realized that linux is not the optimum operating system if I'm having a small kid, which enjoys watching youtube.. So here I am, trying to install windows xp, which is totally impossible.. 

So, what happens: As I boot up the computer, the usual text is shown "Press a key if you want to boot with cd ... " So I press a key, where a new text is shown.. "Setup is inspecting your hardware configuration". At this point my mouse and keyboard starts flashing their LED's in an unsynchronized manner.. And I'm caught at this stage..

What I have done: 
*) Rebooted compuiter with ubuntu live cd.. formatted the whole hard drive in NTFS / FAT16 / FAT32. No luck..
*) Removed the battery on the motherboard, which I assume (and hope) resets the CMOS. I did not see a CMOS jumper.. might just been that I did not search hard enough.. No luck here either though..

Any help would be greatly appreciated.

Short info: 
I had windows XP prior to installing linux. And no hardware changes has been applied during the time with linux. Tried several versions of XP (And also win 7). 

I know that I haven't let you know anything about the computer generals.. that is because I do not know much about it.. I built it 6 years ago.. but I guess the memory fades as you get older =) 

Anyway, thanks on advance!

---

### Post by oldfred on 2011-05-21
Windows installs to empty space if a primary partition is available or to a NTFS partition with the boot flag. Did you put a boot flag on the NTFS partition and is it a primary partition?

---

### Post by Thewhistlingwind on 2011-05-21
> **kandreas87 said:**
> 

Short info: 
I had windows XP prior to installing linux. And no hardware changes has been applied during the time with linux. Tried several versions of XP (And also win 7). 

I know that I haven't let you know anything about the computer generals.. that is because I do not know much about it.. I built it 6 years ago.. but I guess the memory fades as you get older =) 

Anyway, thanks on advance!

Post the output of lspci, now. Also, like the guy above said, check your flags.

---

### Post by kandreas87 on 2011-05-21
Hey guys, thanks for you replies. To the first question; I did put the boot flag on the NTFS partition, and it was the primary partition as well..

To the request; here is the output of lspci; 
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0d.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
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
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

---

### Post by Hedgehog1 on 2011-05-21
You can use gparted to 'wipe the drive' (really just give it a nice, empty partition table and then let XP take it form there)

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

Run gparted, and do this:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]

Then install XP on this 'clean' drive.

***The Hedge***

:KS

---

