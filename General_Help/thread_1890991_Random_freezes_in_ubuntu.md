---
title: "Random freezes in ubuntu"
date: 2011-12-04
forum: General Help
---

### Post by ashgard on 2011-12-04
Hello,

I have experienced three total freezes in three days with ubuntu 11.10. It quite annoying because I have to reboot by holding the power button and I loose all my unstored data. Help would be appreciated very much.

I installed ubuntu 11.10 desktop edition (with unity). Formatted the whole drive, installed all updates and installed driver updates. Nothing else.

What can you advice me to do? Im not familiar with debugging such thing. I posted the output of lspci and /var/log/syslog.1 below. Hopefully you can use it. Should I run a memtest? All help is welcome :)

Thanks,
Ashgard

The output of lspci is:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
08:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
```

This is the output of /var/log/syslog.1:

```
Dec  3 23:36:18 ashgard-laptop dbus[790]: [system] Activating service name='org.debian.apt' (using servicehelper)
Dec  3 23:36:19 ashgard-laptop AptDaemon: INFO: Initializing daemon
Dec  3 23:36:19 ashgard-laptop dbus[790]: [system] Successfully activated service 'org.debian.apt'
Dec  3 23:36:19 ashgard-laptop AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Dec  3 23:36:19 ashgard-laptop AptDaemon.Trans: INFO: Simulate was called
Dec  3 23:36:19 ashgard-laptop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/d2e014889cf443f38e94ec3209cb7529
Dec  3 23:36:20 ashgard-laptop AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Dec  3 23:37:19 ashgard-laptop AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'rhythmbox')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Dec  3 23:37:20 ashgard-laptop AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/3d86077778c341ffac715718d987882d
Dec  3 23:37:24 ashgard-laptop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/3d86077778c341ffac715718d987882d
Dec  3 23:37:24 ashgard-laptop AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'rhythmbox')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Dec  3 23:37:26 ashgard-laptop AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/3d86077778c341ffac715718d987882d
Dec  3 23:37:26 ashgard-laptop AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'rhythmbox')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Dec  3 23:38:31 ashgard-laptop AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/3d86077778c341ffac715718d987882d
Dec  3 23:42:39 ashgard-laptop kernel: [ 1762.725263] iwl4965 0000:0c:00.0: Queue 4 stuck for 2000 ms.
Dec  3 23:42:39 ashgard-laptop kernel: [ 1762.725273] iwl4965 0000:0c:00.0: On demand firmware reload
Dec  3 23:42:39 ashgard-laptop kernel: [ 1762.725417] iwl4965 0000:0c:00.0: Request scan called when driver not ready.
Dec  3 23:42:39 ashgard-laptop kernel: [ 1762.725857] ieee80211 phy0: Hardware restart was requested
Dec  3 23:42:39 ashgard-laptop kernel: [ 1763.004969] iwl4965 0000:0c:00.0: Stopping AGG while state not ON or starting
Dec  3 23:42:39 ashgard-laptop kernel: [ 1763.004981] iwl4965 0000:0c:00.0: queue number out of range: 0, must be 7 to 14
Dec  3 23:42:59 ashgard-laptop kernel: [ 1782.620052] iwl4965 0000:0c:00.0: Queue 4 stuck for 2000 ms.
Dec  3 23:42:59 ashgard-laptop kernel: [ 1782.620061] iwl4965 0000:0c:00.0: On demand firmware reload
Dec  3 23:42:59 ashgard-laptop kernel: [ 1782.621055] ieee80211 phy0: Hardware restart was requested
```

---

### Post by bluexrider on 2011-12-04
did you recently upgrade the kernel? if so, boot into the one prior and see what the results are.

---

### Post by ashgard on 2011-12-07
I havent updated the kernel recently. I just have the ones that come with the install of ubuntu 11.10. 

I tried the two versions available: 3.0.0-12 and -13. Both crash. 

Just to be sure, I also did a memtest. No errors found.

Any ideas?
Thanks,
Ashgard

---

### Post by pretty_whistle on 2011-12-07
I had some freezes myself till I stopped using Chrome and Chromium.

---

### Post by 2F4U on 2011-12-07
Do the lines "Hardware restart was requested" indicate the times when it froze? If yes, was there network activity before the freeze such as browsing the web? Is there a pattern behind the freezes, such as always happens when application xyz is used?

---

### Post by ashgard on 2011-12-07
it freezes without any notification. Just nothing happens anymore.  The mouse won't move. No response from keyboard. And no signs that the computer is trying to do something. 

The network always has been active. Either a web browser or download tool.

Let me disable the network and disable wifi. I'll let you know the results.

Thx

---

### Post by Mark Phelps on 2011-12-07
I see that you're using a Mobility Radeon driver, so this is a laptop, right?  Have you noticed it running warm or hot?  Is that happening just before the freezing?

If so, you're one of the MANY affected by the overheating problem in 11.10.

The link below has a workaround for that:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

---

### Post by ashgard on 2011-12-08
> **Mark Phelps said:**
> I see that you're using a Mobility Radeon driver, so this is a laptop, right?  Have you noticed it running warm or hot?  Is that happening just before the freezing?


No I haven't noticed that. Once I booted the pc (it was off for 1 day so I could not have been warm/hot) and after 10sec of working it already crashed. So I think it is unlikely that this is the problem.

> 
Let me disable the network and disable wifi. I'll let you know the results.

For the last 15h or so, the system has been running without network and disabled WIFI. Guess what: it didnt crash. It seems the issue is with networking indeed. How to proceed?
- try running with network, no wifi but ethernet cable?
- reinstall/update network drivers?

Perhaps this is unrelated, but let me mention it anyway. Yesterday when I was working with the laptop I noticed that my system monitor was acting weird. The processes that are shown (for cpu, network, etc) are not updated properly. That is, when I move my mouse the plots keep updating, when I stop moving my move the plots also stop within 5 sec. The strange thing is that this also applies to my audio/video. As long as I move the mouse I hear/see everything as it should. If i stop moving the mouse, the audio/video stops? Can this have to do something with the issue above?

Thanks for your help!

---

### Post by ashgard on 2011-12-11
I dont know if the two issues I described in the previous chat can be related? But on the internet I found same situations where people had the same issue, at least with the continuously having to use the mouse/keyboard to keep the audio/video working. They used a (what they called) workaround:

1. Open terminal
2. Type: sudo vi /etc/default/grub
3. Change line GRUB_CMDLINE_LINUX_DEFAULT to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"
4. Save and exit
5. Type: sudo update-grub
6. Type: sudo reboot

The good news is that this solved my audio/video issue. Also I havent noticed any crashes yet. But I am only working with this nolapic_timer for 30min. At least I am glad I fixed the first part already.

---

