---
title: "Wireless Help, loosing hope"
date: 2009-11-04
forum: General Help
---

### Post by jubop on 2009-11-04
So I just installed ubuntu 9.10 on my friends Toshiba Satellite A200-25v and cannot for the life of me get the wireless card working. I got ndiswrapper, and ndisgtk, and i've tried a couple of drivers one from the toshiba website for this model but there's no .inf file to install once I get to installing the driver from Windows Wireless drivers.

I managed to install these drivers properly but they then said that there was no hardware to match so i guess the drivers were wrong:
[http://tinyurl.com/265hyw](http://tinyurl.com/265hyw)
and
one from the acer.com website.

I'm sure I need the driver from this site 
[http://www.atheros.cz/download.php?atheros=AR5007EG&system=1](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1)
(xp32-6.0.3.85.zip for Atheros AR5007EG) but cannot download at all from this site evrytime I tried it kept timing out and not downloading.

So finally I just need help with the appropriate driver can anyone find it for me or help me with this it's my friend's laptop and not mine so I'm at my wit's end here trying to help her out, I feel so bad.

I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=678953](http://ubuntuforums.org/showthread.php?t=678953)

and I'm also not sure if I did a couple of the beginning steps right such as
> get rid of a couple of modules. Blacklist ath_pci in /etc/modprobe.d/blacklist and disable ath_hal in /etc/default/linux-restricted-modules-common. Then remove the modules.

No idea what this means but when I typed
> echo "Blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
sudo gedit /etc/default/linux-restricted-modules-common
into terminal the file cam up blank so I'm assuming I don't have them.

I'm just stuck here and I'm not the most knowledgable at Ubuntu, I get around so any answers could please be spelled out in as simple language as possible would be so wonderfully appreciates.

Thanks for reading all this I hope it doesn't sound like a rant or anything I just wanted to include everything I've tried so I don't get pointed towards directions I already tried following thanks :)

---

### Post by michy99 on 2009-11-04
See if this driver will work.

[http://www.nodevice.com/driver/AR5007EG/get64240.html](http://www.nodevice.com/driver/AR5007EG/get64240.html)

Unzip the file and then unzip the zip file inside that. There are two inf files, hopefully one will work.

---

### Post by wildweathel on 2009-11-04
First, even though ndiswrapper has a long and venerable history in the Linux world (thus many, many tutorials floating around the web), it's pretty much obsolete now as real Linux drivers have taken over.   Generally it's best to confirm that native drivers aren't available before trying ndiswrapper as a last-ditch effort to get it working.  For troubleshooting purposes, can you disable that driver (maybe uninstall ndiswrapper all together if your not sure) and un-blacklist ath_pci (by removing the blacklist line you added.  gksu gedit /etc/modprobe.d/blacklist)?  

(Besides, those 4th-party download websites are downright *scary*.  No wonder the Windows world is so plagued by viruses...  This isn't Windows, we can do better than that.)

Second, we need to know exactly what kind of wireless adapter you have, not who sold you your laptop, but what's inside.  The best way to find this is run lspci in a terminal and look through the output.  Note the ID of the wireless device is, and run "sudo lspci -vv -s *ID*".  For example, on my computer, "sudo lspci -vv -s 04:00.0" gives

```

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1000
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at b0200000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number *[removed]*
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

```Paste the whole thing (except for serial number or MAC address if your paranoid).  The slot ID number will probably be different.  I know that the thread you linked to mentions that lspci was wrong, but that was on Gutsy, four releases ago.  

Finally, please have some hope.  I poked around the madwifi project website, and it looks like they have a driver.  (can't be sure until I see the lspci; can't be *real* sure until it works)  If they do, it should be possible to get that radio working--if the working driver isn't in Ubuntu yet, it'll be a bit of work, but entirely possible.

madwifi's set-up guide is here: [http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)  and a more Ubuntu-specific one is here: [http://madwifi-project.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi-project.org/wiki/UserDocs/Distro/Ubuntu) .  

The Ubuntu guide is out of date and the other one does some things that are bad for Ubuntu.  Someone needs to adapt the instructions for Ubuntu.  (checkinstall rather than "sudo make install"; deal with packaging conflicts with Ubuntu's driver package so that updates don't wipe out the new driver, that sort of thing).  I'm pretty sure I can do it, but it's late now (quarter to midnight), so not right now.

Thanks for the interesting problem.  Later.  ):P

---

### Post by jubop on 2009-11-05
thanks for the quick replies evreyone I'll get working on it but sinces it's not my laptop I probably can't get to it until this weekend so I won't be able to give more info til then, just thought anyone who's looking would want to know.
As soon as I get my hands on the laptop I'll post the relevent info.

Thanks again, starting to regain hope.

---

### Post by jubop on 2009-11-06
so I ran sudo lspci -vv -s 5:00.0 and come up with this:
```
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7128
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f8000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
		Vector table: BAR=0 offset=00000000
		PBA: BAR=0 offset=00000000
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel modules: ath5k
```

so now what should I try madwifi do you think it'll support it?? also I installed wicd so I don't have network manager and can't figure out how to switch back to it I tried installing it from terminal but it wouldn't install since wicd is installed and if I uninstall wicd then I have no internet access, anyway this might be irrelevant but I just want to know if it matters at all once I hopefully finally get this card up and running.

Thanks

---

### Post by jubop on 2009-11-07
So update: I managed to get the driver recognized (using madwifi) and activated briefly but it still couldn't detect any wireless networks, but I'm in an apartment building and have another laptop next to me connected to my wireless network, so that's not right, tried to reboot and see if it would then find the networks and poof wireless card not recognized :(. 

Please someone help me I'm also starting to think I've messed around with this too much and should just do a blank reinstall of ubuntu and start trying again??? ANYONE have an idea. I'm begging here.

---

### Post by coffeecat on 2009-11-07
> **jubop said:**
> 
```
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

snip


```

I think I've got some good news for you. According to lspci my EeePC has the Atheros AR5001 rev 01 adapter. And wireless works out of the box in 9.10 (NBR) - WPA-PSK too - very reliably. No wicd, no ndiswrapper, no madwifi, no blacklisting anything, no mucking about. So it should work for you too.

Try this. Boot up with the live Karmic CD. At the desktop, click on the Network Manager applet icon, select your network and put in your WPA/WEP key when prompted. Does it work? If so, perhaps a fresh install may be in order.

Good luck!

**Edit:** just noticed this at the bottom of your lspci output:

> Kernel modules: ath5k

That's the kernel driver for the wireless device. The driver comes in the kernel.
And lspci on my machine says 'Kernel driver in use: ath5k'

Sounds optimistic.

---

### Post by jubop on 2009-11-07
so now I'm just baffled I ran karma from the livecd and the wireless connected flawlessly, no issues whatsoever, so I did a reinstall since I figured at that point I'd messed with the system enough and after reinstall no wireless access. 
so now I'm just wondering anyone can help me from scratch in setting it up???

---

### Post by jubop on 2009-11-07
SOLVED!!!!!!!!!!!!!!!! Not sure if it's a bug but if anyone else has this issue it's in etc/modprobe.d/blacklist-ath_pci.conf for some reason ath_pci is blacklist, just unblacklist it with #blacklist ath_pci restart the computer and voila wireless is up and running.

The answers are always the easy ones lol.

Thanks to anyone who tried to help.

---

