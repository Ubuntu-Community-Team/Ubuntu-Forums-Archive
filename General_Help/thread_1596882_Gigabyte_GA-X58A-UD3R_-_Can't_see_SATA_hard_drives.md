---
title: "Gigabyte GA-X58A-UD3R - Can't see SATA hard drives"
date: 2010-10-14
forum: General Help
---

### Post by moorsey on 2010-10-14
Hi all,

Have just got around to setting up a dual boot on my new PC, want to give some linux video editing stuff a whirl

Seems that the SATA controllers on my motherboard are not supported my the current kernel.  Have tried ubuntu 32/64bit 10.10 live CD and the latest gparted (as of today).  But no drives are seen at all.

I am running a hardware RAID on this motherboard, can't find any additional drivers for it on Gigabyte's website or with a Google search, sort of assumed it would just work, as my previous hardware RAID did.

Output of lspci is:

```
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:11.0 PIC: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 (rev 13)
00:11.1 PIC: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 (rev 13)
00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:15.0 PIC: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 5870 (Cypress)
03:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
08:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
08:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

I believe the device in question is "Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller"

Is there any way I can get this working?

Thanks

---

### Post by cascade9 on 2010-10-14
OK, this again (no insult to you moorsey, I've seen a few others ask similar questions)

You've hooked up your HDDs to the white ports, right? (labeled SATA3 6GB). Hard tell from teh specs on the gigabyte site, but it looks like the white port are run from the Marvell 9128 chip  (GSATA3_6, GSATA3_7) or the gigabyte sata2 chip (GSATA2_8, GSATA2_9).

The marvel chips are renowned for poor linux support, and while I'm pretty sure I've seen somebody say that they got the gigabyte sata 2 ports goiong, I havent seen it done myself, and I cant remember where I saw it. 

Try chaning over to the blue ports, those should be from the intel chipset (ICH10), and they should work. Well, apart from the hardware RAID bit. I didnt think that you could change hardware RAID controllers without some serious stuffing around. 

BTW, odd that your ICH10 SATA controller is apearing in lspci as an IDE controller. Did you switch to IDE mode in BIOS?

---

### Post by moorsey on 2010-10-14
sort of solved this, if I change the RAID to AHCI then Ubuntu can see the drives, but Windows will not work, alas!  I guess this setting needs changing before installing Windows, not a job I can be bothered with at the moment, but at least I know how to solve it

---

### Post by moorsey on 2010-10-15
thanks cascade9 and apologies for the dupe question, no insult at all, appreciate the reply!

Thanks for the info on the ports and Marvel, will bear that in mind when I re-build.  Along with what I found on the AHCI, there will be some way forward.

Thanks again

---

### Post by cascade9 on 2010-10-15
No problem.

It wasnt a dupe question actually, I just jumped to conclusions. ;)

---

### Post by Renée Jade on 2010-11-24
Ok, I'm having the same issue. I've got the GA-X58A-UD7. I've set up two RAIDs on the ICH10R, and I have my DVD drive and boot drive on the Gigabyte Sata 2 (or Marvel. I can not figure out which chip actually controls the white ports) controller. Does anyone know if there IS a driver for the controller? Has anyone gotten the secondary SATA controller on a modern X58 Gigabyte motherboard working with Linux, or do I have to move all my drives back to the southbridge? Thanks for any help.

---

### Post by moorsey on 2010-11-25
do you have everything set to AHCI in the BIOS?  Need to double check which ports I am using for what later on and will post back, I can never remember

---

### Post by RayVad on 2011-01-07
Hi Moorsey,

Did you solve this?
I presume you did set AHCI in BIOS for this GA-X58A-UD3R?

Regards,
Ray

---

### Post by moorsey on 2011-01-07
Ray,

Yes, for Ubuntu to work, just change your SATA ports to AHCI in the BIOS and reboot, works a treat.

If you have an existing Windows installation, then Windows will not boot after this change, but I found a way around this, copied below for reference:

> 1.Exit all Windows-based programs.
2.Click Start, type regedit in the Start Search box, and then press ENTER.
3.If you receive the User Account Control dialog box, click Continue.
4.Locate and then click the following registry subkey:
HKEY_LOCAL_MACHINE/System/CurrentControlSet/Services/sahci

5.In the right panel, right-click Start in the Name column, and then click Modify.
6.In the Value data box, type 0, and then click OK.
7.On the File menu, click Exit to close Registry Editor.
After this you’ll have to restart your computer, go to BIOS and enable AHCI. When you log in to Windows again, you’ll notice the installation of drivers for AHCI. Another restart will be required to finish the driver installation

Taken from [http://forums.tweaktown.com/gigabyte/39418-best-way-install-ssd-ahci-mode-790xta-ud4-windows-7-a.html]("http://forums.tweaktown.com/gigabyte/39418-best-way-install-ssd-ahci-mode-790xta-ud4-windows-7-a.html")

You may have to get these drivers downloaded first, can't remember if I had to install some, or if I just used the default Windows ones.  The above method worked for me, YMMV.

---

### Post by limeyd on 2011-02-15
OK so i just got this motherboard and created a raid1 volume but how do I get mount? I don't see it in disk utility as raid only as two disk marked as raid component. ANy help would be great.

thank you

---

### Post by moorsey on 2011-02-16
have you got AHCI enabled?

Mine "just works" with a RAID1 volume and AHCI enabled

---

### Post by limeyd on 2011-02-20
So ahci not raid? do i need madam installed or is it hardware raid? and which ports I have 2 seagate sataII drivers

---

### Post by moorsey on 2011-02-21
Both, see below screenshot

[[IMG]http://img716.imageshack.us/img716/1713/imag0319m.th.jpg[/IMG]](http://img716.imageshack.us/i/imag0319m.jpg/)

I have my 2 drives connected to the Marvell SATA3 ports, so GSATA 6_7 needs to be set to AHCI and the drives need setting up in whatever RAID you want in "SATA3 RAID config".

Then, you can install Ubuntu, no need for madam, all the RAID is handled in hardware.

Hope that helps!

---

