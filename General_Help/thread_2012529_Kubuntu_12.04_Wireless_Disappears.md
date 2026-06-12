---
title: "Kubuntu 12.04 Wireless Disappears"
date: 2012-06-29
forum: General Help
---

### Post by x C0MMAND0 x on 2012-06-29
Brand new install.

Went to "Additional Drivers" saw the broadcom wireless, installed it, rebooted everything was working fine.  Rebooted again, no wireless networks showing up.  I go to "Additional Drivers" and only my graphics card shows up...

I installed "b43-fwcutter" and rebooted and the wireless adaptor shows up.  Every few reboots it seems to disappear or get confused.

FYI currently no wireless is showing up or enabled, and here is a terminal output.  I don't see my wireless even showing up as a device!  Any thoughts/ideas?

Dell XPS M1330

```
brent@Poseidon:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GS] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

```

---

### Post by x C0MMAND0 x on 2012-07-02
Everytime I reboot my wireless adapter seems to disappear...any ideas?

---

### Post by x C0MMAND0 x on 2012-08-09
If i uninstall and reinstall broadcom-sta-common and broadcom-sta-source and ndiswrapper-* it works, but then when I reboot it doesn't work.

This isn't an issue at my office because I wire in, but it is a problem everywhere else.  Any ideas?

---

### Post by wildmanne39 on 2012-08-10
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by x C0MMAND0 x on 2012-08-10
Log attached.  Currently, the state of my laptop is with no wireless anything showing up; I am wired in.  If you would like I can do my "fix" to get my wireless drivers working and then repost the log, but they always disappaer after rebooting anyways.

---

### Post by wildmanne39 on 2012-08-10
Hi, is this a pci card? you are not trying to get bluetooth wireless to work are you?

If this is an internal pci card then it is not showing at all which means possibly it is getting disabled in the bios, or the card is going bad or is loose but there is not anything else we can do with a hardware issue.
Thanks

---

### Post by x C0MMAND0 x on 2012-08-10
Internal PCI, BIOS settings are all correct.  I just ran the an uninstall of broadcom-sta-common broadcom-sta-source ndiswrapper-common and then immediately installed them, rebooted and viola, wireless is working.  Check out the same script I ran after rebooting.

If I reboot again though, it will not work!

New version of updated script attached.  Also, here's lspci output

```
brent@Poseidon:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GS] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)

```

---

### Post by wildmanne39 on 2012-08-10
Hi, that is strange please try:
```
sudo su 
echo wl >> /etc/modules 
exit
```
Reboot
Thanks

---

### Post by x C0MMAND0 x on 2012-08-13
That seems to have worked...I'll keep you posted after a few reboots to see is the changes stick.

Care to explain the sytax?  I haven't seen echo used like that before so I'm honestly not sure what that command did - though I'm curious.

Thank you.

---

### Post by wildmanne39 on 2012-08-13
Hi, the command makes the wl driver load at boot, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by x C0MMAND0 x on 2012-08-15
So, after a few reboots it quit out again.  I re-ran the script and rebooted and it did not work...I'm not sure what's going on why it would show up sometimes and not other times.  Having a non-working wifi connection is not really an option for a laptop.

Any suggestions or anything else I can try or remove or reinstall or anything?

---

### Post by wildmanne39 on 2012-08-15
Hi, I suspect something else is going on.

Maybe a hardware failure or bios issue.

When you can not connect copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by x C0MMAND0 x on 2012-08-29
It turns out it is a physical hardware issue - I did more testing and it is physical.  I will make this thread as resolved and look into a good usb wifi adapter that plays nicely with linux.

Thank you for your help.

---

### Post by wildmanne39 on 2012-09-01
Hi, your welcome!

---

### Post by HtmlGifted on 2012-09-01
found that 12.04 upgrade is not a good version to do upgrade with get half way through the install and the system can't shut things down to finish the proper install and then after restart it quits... 

got this fixed by going back to original distro.. and burnt a 12,04 install cd... 

so hay take that upgrade,.....

---

