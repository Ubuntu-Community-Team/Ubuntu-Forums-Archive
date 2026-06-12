---
title: "Suspend broken by fixing Kobo usb problem"
date: 2012-04-22
forum: General Help
---

### Post by alanwalterthomas on 2012-04-22
This is about a problem getting my system to suspend properly after fixing a problem that kept by Kobo touch from working properly. I strongly suspect the problem has to do with getting libusb-0.1-4 via getlibs, but don't know how to fix the problem, or even how to revert it. Relevant log files below.

Kobo Probelem:
I had trouble getting my Kobo touch e-reader to work with Ubuntu after upgrading its firmware to 1.9.17. Upon connecting the usb cable it would show its "would you like to connect" dialog, but for only an instant. To connect I had to touch "connect" at exactly the right moment. It would then be recognized by Calibre, but after saving books to it, it would not process them correctly & hang. If I then plugged it into a Windows computer with Kobo Desktop (the proprietary software) & synced it, it would find the books. Less than ideal.

Kobo Fix:
I found an 'unofficial' 32-bit kobo-desktop .deb on the net. It works, but took a bit of tweaking on my 64-bit 11.10 install, as follows:
sudo dpkg -i --force-architecture kobo-desktop.deb
getlibs -p libzip1
getlibs -p libxml2
getlibs -p libpng3
getlibs -p libusb-0.1-4
sudo ln -s /usr/lib32/libz.so.1.2.3.4 /usr/local/Kobo/libzip.so.1

Result:
After this, my kobo connects normally and correctly processes loaded books.
However, I can no longer suspend the computer.

Suspend Problem:
Simply put, clicking on suspend drops the screen to a virtual terminal, the screen goes black for a few seconds, then it goes back to the desktop. Note that upon return to the desktop, no USB devices work at all (they're unpowered it seems) for a few minutes, after which they work normally again.
Here are the log files from pressing suspend to getting control of my mouse back:
Logs: auth.log kern.log pm-suspend.log syslog Xorg.0.log
auth.log
```

Apr 16 07:56:43 Desktop su[9521]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9521]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9521]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9521]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:43 Desktop su[9531]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9531]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9531]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9531]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:43 Desktop su[9546]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9546]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9546]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9546]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:43 Desktop su[9574]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9574]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9574]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9574]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:43 Desktop su[9584]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9584]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9584]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9584]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:43 Desktop su[9599]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9599]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9599]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9599]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:43 Desktop su[9612]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9612]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9612]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9612]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:43 Desktop su[9627]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9627]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9627]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9627]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:43 Desktop su[9642]: Successful su for alan by root
Apr 16 07:56:43 Desktop su[9642]: + ??? root:alan
Apr 16 07:56:43 Desktop su[9642]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:56:43 Desktop su[9642]: pam_unix(su:session): session closed for user alan
Apr 16 07:56:44 Desktop dbus[1153]: [system] Rejected send message, 4 matched rules; type="error", sender=":1.30" (uid=1000 pid=2214 comm="bluetooth-applet ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.7" (uid=0 pid=1459 comm="/usr/sbin/bluetoothd ")
Apr 16 07:57:05 Desktop su[10052]: Successful su for alan by root
Apr 16 07:57:05 Desktop su[10052]: + ??? root:alan
Apr 16 07:57:05 Desktop su[10052]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:57:05 Desktop su[10052]: pam_unix(su:session): session closed for user alan
Apr 16 07:57:05 Desktop su[10077]: Successful su for alan by root
Apr 16 07:57:05 Desktop su[10077]: + ??? root:alan
Apr 16 07:57:05 Desktop su[10077]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:57:05 Desktop su[10077]: pam_unix(su:session): session closed for user alan
Apr 16 07:57:05 Desktop su[10101]: Successful su for alan by root
Apr 16 07:57:05 Desktop su[10101]: + ??? root:alan
Apr 16 07:57:05 Desktop su[10101]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:57:05 Desktop su[10101]: pam_unix(su:session): session closed for user alan
Apr 16 07:57:05 Desktop su[10118]: Successful su for alan by root
Apr 16 07:57:05 Desktop su[10118]: + ??? root:alan
Apr 16 07:57:05 Desktop su[10118]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:57:05 Desktop su[10118]: pam_unix(su:session): session closed for user alan
Apr 16 07:57:05 Desktop su[10133]: Successful su for alan by root
Apr 16 07:57:05 Desktop su[10133]: + ??? root:alan
Apr 16 07:57:05 Desktop su[10133]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:57:05 Desktop su[10133]: pam_unix(su:session): session closed for user alan
Apr 16 07:57:05 Desktop su[10146]: Successful su for alan by root
Apr 16 07:57:05 Desktop su[10146]: + ??? root:alan
Apr 16 07:57:05 Desktop su[10146]: pam_unix(su:session): session opened for user alan by (uid=0)
Apr 16 07:57:05 Desktop su[10146]: pam_unix(su:session): session closed for user alan
Apr 16 07:57:06 Desktop dbus[1153]: [system] Rejected send message, 4 matched rules; type="error", sender=":1.30" (uid=1000 pid=2214 comm="bluetooth-applet ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.7" (uid=0 pid=1459 comm="/usr/sbin/bluetoothd ")

```

kern.log
```

Apr 16 07:56:42 Desktop kernel: [238522.066948] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro,commit=0
Apr 16 07:56:43 Desktop kernel: [238522.294493] EXT4-fs (md1): re-mounted. Opts: commit=0
Apr 16 07:56:43 Desktop kernel: [238522.301086] EXT4-fs (sda7): re-mounted. Opts: commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0
Apr 16 07:56:43 Desktop kernel: [238522.905981] ehci_hcd 0000:00:12.2: remove, state 4
Apr 16 07:56:43 Desktop kernel: [238522.905994] usb usb1: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238522.924756] ehci_hcd 0000:00:12.2: USB bus 1 deregistered
Apr 16 07:56:43 Desktop kernel: [238522.924913] ehci_hcd 0000:00:12.2: PCI INT B disabled
Apr 16 07:56:43 Desktop kernel: [238522.926961] ehci_hcd 0000:00:13.2: remove, state 1
Apr 16 07:56:43 Desktop kernel: [238522.926981] usb usb2: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238522.926988] usb 2-4: USB disconnect, device number 6
Apr 16 07:56:43 Desktop kernel: [238523.004455] ehci_hcd 0000:00:13.2: USB bus 2 deregistered
Apr 16 07:56:43 Desktop kernel: [238523.004619] ehci_hcd 0000:00:13.2: PCI INT B disabled
Apr 16 07:56:43 Desktop kernel: [238523.024785] ehci_hcd 0000:03:06.2: remove, state 1
Apr 16 07:56:43 Desktop kernel: [238523.024806] usb usb3: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238523.024813] usb 3-5: USB disconnect, device number 3
Apr 16 07:56:43 Desktop kernel: [238523.024819] usb 3-5.1: USB disconnect, device number 4
Apr 16 07:56:43 Desktop kernel: [238523.076412] ehci_hcd 0000:03:06.2: USB bus 3 deregistered
Apr 16 07:56:43 Desktop kernel: [238523.076576] ehci_hcd 0000:03:06.2: PCI INT C disabled
Apr 16 07:56:43 Desktop kernel: [238523.076589] usb 10-1: USB disconnect, device number 16
Apr 16 07:56:43 Desktop kernel: [238523.077311] btusb_bulk_complete: hci0 urb ffff8801a1532e40 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.077327] btusb_intr_complete: hci0 urb ffff8801a1532b40 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.078321] btusb_bulk_complete: hci0 urb ffff8801a1532840 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.078396] btusb_send_frame: hci0 urb ffff8800785ee6c0 submission failed
Apr 16 07:56:44 Desktop kernel: [238523.632057] usb 10-1: new full speed USB device number 17 using ohci_hcd
Apr 16 07:56:44 Desktop kernel: [238523.996082] usb 7-1: new full speed USB device number 6 using ohci_hcd
Apr 16 07:56:44 Desktop kernel: [238524.168698] scsi17 : usb-storage 7-1:1.0
Apr 16 07:56:45 Desktop kernel: [238524.276062] PM: Syncing filesystems ... 
Apr 16 07:56:45 Desktop kernel: [238524.344082] usb 9-3: new full speed USB device number 12 using ohci_hcd
Apr 16 07:57:05 Desktop kernel: [238524.523838] done.
Apr 16 07:57:05 Desktop kernel: [238524.523842] PM: Preparing system for mem sleep
Apr 16 07:57:05 Desktop kernel: [238524.523951] Freezing user space processes ... (elapsed 0.01 seconds) done.
Apr 16 07:57:05 Desktop kernel: [238524.540412] Freezing remaining freezable tasks ... 
Apr 16 07:57:05 Desktop kernel: [238524.547361] hub 9-3:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238524.550331] hub 9-3:1.0: 2 ports detected
Apr 16 07:57:05 Desktop kernel: [238524.696387] usb 6-3: new full speed USB device number 41 using ohci_hcd
Apr 16 07:57:05 Desktop kernel: [238539.832379] usb 6-3: device descriptor read/64, error -110
Apr 16 07:57:05 Desktop kernel: [238544.556403] 
Apr 16 07:57:05 Desktop kernel: [238544.556405] Freezing of tasks failed after 20.01 seconds (1 tasks refusing to freeze, wq_busy=0):
Apr 16 07:57:05 Desktop kernel: [238544.556418] khubd           D ffffffff81805120     0    26      2 0x00800000
Apr 16 07:57:05 Desktop kernel: [238544.556422]  ffff8801a31f9a50 0000000000000046 ffff8801a31f9a8c 0000000000000082
Apr 16 07:57:05 Desktop kernel: [238544.556424]  ffff8801a31f9fd8 ffff8801a31f9fd8 ffff8801a31f9fd8 0000000000012a40
Apr 16 07:57:05 Desktop kernel: [238544.556427]  ffffffff81c0b020 ffff8801a31f1720 ffffffff81e37900 ffff8801a31f9a88
Apr 16 07:57:05 Desktop kernel: [238544.556429] Call Trace:
Apr 16 07:57:05 Desktop kernel: [238544.556436]  [<ffffffff815f22df>] schedule+0x3f/0x60
Apr 16 07:57:05 Desktop kernel: [238544.556438]  [<ffffffff815f27ed>] schedule_timeout+0x16d/0x320
Apr 16 07:57:05 Desktop kernel: [238544.556442]  [<ffffffff81030d5c>] ? amd_flush_garts.part.2+0xfc/0x130
Apr 16 07:57:05 Desktop kernel: [238544.556446]  [<ffffffff8106e040>] ? usleep_range+0x50/0x50
Apr 16 07:57:05 Desktop kernel: [238544.556448]  [<ffffffff815f211f>] wait_for_common+0xdf/0x180
Apr 16 07:57:05 Desktop kernel: [238544.556451]  [<ffffffff810572f0>] ? try_to_wake_up+0x200/0x200
Apr 16 07:57:05 Desktop kernel: [238544.556453]  [<ffffffff815f2273>] wait_for_completion_timeout+0x13/0x20
Apr 16 07:57:05 Desktop kernel: [238544.556456]  [<ffffffff814561d1>] usb_start_wait_urb+0x81/0xf0
Apr 16 07:57:05 Desktop kernel: [238544.556458]  [<ffffffff81455205>] ? usb_init_urb+0x55/0xf0
Apr 16 07:57:05 Desktop kernel: [238544.556460]  [<ffffffff814564c6>] usb_control_msg+0xe6/0x120
Apr 16 07:57:05 Desktop kernel: [238544.556463]  [<ffffffff8144e41a>] hub_port_init+0x32a/0x640
Apr 16 07:57:05 Desktop kernel: [238544.556466]  [<ffffffff81032a79>] ? default_spin_lock_flags+0x9/0x10
Apr 16 07:57:05 Desktop kernel: [238544.556468]  [<ffffffff81450ddb>] hub_port_connect_change+0x2cb/0x6e0
Apr 16 07:57:05 Desktop kernel: [238544.556471]  [<ffffffff814516a4>] hub_events+0x4b4/0x610
Apr 16 07:57:05 Desktop kernel: [238544.556473]  [<ffffffff815f1c84>] ? __schedule+0x3d4/0x700
Apr 16 07:57:05 Desktop kernel: [238544.556475]  [<ffffffff81451835>] hub_thread+0x35/0x180
Apr 16 07:57:05 Desktop kernel: [238544.556478]  [<ffffffff81081da0>] ? add_wait_queue+0x60/0x60
Apr 16 07:57:05 Desktop kernel: [238544.556480]  [<ffffffff81451800>] ? hub_events+0x610/0x610
Apr 16 07:57:05 Desktop kernel: [238544.556482]  [<ffffffff810812fc>] kthread+0x8c/0xa0
Apr 16 07:57:05 Desktop kernel: [238544.556485]  [<ffffffff815fd764>] kernel_thread_helper+0x4/0x10
Apr 16 07:57:05 Desktop kernel: [238544.556487]  [<ffffffff81081270>] ? flush_kthread_worker+0xa0/0xa0
Apr 16 07:57:05 Desktop kernel: [238544.556489]  [<ffffffff815fd760>] ? gs_change+0x13/0x13
Apr 16 07:57:05 Desktop kernel: [238544.556536] 
Apr 16 07:57:05 Desktop kernel: [238544.556537] Restarting tasks ... done.
Apr 16 07:57:05 Desktop kernel: [238544.570733] scsi 17:0:0:0: Direct-Access     Memorex  Flashdrive 601B  PMAP PQ: 0 ANSI: 0 CCS
Apr 16 07:57:05 Desktop kernel: [238544.706352] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 16 07:57:05 Desktop kernel: [238544.706402] ehci_hcd 0000:00:12.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.706481] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr 16 07:57:05 Desktop kernel: [238544.706492] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 07:57:05 Desktop kernel: [238544.706507] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Apr 16 07:57:05 Desktop kernel: [238544.706523] ehci_hcd 0000:00:12.2: debug port 1
Apr 16 07:57:05 Desktop kernel: [238544.706550] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Apr 16 07:57:05 Desktop kernel: [238544.716086] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.716215] hub 1-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.716219] hub 1-0:1.0: 6 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.717132] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr 16 07:57:05 Desktop kernel: [238544.717157] ehci_hcd 0000:00:13.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.717210] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr 16 07:57:05 Desktop kernel: [238544.717221] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 07:57:05 Desktop kernel: [238544.717234] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Apr 16 07:57:05 Desktop kernel: [238544.717254] ehci_hcd 0000:00:13.2: debug port 1
Apr 16 07:57:05 Desktop kernel: [238544.717283] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Apr 16 07:57:05 Desktop kernel: [238544.724565] sd 17:0:0:0: Attached scsi generic sg3 type 0
Apr 16 07:57:05 Desktop kernel: [238544.728162] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.728519] hub 2-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.728530] hub 2-0:1.0: 6 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.734040] ehci_hcd 0000:03:06.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Apr 16 07:57:05 Desktop kernel: [238544.734101] ehci_hcd 0000:03:06.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.734248] ehci_hcd 0000:03:06.2: new USB bus registered, assigned bus number 3
Apr 16 07:57:05 Desktop kernel: [238544.760101] ehci_hcd 0000:03:06.2: irq 22, io mem 0xfddfd000
Apr 16 07:57:05 Desktop kernel: [238544.784129] hub 6-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:57:05 Desktop kernel: [238544.796045] ehci_hcd 0000:03:06.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.796152] hub 3-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.796155] hub 3-0:1.0: 5 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.852883] sd 17:0:0:0: [sdc] READ CAPACITY failed
Apr 16 07:57:05 Desktop kernel: [238544.852894] sd 17:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Apr 16 07:57:05 Desktop kernel: [238544.852903] sd 17:0:0:0: [sdc] Sense not available.
Apr 16 07:57:05 Desktop kernel: [238544.853082] sd 17:0:0:0: [sdc] Write Protect is off
Apr 16 07:57:05 Desktop kernel: [238544.853095] sd 17:0:0:0: [sdc] Mode Sense: 00 00 00 00
Apr 16 07:57:05 Desktop kernel: [238544.853268] sd 17:0:0:0: [sdc] Asking for cache data failed
Apr 16 07:57:05 Desktop kernel: [238544.853276] sd 17:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:57:05 Desktop kernel: [238544.855157] sd 17:0:0:0: [sdc] Attached SCSI removable disk
Apr 16 07:57:05 Desktop kernel: [238544.914025] hub 9-3:1.0: hub_port_status failed (err = -62)
Apr 16 07:57:05 Desktop kernel: [238544.914044] usb 4-2: USB disconnect, device number 9
Apr 16 07:57:05 Desktop kernel: [238545.152204] usb 7-1: USB disconnect, device number 6
Apr 16 07:57:06 Desktop kernel: [238545.296578] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro,commit=0
Apr 16 07:57:06 Desktop kernel: [238545.312136] usb 10-1: USB disconnect, device number 17
Apr 16 07:57:06 Desktop kernel: [238545.312178] btusb_bulk_complete: hci0 urb ffff8800711d9900 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.312195] btusb_intr_complete: hci0 urb ffff8800711d9c00 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.313187] btusb_bulk_complete: hci0 urb ffff8800711d9840 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.313266] btusb_send_frame: hci0 urb ffff8800bd203f00 submission failed
Apr 16 07:57:06 Desktop kernel: [238545.449582] EXT4-fs (md1): re-mounted. Opts: commit=0
Apr 16 07:57:06 Desktop kernel: [238545.456341] EXT4-fs (sda7): re-mounted. Opts: commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0
Apr 16 07:57:06 Desktop kernel: [238545.527710] r8169 0000:02:00.0: eth0: link down
Apr 16 07:57:06 Desktop kernel: [238545.527729] r8169 0000:02:00.0: eth0: link down
Apr 16 07:57:06 Desktop kernel: [238545.530294] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 07:57:06 Desktop kernel: [238545.700525] usb 9-3: USB disconnect, device number 12
Apr 16 07:57:06 Desktop kernel: [238546.052082] usb 2-3: new high speed USB device number 2 using ehci_hcd
Apr 16 07:57:08 Desktop kernel: [238548.007257] r8169 0000:02:00.0: eth0: link up
Apr 16 07:57:08 Desktop kernel: [238548.009753] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 16 07:57:18 Desktop kernel: [238558.096452] eth0: no IPv6 routers present
Apr 16 07:57:21 Desktop kernel: [238561.164467] usb 2-3: device descriptor read/64, error -110
Apr 16 07:57:37 Desktop kernel: [238576.380482] usb 2-3: device descriptor read/64, error -110
Apr 16 07:57:37 Desktop kernel: [238576.596485] usb 2-3: new high speed USB device number 3 using ehci_hcd
Apr 16 07:57:52 Desktop kernel: [238591.708260] usb 2-3: device descriptor read/64, error -110
Apr 16 07:58:07 Desktop kernel: [238606.924101] usb 2-3: device descriptor read/64, error -110
Apr 16 07:58:07 Desktop kernel: [238607.140097] usb 2-3: new high speed USB device number 4 using ehci_hcd
Apr 16 07:58:18 Desktop kernel: [238617.548413] usb 2-3: device not accepting address 4, error -110
Apr 16 07:58:18 Desktop kernel: [238617.660487] usb 2-3: new high speed USB device number 5 using ehci_hcd
Apr 16 07:58:28 Desktop kernel: [238628.068470] usb 2-3: device not accepting address 5, error -110
Apr 16 07:58:28 Desktop kernel: [238628.068504] hub 2-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:58:28 Desktop kernel: [238628.192620] usb 2-4: new high speed USB device number 6 using ehci_hcd
Apr 16 07:58:29 Desktop kernel: [238628.336710] scsi18 : usb-storage 2-4:1.0
Apr 16 07:58:29 Desktop kernel: [238628.560529] usb 3-5: new high speed USB device number 3 using ehci_hcd
Apr 16 07:58:29 Desktop kernel: [238628.694903] hub 3-5:1.0: USB hub found
Apr 16 07:58:29 Desktop kernel: [238628.695072] hub 3-5:1.0: 2 ports detected
Apr 16 07:58:29 Desktop kernel: [238628.956455] usb 4-2: new full speed USB device number 10 using ohci_hcd
Apr 16 07:58:29 Desktop kernel: [238629.138807] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input31
Apr 16 07:58:29 Desktop kernel: [238629.139033] generic-usb 0003:046D:C318.001C: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:00:12.0-2/input0
Apr 16 07:58:29 Desktop kernel: [238629.146371] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input32
Apr 16 07:58:29 Desktop kernel: [238629.146631] generic-usb 0003:046D:C318.001D: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:00:12.0-2/input1
Apr 16 07:58:30 Desktop kernel: [238629.340535] scsi 18:0:0:0: Direct-Access     Memorex  Flashdrive 601B  PMAP PQ: 0 ANSI: 0 CCS
Apr 16 07:58:30 Desktop kernel: [238629.375991] sd 18:0:0:0: Attached scsi generic sg3 type 0
Apr 16 07:58:30 Desktop kernel: [238629.378638] sd 18:0:0:0: [sdc] 977664 512-byte logical blocks: (500 MB/477 MiB)
Apr 16 07:58:30 Desktop kernel: [238629.380594] sd 18:0:0:0: [sdc] Write Protect is off
Apr 16 07:58:30 Desktop kernel: [238629.380604] sd 18:0:0:0: [sdc] Mode Sense: 23 00 00 00
Apr 16 07:58:30 Desktop kernel: [238629.381735] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.381743] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.390968] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.390977] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.395238]  sdc: sdc1
Apr 16 07:58:30 Desktop kernel: [238629.397886] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.397896] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.397905] sd 18:0:0:0: [sdc] Attached SCSI removable disk
Apr 16 07:58:30 Desktop kernel: [238629.412445] usb 6-3: new full speed USB device number 42 using ohci_hcd
Apr 16 07:58:45 Desktop kernel: [238644.548488] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:00 Desktop kernel: [238659.788364] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:00 Desktop kernel: [238660.028369] usb 6-3: new full speed USB device number 43 using ohci_hcd
Apr 16 07:59:15 Desktop kernel: [238675.164425] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:31 Desktop kernel: [238690.404491] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:31 Desktop kernel: [238690.644449] usb 6-3: new full speed USB device number 44 using ohci_hcd
Apr 16 07:59:41 Desktop kernel: [238701.052456] usb 6-3: device not accepting address 44, error -110
Apr 16 07:59:41 Desktop kernel: [238701.188437] usb 6-3: new full speed USB device number 45 using ohci_hcd
Apr 16 07:59:52 Desktop kernel: [238711.596363] usb 6-3: device not accepting address 45, error -110
Apr 16 07:59:52 Desktop kernel: [238711.596417] hub 6-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:59:52 Desktop kernel: [238711.772485] usb 10-1: new full speed USB device number 18 using ohci_hcd
Apr 16 07:59:52 Desktop kernel: [238712.089488] usb 3-5.1: new low speed USB device number 4 using ehci_hcd
Apr 16 07:59:52 Desktop kernel: [238712.205276] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb3/3-5/3-5.1/3-5.1:1.0/input/input33
Apr 16 07:59:52 Desktop kernel: [238712.205554] generic-usb 0003:15CA:00C3.001E: input,hidraw2: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:03:06.2-5.1/input0

```

pm-suspend.log
```

Mon Apr 16 07:50:06 BRT 2012: Finished.
Apr 16 07:56:42 Desktop kernel: [238522.066948] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro,commit=0
Apr 16 07:56:43 Desktop kernel: [238522.294493] EXT4-fs (md1): re-mounted. Opts: commit=0
Apr 16 07:56:43 Desktop kernel: [238522.301086] EXT4-fs (sda7): re-mounted. Opts: commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0
Initial commandline parameters: 
Mon Apr 16 07:56:42 BRT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Desktop 3.0.0-19-generic #32-Ubuntu SMP Thu Apr 5 18:22:38 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
usb_storage            57900  1 
uas                    18027  0 
btusb                  18600  2 
nls_utf8               12557  1 
isofs                  40253  1 
ip6table_filter        12815  0 
ip6_tables             27864  1 ip6table_filter
ipt_MASQUERADE         12759  0 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  0 
nf_conntrack           82342  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             12576  0 
xt_CHECKSUM            12549  0 
iptable_mangle         12734  0 
xt_tcpudp              12603  0 
iptable_filter         12810  0 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 ip6table_filter,ip6_tables,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_CHECKSUM,iptable_mangle,xt_tcpudp,iptable_filter,ip_tables
bridge                 90929  0 
stp                    12931  1 bridge
vesafb                 13844  1 
joydev                 17693  0 
rfcomm                 47946  12 
bnep                   18436  2 
bluetooth             166150  23 btusb,rfcomm,bnep
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
kvm_amd                59832  0 
kvm                   383910  1 kvm_amd
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330815  1 
snd_hda_intel          33390  2 
snd_hda_codec         104968  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
ppdev                  17113  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36962  1 
fglrx                2928969  161 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
it87                   43287  0 
edac_core              53746  0 
hwmon_vid              12746  1 it87
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13791  0 
lp                     17799  0 
wmi                    19256  0 
dm_multipath           27434  0 
psmouse                73882  0 
parport                46562  3 ppdev,parport_pc,lp
serio_raw              13166  0 
i2c_piix4              13301  0 
k10temp                13166  0 
edac_mce_amd           23709  0 
raid10                 30714  0 
raid456                62545  0 
async_pq               13187  1 raid456
async_xor              12879  2 raid456,async_pq
xor                    12894  1 async_xor
async_memcpy           12529  1 raid456
async_raid6_recov      12776  1 raid456
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  9 
r8169                  52788  0 
libahci                26861  1 ahci
raid6_pq               88346  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
pata_atiixp            13164  0 
raid1                  30856  1 
raid0                  17272  1 
multipath              13145  0 
linear                 12928  0 
             total       used       free     shared    buffers     cached
Mem:       6123024    5819348     303676          0     369388    3851932
-/+ buffers/cache:    1598028    4524996
Swap:      7519228         52    7519176

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
Apr 16 07:56:43 Desktop kernel: [238522.905981] ehci_hcd 0000:00:12.2: remove, state 4
Apr 16 07:56:43 Desktop kernel: [238522.905994] usb usb1: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238522.924756] ehci_hcd 0000:00:12.2: USB bus 1 deregistered
Apr 16 07:56:43 Desktop kernel: [238522.924913] ehci_hcd 0000:00:12.2: PCI INT B disabled
Apr 16 07:56:43 Desktop kernel: [238522.926961] ehci_hcd 0000:00:13.2: remove, state 1
Apr 16 07:56:43 Desktop kernel: [238522.926981] usb usb2: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238522.926988] usb 2-4: USB disconnect, device number 6
Apr 16 07:56:43 Desktop kernel: [238523.004455] ehci_hcd 0000:00:13.2: USB bus 2 deregistered
Apr 16 07:56:43 Desktop kernel: [238523.004619] ehci_hcd 0000:00:13.2: PCI INT B disabled
Apr 16 07:56:43 Desktop kernel: [238523.024785] ehci_hcd 0000:03:06.2: remove, state 1
Apr 16 07:56:43 Desktop kernel: [238523.024806] usb usb3: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238523.024813] usb 3-5: USB disconnect, device number 3
Apr 16 07:56:43 Desktop kernel: [238523.024819] usb 3-5.1: USB disconnect, device number 4
Apr 16 07:56:43 Desktop kernel: [238523.076412] ehci_hcd 0000:03:06.2: USB bus 3 deregistered
Apr 16 07:56:43 Desktop kernel: [238523.076576] ehci_hcd 0000:03:06.2: PCI INT C disabled
Apr 16 07:56:43 Desktop kernel: [238523.076589] usb 10-1: USB disconnect, device number 16
Apr 16 07:56:43 Desktop kernel: [238523.077311] btusb_bulk_complete: hci0 urb ffff8801a1532e40 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.077327] btusb_intr_complete: hci0 urb ffff8801a1532b40 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.078321] btusb_bulk_complete: hci0 urb ffff8801a1532840 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.078396] btusb_send_frame: hci0 urb ffff8800785ee6c0 submission failed
Apr 16 07:56:44 Desktop kernel: [238523.632057] usb 10-1: new full speed USB device number 17 using ohci_hcd
Apr 16 07:56:44 Desktop kernel: [238523.996082] usb 7-1: new full speed USB device number 6 using ohci_hcd
Apr 16 07:56:44 Desktop kernel: [238524.168698] scsi17 : usb-storage 7-1:1.0
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:
0000:00:12.20000:00:13.20000:03:06.2ls: cannot access /sys/bus/pci/drivers/xhci_hcd: No such file or directory

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Apr 16 07:56:43 BRT 2012: performing suspend
s2ram_do: Device or resource busy
Apr 16 07:56:45 Desktop kernel: [238524.276062] PM: Syncing filesystems ... 
Apr 16 07:56:45 Desktop kernel: [238524.344082] usb 9-3: new full speed USB device number 12 using ohci_hcd
Apr 16 07:57:05 Desktop kernel: [238524.523838] done.
Apr 16 07:57:05 Desktop kernel: [238524.523842] PM: Preparing system for mem sleep
Apr 16 07:57:05 Desktop kernel: [238524.523951] Freezing user space processes ... (elapsed 0.01 seconds) done.
Apr 16 07:57:05 Desktop kernel: [238524.540412] Freezing remaining freezable tasks ... 
Apr 16 07:57:05 Desktop kernel: [238524.547361] hub 9-3:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238524.550331] hub 9-3:1.0: 2 ports detected
Apr 16 07:57:05 Desktop kernel: [238524.696387] usb 6-3: new full speed USB device number 41 using ohci_hcd
Apr 16 07:57:05 Desktop kernel: [238539.832379] usb 6-3: device descriptor read/64, error -110
Apr 16 07:57:05 Desktop kernel: [238544.556403] 
Apr 16 07:57:05 Desktop kernel: [238544.556405] Freezing of tasks failed after 20.01 seconds (1 tasks refusing to freeze, wq_busy=0):
Apr 16 07:57:05 Desktop kernel: [238544.556418] khubd           D ffffffff81805120     0    26      2 0x00800000
Apr 16 07:57:05 Desktop kernel: [238544.556422]  ffff8801a31f9a50 0000000000000046 ffff8801a31f9a8c 0000000000000082
Apr 16 07:57:05 Desktop kernel: [238544.556424]  ffff8801a31f9fd8 ffff8801a31f9fd8 ffff8801a31f9fd8 0000000000012a40
Apr 16 07:57:05 Desktop kernel: [238544.556427]  ffffffff81c0b020 ffff8801a31f1720 ffffffff81e37900 ffff8801a31f9a88
Apr 16 07:57:05 Desktop kernel: [238544.556429] Call Trace:
Apr 16 07:57:05 Desktop kernel: [238544.556436]  [<ffffffff815f22df>] schedule+0x3f/0x60
Apr 16 07:57:05 Desktop kernel: [238544.556438]  [<ffffffff815f27ed>] schedule_timeout+0x16d/0x320
Apr 16 07:57:05 Desktop kernel: [238544.556442]  [<ffffffff81030d5c>] ? amd_flush_garts.part.2+0xfc/0x130
Apr 16 07:57:05 Desktop kernel: [238544.556446]  [<ffffffff8106e040>] ? usleep_range+0x50/0x50
Apr 16 07:57:05 Desktop kernel: [238544.556448]  [<ffffffff815f211f>] wait_for_common+0xdf/0x180
Apr 16 07:57:05 Desktop kernel: [238544.556451]  [<ffffffff810572f0>] ? try_to_wake_up+0x200/0x200
Apr 16 07:57:05 Desktop kernel: [238544.556453]  [<ffffffff815f2273>] wait_for_completion_timeout+0x13/0x20
Apr 16 07:57:05 Desktop kernel: [238544.556456]  [<ffffffff814561d1>] usb_start_wait_urb+0x81/0xf0
Apr 16 07:57:05 Desktop kernel: [238544.556458]  [<ffffffff81455205>] ? usb_init_urb+0x55/0xf0
Apr 16 07:57:05 Desktop kernel: [238544.556460]  [<ffffffff814564c6>] usb_control_msg+0xe6/0x120
Apr 16 07:57:05 Desktop kernel: [238544.556463]  [<ffffffff8144e41a>] hub_port_init+0x32a/0x640
Apr 16 07:57:05 Desktop kernel: [238544.556466]  [<ffffffff81032a79>] ? default_spin_lock_flags+0x9/0x10
Apr 16 07:57:05 Desktop kernel: [238544.556468]  [<ffffffff81450ddb>] hub_port_connect_change+0x2cb/0x6e0
Apr 16 07:57:05 Desktop kernel: [238544.556471]  [<ffffffff814516a4>] hub_events+0x4b4/0x610
Apr 16 07:57:05 Desktop kernel: [238544.556473]  [<ffffffff815f1c84>] ? __schedule+0x3d4/0x700
Apr 16 07:57:05 Desktop kernel: [238544.556475]  [<ffffffff81451835>] hub_thread+0x35/0x180
Apr 16 07:57:05 Desktop kernel: [238544.556478]  [<ffffffff81081da0>] ? add_wait_queue+0x60/0x60
Apr 16 07:57:05 Desktop kernel: [238544.556480]  [<ffffffff81451800>] ? hub_events+0x610/0x610
Apr 16 07:57:05 Desktop kernel: [238544.556482]  [<ffffffff810812fc>] kthread+0x8c/0xa0
Apr 16 07:57:05 Desktop kernel: [238544.556485]  [<ffffffff815fd764>] kernel_thread_helper+0x4/0x10
Apr 16 07:57:05 Desktop kernel: [238544.556487]  [<ffffffff81081270>] ? flush_kthread_worker+0xa0/0xa0
Apr 16 07:57:05 Desktop kernel: [238544.556489]  [<ffffffff815fd760>] ? gs_change+0x13/0x13
Apr 16 07:57:05 Desktop kernel: [238544.556536] 
Apr 16 07:57:05 Desktop kernel: [238544.556537] Restarting tasks ... done.
Apr 16 07:57:05 Desktop kernel: [238544.570733] scsi 17:0:0:0: Direct-Access     Memorex  Flashdrive 601B  PMAP PQ: 0 ANSI: 0 CCS
Apr 16 07:57:05 Desktop kernel: [238544.706352] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 16 07:57:05 Desktop kernel: [238544.706402] ehci_hcd 0000:00:12.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.706481] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr 16 07:57:05 Desktop kernel: [238544.706492] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 07:57:05 Desktop kernel: [238544.706507] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Apr 16 07:57:05 Desktop kernel: [238544.706523] ehci_hcd 0000:00:12.2: debug port 1
Apr 16 07:57:05 Desktop kernel: [238544.706550] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Apr 16 07:57:05 Desktop kernel: [238544.716086] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.716215] hub 1-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.716219] hub 1-0:1.0: 6 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.717132] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr 16 07:57:05 Desktop kernel: [238544.717157] ehci_hcd 0000:00:13.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.717210] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr 16 07:57:05 Desktop kernel: [238544.717221] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 07:57:05 Desktop kernel: [238544.717234] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Apr 16 07:57:05 Desktop kernel: [238544.717254] ehci_hcd 0000:00:13.2: debug port 1
Apr 16 07:57:05 Desktop kernel: [238544.717283] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Apr 16 07:57:05 Desktop kernel: [238544.724565] sd 17:0:0:0: Attached scsi generic sg3 type 0
Apr 16 07:57:05 Desktop kernel: [238544.728162] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.728519] hub 2-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.728530] hub 2-0:1.0: 6 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.734040] ehci_hcd 0000:03:06.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Apr 16 07:57:05 Desktop kernel: [238544.734101] ehci_hcd 0000:03:06.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.734248] ehci_hcd 0000:03:06.2: new USB bus registered, assigned bus number 3
Apr 16 07:57:05 Desktop kernel: [238544.760101] ehci_hcd 0000:03:06.2: irq 22, io mem 0xfddfd000
Apr 16 07:57:05 Desktop kernel: [238544.784129] hub 6-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:57:05 Desktop kernel: [238544.796045] ehci_hcd 0000:03:06.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.796152] hub 3-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.796155] hub 3-0:1.0: 5 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.852883] sd 17:0:0:0: [sdc] READ CAPACITY failed
Apr 16 07:57:05 Desktop kernel: [238544.852894] sd 17:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Apr 16 07:57:05 Desktop kernel: [238544.852903] sd 17:0:0:0: [sdc] Sense not available.
Apr 16 07:57:05 Desktop kernel: [238544.853082] sd 17:0:0:0: [sdc] Write Protect is off
Apr 16 07:57:05 Desktop kernel: [238544.853095] sd 17:0:0:0: [sdc] Mode Sense: 00 00 00 00
Apr 16 07:57:05 Desktop kernel: [238544.853268] sd 17:0:0:0: [sdc] Asking for cache data failed
Apr 16 07:57:05 Desktop kernel: [238544.853276] sd 17:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:57:05 Desktop kernel: [238544.855157] sd 17:0:0:0: [sdc] Attached SCSI removable disk
Apr 16 07:57:05 Desktop kernel: [238544.914025] hub 9-3:1.0: hub_port_status failed (err = -62)
Apr 16 07:57:05 Desktop kernel: [238544.914044] usb 4-2: USB disconnect, device number 9
Apr 16 07:57:05 Desktop kernel: [238545.152204] usb 7-1: USB disconnect, device number 6
Apr 16 07:57:06 Desktop kernel: [238545.296578] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro,commit=0
Apr 16 07:57:06 Desktop kernel: [238545.312136] usb 10-1: USB disconnect, device number 17
Apr 16 07:57:06 Desktop kernel: [238545.312178] btusb_bulk_complete: hci0 urb ffff8800711d9900 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.312195] btusb_intr_complete: hci0 urb ffff8800711d9c00 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.313187] btusb_bulk_complete: hci0 urb ffff8800711d9840 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.313266] btusb_send_frame: hci0 urb ffff8800bd203f00 submission failed
Apr 16 07:57:06 Desktop kernel: [238545.449582] EXT4-fs (md1): re-mounted. Opts: commit=0
Apr 16 07:57:06 Desktop kernel: [238545.456341] EXT4-fs (sda7): re-mounted. Opts: commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0
Apr 16 07:57:06 Desktop kernel: [238545.527710] r8169 0000:02:00.0: eth0: link down
Apr 16 07:57:06 Desktop kernel: [238545.527729] r8169 0000:02:00.0: eth0: link down
Apr 16 07:57:06 Desktop kernel: [238545.530294] ADDRCONF(NETDEV_UP): eth0: link is not ready
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Mon Apr 16 07:57:05 BRT 2012: Awake.
Mon Apr 16 07:57:05 BRT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:
0000:00:12.20000:00:13.20000:03:06.2
/etc/pm/sleep.d/20_custom-ehci_hcd resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Apr 16 07:57:06 BRT 2012: Finished.
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Mon Apr 16 07:57:05 BRT 2012: Awake.
Mon Apr 16 07:57:05 BRT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:
0000:00:12.20000:00:13.20000:03:06.2
/etc/pm/sleep.d/20_custom-ehci_hcd resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Apr 16 07:57:06 BRT 2012: Finished.
Apr 16 07:57:06 Desktop kernel: [238545.700525] usb 9-3: USB disconnect, device number 12
Apr 16 07:57:06 Desktop kernel: [238546.052082] usb 2-3: new high speed USB device number 2 using ehci_hcd
Apr 16 07:57:08 Desktop kernel: [238548.007257] r8169 0000:02:00.0: eth0: link up
Apr 16 07:57:08 Desktop kernel: [238548.009753] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 16 07:57:18 Desktop kernel: [238558.096452] eth0: no IPv6 routers present
Apr 16 07:57:21 Desktop kernel: [238561.164467] usb 2-3: device descriptor read/64, error -110
Apr 16 07:57:37 Desktop kernel: [238576.380482] usb 2-3: device descriptor read/64, error -110
Apr 16 07:57:37 Desktop kernel: [238576.596485] usb 2-3: new high speed USB device number 3 using ehci_hcd
Apr 16 07:57:52 Desktop kernel: [238591.708260] usb 2-3: device descriptor read/64, error -110
Apr 16 07:58:07 Desktop kernel: [238606.924101] usb 2-3: device descriptor read/64, error -110
Apr 16 07:58:07 Desktop kernel: [238607.140097] usb 2-3: new high speed USB device number 4 using ehci_hcd
Apr 16 07:58:18 Desktop kernel: [238617.548413] usb 2-3: device not accepting address 4, error -110
Apr 16 07:58:18 Desktop kernel: [238617.660487] usb 2-3: new high speed USB device number 5 using ehci_hcd
Apr 16 07:58:28 Desktop kernel: [238628.068470] usb 2-3: device not accepting address 5, error -110
Apr 16 07:58:28 Desktop kernel: [238628.068504] hub 2-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:58:28 Desktop kernel: [238628.192620] usb 2-4: new high speed USB device number 6 using ehci_hcd
Apr 16 07:58:29 Desktop kernel: [238628.336710] scsi18 : usb-storage 2-4:1.0
Apr 16 07:58:29 Desktop kernel: [238628.560529] usb 3-5: new high speed USB device number 3 using ehci_hcd
Apr 16 07:58:29 Desktop kernel: [238628.694903] hub 3-5:1.0: USB hub found
Apr 16 07:58:29 Desktop kernel: [238628.695072] hub 3-5:1.0: 2 ports detected
Apr 16 07:58:29 Desktop kernel: [238628.956455] usb 4-2: new full speed USB device number 10 using ohci_hcd
Apr 16 07:58:29 Desktop kernel: [238629.138807] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input31
Apr 16 07:58:29 Desktop kernel: [238629.139033] generic-usb 0003:046D:C318.001C: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:00:12.0-2/input0
Apr 16 07:58:29 Desktop kernel: [238629.146371] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input32
Apr 16 07:58:29 Desktop kernel: [238629.146631] generic-usb 0003:046D:C318.001D: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:00:12.0-2/input1
Apr 16 07:58:30 Desktop kernel: [238629.340535] scsi 18:0:0:0: Direct-Access     Memorex  Flashdrive 601B  PMAP PQ: 0 ANSI: 0 CCS
Apr 16 07:58:30 Desktop kernel: [238629.375991] sd 18:0:0:0: Attached scsi generic sg3 type 0
Apr 16 07:58:30 Desktop kernel: [238629.378638] sd 18:0:0:0: [sdc] 977664 512-byte logical blocks: (500 MB/477 MiB)
Apr 16 07:58:30 Desktop kernel: [238629.380594] sd 18:0:0:0: [sdc] Write Protect is off
Apr 16 07:58:30 Desktop kernel: [238629.380604] sd 18:0:0:0: [sdc] Mode Sense: 23 00 00 00
Apr 16 07:58:30 Desktop kernel: [238629.381735] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.381743] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.390968] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.390977] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.395238]  sdc: sdc1
Apr 16 07:58:30 Desktop kernel: [238629.397886] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.397896] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.397905] sd 18:0:0:0: [sdc] Attached SCSI removable disk
Apr 16 07:58:30 Desktop kernel: [238629.412445] usb 6-3: new full speed USB device number 42 using ohci_hcd
Apr 16 07:58:45 Desktop kernel: [238644.548488] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:00 Desktop kernel: [238659.788364] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:00 Desktop kernel: [238660.028369] usb 6-3: new full speed USB device number 43 using ohci_hcd
Apr 16 07:59:15 Desktop kernel: [238675.164425] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:31 Desktop kernel: [238690.404491] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:31 Desktop kernel: [238690.644449] usb 6-3: new full speed USB device number 44 using ohci_hcd
Apr 16 07:59:41 Desktop kernel: [238701.052456] usb 6-3: device not accepting address 44, error -110
Apr 16 07:59:41 Desktop kernel: [238701.188437] usb 6-3: new full speed USB device number 45 using ohci_hcd
Apr 16 07:59:52 Desktop kernel: [238711.596363] usb 6-3: device not accepting address 45, error -110
Apr 16 07:59:52 Desktop kernel: [238711.596417] hub 6-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:59:52 Desktop kernel: [238711.772485] usb 10-1: new full speed USB device number 18 using ohci_hcd
Apr 16 07:59:52 Desktop kernel: [238712.089488] usb 3-5.1: new low speed USB device number 4 using ehci_hcd
Apr 16 07:59:52 Desktop kernel: [238712.205276] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb3/3-5/3-5.1/3-5.1:1.0/input/input33
Apr 16 07:59:52 Desktop kernel: [238712.205554] generic-usb 0003:15CA:00C3.001E: input,hidraw2: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:03:06.2-5.1/input0

```

syslong
```

Apr 16 07:53:06 Desktop AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> sleep requested (sleeping: no  enabled: yes)
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> sleeping or disabling...
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (eth0): now unmanaged
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (eth0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (eth0): deactivating device (reason 'sleeping') [37]
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (eth0): canceled DHCP transaction, DHCP client pid 6546
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (eth0): cleaning up...
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (eth0): taking down device.
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): now unmanaged
Apr 16 07:56:41 Desktop dbus[1153]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): cleaning up...
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): taking down device.
Apr 16 07:56:41 Desktop NetworkManager[1167]: <info> (eth0): carrier now OFF (device state 10)
Apr 16 07:56:41 Desktop dbus[1153]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 16 07:56:42 Desktop anacron[9483]: Anacron 2.3 started on 2012-04-16
Apr 16 07:56:42 Desktop anacron[9483]: Normal exit (0 jobs run)
Apr 16 07:56:42 Desktop kernel: [238522.066948] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro,commit=0
Apr 16 07:56:43 Desktop kernel: [238522.294493] EXT4-fs (md1): re-mounted. Opts: commit=0
Apr 16 07:56:43 Desktop kernel: [238522.301086] EXT4-fs (sda7): re-mounted. Opts: commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0
Apr 16 07:56:43 Desktop kernel: [238522.905981] ehci_hcd 0000:00:12.2: remove, state 4
Apr 16 07:56:43 Desktop kernel: [238522.905994] usb usb1: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238522.924756] ehci_hcd 0000:00:12.2: USB bus 1 deregistered
Apr 16 07:56:43 Desktop kernel: [238522.924913] ehci_hcd 0000:00:12.2: PCI INT B disabled
Apr 16 07:56:43 Desktop kernel: [238522.926961] ehci_hcd 0000:00:13.2: remove, state 1
Apr 16 07:56:43 Desktop kernel: [238522.926981] usb usb2: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238522.926988] usb 2-4: USB disconnect, device number 6
Apr 16 07:56:43 Desktop kernel: [238523.004455] ehci_hcd 0000:00:13.2: USB bus 2 deregistered
Apr 16 07:56:43 Desktop kernel: [238523.004619] ehci_hcd 0000:00:13.2: PCI INT B disabled
Apr 16 07:56:43 Desktop kernel: [238523.024785] ehci_hcd 0000:03:06.2: remove, state 1
Apr 16 07:56:43 Desktop kernel: [238523.024806] usb usb3: USB disconnect, device number 1
Apr 16 07:56:43 Desktop kernel: [238523.024813] usb 3-5: USB disconnect, device number 3
Apr 16 07:56:43 Desktop kernel: [238523.024819] usb 3-5.1: USB disconnect, device number 4
Apr 16 07:56:43 Desktop bluetoothd[1459]: HCI dev 0 down
Apr 16 07:56:43 Desktop bluetoothd[1459]: Adapter /org/bluez/1459/hci0 has been disabled
Apr 16 07:56:43 Desktop kernel: [238523.076412] ehci_hcd 0000:03:06.2: USB bus 3 deregistered
Apr 16 07:56:43 Desktop kernel: [238523.076576] ehci_hcd 0000:03:06.2: PCI INT C disabled
Apr 16 07:56:43 Desktop kernel: [238523.076589] usb 10-1: USB disconnect, device number 16
Apr 16 07:56:43 Desktop kernel: [238523.077311] btusb_bulk_complete: hci0 urb ffff8801a1532e40 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.077327] btusb_intr_complete: hci0 urb ffff8801a1532b40 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.078321] btusb_bulk_complete: hci0 urb ffff8801a1532840 failed to resubmit (19)
Apr 16 07:56:43 Desktop kernel: [238523.078396] btusb_send_frame: hci0 urb ffff8800785ee6c0 submission failed
Apr 16 07:56:43 Desktop bluetoothd[1459]: Can't init device hci0: No such device (19)
Apr 16 07:56:44 Desktop bluetoothd[1459]: HCI dev 0 unregistered
Apr 16 07:56:44 Desktop bluetoothd[1459]: Stopping hci0 event socket
Apr 16 07:56:44 Desktop bluetoothd[1459]: Unregister path: /org/bluez/1459/hci0
Apr 16 07:56:44 Desktop NetworkManager[1167]: <info> BT device 76:8E:46:66:20:4C removed
Apr 16 07:56:44 Desktop kernel: [238523.632057] usb 10-1: new full speed USB device number 17 using ohci_hcd
Apr 16 07:56:44 Desktop bluetoothd[1459]: HCI dev 0 registered
Apr 16 07:56:44 Desktop bluetoothd[1459]: Listening for HCI events on hci0
Apr 16 07:56:44 Desktop kernel: [238523.996082] usb 7-1: new full speed USB device number 6 using ohci_hcd
Apr 16 07:56:44 Desktop bluetoothd[1459]: HCI dev 0 up
Apr 16 07:56:44 Desktop bluetoothd[1459]: input-headset driver probe failed for device 76:8E:46:66:20:4C
Apr 16 07:56:44 Desktop bluetoothd[1459]: input-headset driver probe failed for device A0:75:91:A0:54:8C
Apr 16 07:56:44 Desktop bluetoothd[1459]: Adapter /org/bluez/1459/hci0 has been enabled
Apr 16 07:56:44 Desktop pulseaudio[2183]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Apr 16 07:56:44  pulseaudio[2183]: last message repeated 2 times
Apr 16 07:56:44 Desktop NetworkManager[1167]: <warn> (76:8E:46:66:20:4C): failed to look up interface index
Apr 16 07:56:44 Desktop NetworkManager[1167]: <info> BT device ANDROID BT (76:8E:46:66:20:4C) added (DUN NAP)
Apr 16 07:56:44 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): new Bluetooth device (driver: 'bluez' ifindex: 0)
Apr 16 07:56:44 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): exported as /org/freedesktop/NetworkManager/Devices/16
Apr 16 07:56:44 Desktop mtp-probe: checking bus 7, device 6: "/sys/devices/pci0000:00/0000:00:13.1/usb7/7-1"
Apr 16 07:56:44 Desktop kernel: [238524.168698] scsi17 : usb-storage 7-1:1.0
Apr 16 07:56:45 Desktop kernel: [238524.276062] PM: Syncing filesystems ... 
Apr 16 07:56:45 Desktop kernel: [238524.344082] usb 9-3: new full speed USB device number 12 using ohci_hcd
Apr 16 07:56:45 Desktop mtp-probe: bus: 7, device: 6 was not an MTP device
Apr 16 07:57:05 Desktop kernel: [238524.523838] done.
Apr 16 07:57:05 Desktop kernel: [238524.523842] PM: Preparing system for mem sleep
Apr 16 07:57:05 Desktop kernel: [238524.523951] Freezing user space processes ... (elapsed 0.01 seconds) done.
Apr 16 07:57:05 Desktop kernel: [238524.540412] Freezing remaining freezable tasks ... 
Apr 16 07:57:05 Desktop kernel: [238524.547361] hub 9-3:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238524.550331] hub 9-3:1.0: 2 ports detected
Apr 16 07:57:05 Desktop kernel: [238524.696387] usb 6-3: new full speed USB device number 41 using ohci_hcd
Apr 16 07:57:05 Desktop kernel: [238539.832379] usb 6-3: device descriptor read/64, error -110
Apr 16 07:57:05 Desktop kernel: [238544.556403] 
Apr 16 07:57:05 Desktop kernel: [238544.556405] Freezing of tasks failed after 20.01 seconds (1 tasks refusing to freeze, wq_busy=0):
Apr 16 07:57:05 Desktop kernel: [238544.556418] khubd           D ffffffff81805120     0    26      2 0x00800000
Apr 16 07:57:05 Desktop kernel: [238544.556422]  ffff8801a31f9a50 0000000000000046 ffff8801a31f9a8c 0000000000000082
Apr 16 07:57:05 Desktop kernel: [238544.556424]  ffff8801a31f9fd8 ffff8801a31f9fd8 ffff8801a31f9fd8 0000000000012a40
Apr 16 07:57:05 Desktop kernel: [238544.556427]  ffffffff81c0b020 ffff8801a31f1720 ffffffff81e37900 ffff8801a31f9a88
Apr 16 07:57:05 Desktop kernel: [238544.556429] Call Trace:
Apr 16 07:57:05 Desktop kernel: [238544.556436]  [<ffffffff815f22df>] schedule+0x3f/0x60
Apr 16 07:57:05 Desktop kernel: [238544.556438]  [<ffffffff815f27ed>] schedule_timeout+0x16d/0x320
Apr 16 07:57:05 Desktop kernel: [238544.556442]  [<ffffffff81030d5c>] ? amd_flush_garts.part.2+0xfc/0x130
Apr 16 07:57:05 Desktop kernel: [238544.556446]  [<ffffffff8106e040>] ? usleep_range+0x50/0x50
Apr 16 07:57:05 Desktop kernel: [238544.556448]  [<ffffffff815f211f>] wait_for_common+0xdf/0x180
Apr 16 07:57:05 Desktop kernel: [238544.556451]  [<ffffffff810572f0>] ? try_to_wake_up+0x200/0x200
Apr 16 07:57:05 Desktop kernel: [238544.556453]  [<ffffffff815f2273>] wait_for_completion_timeout+0x13/0x20
Apr 16 07:57:05 Desktop kernel: [238544.556456]  [<ffffffff814561d1>] usb_start_wait_urb+0x81/0xf0
Apr 16 07:57:05 Desktop kernel: [238544.556458]  [<ffffffff81455205>] ? usb_init_urb+0x55/0xf0
Apr 16 07:57:05 Desktop kernel: [238544.556460]  [<ffffffff814564c6>] usb_control_msg+0xe6/0x120
Apr 16 07:57:05 Desktop kernel: [238544.556463]  [<ffffffff8144e41a>] hub_port_init+0x32a/0x640
Apr 16 07:57:05 Desktop kernel: [238544.556466]  [<ffffffff81032a79>] ? default_spin_lock_flags+0x9/0x10
Apr 16 07:57:05 Desktop kernel: [238544.556468]  [<ffffffff81450ddb>] hub_port_connect_change+0x2cb/0x6e0
Apr 16 07:57:05 Desktop kernel: [238544.556471]  [<ffffffff814516a4>] hub_events+0x4b4/0x610
Apr 16 07:57:05 Desktop kernel: [238544.556473]  [<ffffffff815f1c84>] ? __schedule+0x3d4/0x700
Apr 16 07:57:05 Desktop kernel: [238544.556475]  [<ffffffff81451835>] hub_thread+0x35/0x180
Apr 16 07:57:05 Desktop kernel: [238544.556478]  [<ffffffff81081da0>] ? add_wait_queue+0x60/0x60
Apr 16 07:57:05 Desktop kernel: [238544.556480]  [<ffffffff81451800>] ? hub_events+0x610/0x610
Apr 16 07:57:05 Desktop kernel: [238544.556482]  [<ffffffff810812fc>] kthread+0x8c/0xa0
Apr 16 07:57:05 Desktop kernel: [238544.556485]  [<ffffffff815fd764>] kernel_thread_helper+0x4/0x10
Apr 16 07:57:05 Desktop kernel: [238544.556487]  [<ffffffff81081270>] ? flush_kthread_worker+0xa0/0xa0
Apr 16 07:57:05 Desktop kernel: [238544.556489]  [<ffffffff815fd760>] ? gs_change+0x13/0x13
Apr 16 07:57:05 Desktop kernel: [238544.556536] 
Apr 16 07:57:05 Desktop kernel: [238544.556537] Restarting tasks ... done.
Apr 16 10:57:05 Desktop rtkit-daemon[2185]: The canary thread is apparently starving. Taking action.
Apr 16 10:57:05 Desktop rtkit-daemon[2185]: Demoting known real-time threads.
Apr 16 10:57:05 Desktop rtkit-daemon[2185]: Successfully demoted thread 2203 of process 2183 (n/a).
Apr 16 10:57:05 Desktop rtkit-daemon[2185]: Successfully demoted thread 2202 of process 2183 (n/a).
Apr 16 10:57:05 Desktop rtkit-daemon[2185]: Successfully demoted thread 2183 of process 2183 (n/a).
Apr 16 10:57:05 Desktop rtkit-daemon[2185]: Demoted 3 threads.
Apr 16 07:57:05 Desktop kernel: [238544.570733] scsi 17:0:0:0: Direct-Access     Memorex  Flashdrive 601B  PMAP PQ: 0 ANSI: 0 CCS
Apr 16 07:57:05 Desktop anacron[9992]: Anacron 2.3 started on 2012-04-16
Apr 16 07:57:05 Desktop anacron[9992]: Normal exit (0 jobs run)
Apr 16 07:57:05 Desktop kernel: [238544.706352] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 16 07:57:05 Desktop kernel: [238544.706402] ehci_hcd 0000:00:12.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.706481] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr 16 07:57:05 Desktop kernel: [238544.706492] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 07:57:05 Desktop kernel: [238544.706507] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Apr 16 07:57:05 Desktop kernel: [238544.706523] ehci_hcd 0000:00:12.2: debug port 1
Apr 16 07:57:05 Desktop kernel: [238544.706550] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Apr 16 07:57:05 Desktop kernel: [238544.716086] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.716215] hub 1-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.716219] hub 1-0:1.0: 6 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.717132] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr 16 07:57:05 Desktop kernel: [238544.717157] ehci_hcd 0000:00:13.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.717210] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr 16 07:57:05 Desktop kernel: [238544.717221] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 07:57:05 Desktop kernel: [238544.717234] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Apr 16 07:57:05 Desktop kernel: [238544.717254] ehci_hcd 0000:00:13.2: debug port 1
Apr 16 07:57:05 Desktop kernel: [238544.717283] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Apr 16 07:57:05 Desktop kernel: [238544.724565] sd 17:0:0:0: Attached scsi generic sg3 type 0
Apr 16 07:57:05 Desktop kernel: [238544.728162] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.728519] hub 2-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.728530] hub 2-0:1.0: 6 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.734040] ehci_hcd 0000:03:06.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Apr 16 07:57:05 Desktop kernel: [238544.734101] ehci_hcd 0000:03:06.2: EHCI Host Controller
Apr 16 07:57:05 Desktop kernel: [238544.734248] ehci_hcd 0000:03:06.2: new USB bus registered, assigned bus number 3
Apr 16 07:57:05 Desktop kernel: [238544.760101] ehci_hcd 0000:03:06.2: irq 22, io mem 0xfddfd000
Apr 16 07:57:05 Desktop kernel: [238544.784129] hub 6-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:57:05 Desktop kernel: [238544.796045] ehci_hcd 0000:03:06.2: USB 2.0 started, EHCI 1.00
Apr 16 07:57:05 Desktop kernel: [238544.796152] hub 3-0:1.0: USB hub found
Apr 16 07:57:05 Desktop kernel: [238544.796155] hub 3-0:1.0: 5 ports detected
Apr 16 07:57:05 Desktop kernel: [238544.852883] sd 17:0:0:0: [sdc] READ CAPACITY failed
Apr 16 07:57:05 Desktop kernel: [238544.852894] sd 17:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Apr 16 07:57:05 Desktop kernel: [238544.852903] sd 17:0:0:0: [sdc] Sense not available.
Apr 16 07:57:05 Desktop kernel: [238544.853082] sd 17:0:0:0: [sdc] Write Protect is off
Apr 16 07:57:05 Desktop kernel: [238544.853095] sd 17:0:0:0: [sdc] Mode Sense: 00 00 00 00
Apr 16 07:57:05 Desktop kernel: [238544.853268] sd 17:0:0:0: [sdc] Asking for cache data failed
Apr 16 07:57:05 Desktop kernel: [238544.853276] sd 17:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:57:05 Desktop kernel: [238544.855157] sd 17:0:0:0: [sdc] Attached SCSI removable disk
Apr 16 07:57:05 Desktop kernel: [238544.914025] hub 9-3:1.0: hub_port_status failed (err = -62)
Apr 16 07:57:05 Desktop kernel: [238544.914044] usb 4-2: USB disconnect, device number 9
Apr 16 07:57:05 Desktop anacron[10206]: Anacron 2.3 started on 2012-04-16
Apr 16 07:57:05 Desktop anacron[10206]: Normal exit (0 jobs run)
Apr 16 07:57:05 Desktop kernel: [238545.152204] usb 7-1: USB disconnect, device number 6
Apr 16 07:57:06 Desktop kernel: [238545.296578] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro,commit=0
Apr 16 07:57:06 Desktop bluetoothd[1459]: HCI dev 0 down
Apr 16 07:57:06 Desktop bluetoothd[1459]: Adapter /org/bluez/1459/hci0 has been disabled
Apr 16 07:57:06 Desktop kernel: [238545.312136] usb 10-1: USB disconnect, device number 17
Apr 16 07:57:06 Desktop kernel: [238545.312178] btusb_bulk_complete: hci0 urb ffff8800711d9900 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.312195] btusb_intr_complete: hci0 urb ffff8800711d9c00 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.313187] btusb_bulk_complete: hci0 urb ffff8800711d9840 failed to resubmit (19)
Apr 16 07:57:06 Desktop kernel: [238545.313266] btusb_send_frame: hci0 urb ffff8800bd203f00 submission failed
Apr 16 07:57:06 Desktop bluetoothd[1459]: Can't init device hci0: No such device (19)
Apr 16 07:57:06 Desktop kernel: [238545.449582] EXT4-fs (md1): re-mounted. Opts: commit=0
Apr 16 07:57:06 Desktop kernel: [238545.456341] EXT4-fs (sda7): re-mounted. Opts: commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0,commit=0
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> wake requested (sleeping: yes  enabled: yes)
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> waking up and re-enabling...
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (eth0): now managed
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (eth0): bringing up device.
Apr 16 07:57:06 Desktop kernel: [238545.527710] r8169 0000:02:00.0: eth0: link down
Apr 16 07:57:06 Desktop kernel: [238545.527729] r8169 0000:02:00.0: eth0: link down
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (eth0): preparing device.
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): now managed
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 07:57:06 Desktop kernel: [238545.530294] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): deactivating device (reason 'managed') [2]
Apr 16 07:57:06 Desktop NetworkManager[1167]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Apr 16 07:57:06 Desktop NetworkManager[1167]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Apr 16 07:57:06 Desktop bluetoothd[1459]: HCI dev 0 unregistered
Apr 16 07:57:06 Desktop bluetoothd[1459]: Stopping hci0 event socket
Apr 16 07:57:06 Desktop bluetoothd[1459]: Unregister path: /org/bluez/1459/hci0
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> BT device 76:8E:46:66:20:4C removed
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): now unmanaged
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): cleaning up...
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): taking down device.
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Apr 16 07:57:06 Desktop NetworkManager[1167]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Apr 16 07:57:06 Desktop kernel: [238545.700525] usb 9-3: USB disconnect, device number 12
Apr 16 07:57:06 Desktop kernel: [238546.052082] usb 2-3: new high speed USB device number 2 using ehci_hcd
Apr 16 07:57:08 Desktop kernel: [238548.007257] r8169 0000:02:00.0: eth0: link up
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> (eth0): carrier now ON (device state 20)
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Auto-activating connection 'Auto eth0'.
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) starting connection 'Auto eth0'
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 16 07:57:08 Desktop kernel: [238548.009753] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> dhclient started with pid 10305
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 16 07:57:08 Desktop dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr 16 07:57:08 Desktop dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr 16 07:57:08 Desktop dhclient: All rights reserved.
Apr 16 07:57:08 Desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 16 07:57:08 Desktop dhclient: 
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 16 07:57:08 Desktop dhclient: Listening on LPF/eth0/00:1f:d0:95:8f:50
Apr 16 07:57:08 Desktop dhclient: Sending on   LPF/eth0/00:1f:d0:95:8f:50
Apr 16 07:57:08 Desktop dhclient: Sending on   Socket/fallback
Apr 16 07:57:08 Desktop dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
Apr 16 07:57:08 Desktop dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Apr 16 07:57:08 Desktop dhclient: bound to 192.168.1.100 -- renewal in 37353 seconds.
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info>   address 192.168.1.100
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info>   prefix 24 (255.255.255.0)
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info>   gateway 192.168.1.1
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info>   hostname 'Desktop'
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info>   nameserver '192.168.1.1'
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info>   wins '192.168.1.1'
Apr 16 07:57:08 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 16 07:57:09 Desktop NetworkManager[1167]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 16 07:57:09 Desktop NetworkManager[1167]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Apr 16 07:57:09 Desktop NetworkManager[1167]: <info> Activation (eth0) successful, device activated.
Apr 16 07:57:09 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 16 07:57:09 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 16 07:57:09 Desktop dbus[1153]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 16 07:57:09 Desktop dbus[1153]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 16 07:57:10 Desktop ltsp: # Creating dsa-hostkey for Desktop
Apr 16 07:57:10 Desktop ltsp: # Creating rsa-hostkey for Desktop
Apr 16 07:57:10 Desktop ltsp: # Creating ecdsa-hostkey for Desktop
Apr 16 07:57:10 Desktop ltsp: # Creating dsa-hostkey for 192.168.1.100
Apr 16 07:57:10 Desktop ltsp: # Creating rsa-hostkey for 192.168.1.100
Apr 16 07:57:10 Desktop ltsp: # Creating ecdsa-hostkey for 192.168.1.100
Apr 16 07:57:10 Desktop dnsmasq-dhcp[1277]: 2632737378 available DHCP subnet: 192.168.1.1/255.255.255.0
Apr 16 07:57:10 Desktop dnsmasq-dhcp[1277]: 2632737378 client provides name: android_3e43580ea6c26412
Apr 16 07:57:10 Desktop dnsmasq-dhcp[1277]: 2632737378 vendor class: dhcpcd 4.0.15
Apr 16 07:57:10 Desktop dnsmasq-dhcp[1277]: 2632737378 available DHCP subnet: 192.168.1.1/255.255.255.0
Apr 16 07:57:10 Desktop dnsmasq-dhcp[1277]: 2632737378 client provides name: android_3e43580ea6c26412
Apr 16 07:57:10 Desktop dnsmasq-dhcp[1277]: 2632737378 vendor class: dhcpcd 4.0.15
Apr 16 07:57:18 Desktop kernel: [238558.096452] eth0: no IPv6 routers present
Apr 16 07:57:19 Desktop nss_wins[10415]: adjust time server 91.189.94.4 offset -0.016068 sec
Apr 16 07:57:21 Desktop kernel: [238561.164467] usb 2-3: device descriptor read/64, error -110
Apr 16 07:57:28 Desktop NetworkManager[1167]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 16 07:57:28 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Apr 16 07:57:28 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr 16 07:57:28 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 16 07:57:28 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 16 07:57:28 Desktop NetworkManager[1167]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr 16 07:57:37 Desktop kernel: [238576.380482] usb 2-3: device descriptor read/64, error -110
Apr 16 07:57:37 Desktop kernel: [238576.596485] usb 2-3: new high speed USB device number 3 using ehci_hcd
Apr 16 07:57:52 Desktop kernel: [238591.708260] usb 2-3: device descriptor read/64, error -110
Apr 16 07:58:05 Desktop AptDaemon: INFO: Quitting due to inactivity
Apr 16 07:58:05 Desktop AptDaemon: INFO: Quitting was requested
Apr 16 07:58:05 Desktop dbus[1153]: [system] Activating service name='org.debian.apt' (using servicehelper)
Apr 16 07:58:06 Desktop AptDaemon: INFO: Initializing daemon
Apr 16 07:58:06 Desktop dbus[1153]: [system] Successfully activated service 'org.debian.apt'
Apr 16 07:58:06 Desktop AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Apr 16 07:58:06 Desktop AptDaemon.Trans: INFO: Simulate was called
Apr 16 07:58:06 Desktop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/0865d48d45af45cbb1502cd2e5a12d07
Apr 16 07:58:07 Desktop kernel: [238606.924101] usb 2-3: device descriptor read/64, error -110
Apr 16 07:58:07 Desktop AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Apr 16 07:58:07 Desktop kernel: [238607.140097] usb 2-3: new high speed USB device number 4 using ehci_hcd
Apr 16 07:58:18 Desktop kernel: [238617.548413] usb 2-3: device not accepting address 4, error -110
Apr 16 07:58:18 Desktop kernel: [238617.660487] usb 2-3: new high speed USB device number 5 using ehci_hcd
Apr 16 07:58:28 Desktop kernel: [238628.068470] usb 2-3: device not accepting address 5, error -110
Apr 16 07:58:28 Desktop kernel: [238628.068504] hub 2-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:58:28 Desktop kernel: [238628.192620] usb 2-4: new high speed USB device number 6 using ehci_hcd
Apr 16 07:58:29 Desktop mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-4"
Apr 16 07:58:29 Desktop kernel: [238628.336710] scsi18 : usb-storage 2-4:1.0
Apr 16 07:58:29 Desktop kernel: [238628.560529] usb 3-5: new high speed USB device number 3 using ehci_hcd
Apr 16 07:58:29 Desktop kernel: [238628.694903] hub 3-5:1.0: USB hub found
Apr 16 07:58:29 Desktop kernel: [238628.695072] hub 3-5:1.0: 2 ports detected
Apr 16 07:58:29 Desktop kernel: [238628.956455] usb 4-2: new full speed USB device number 10 using ohci_hcd
Apr 16 07:58:29 Desktop mtp-probe: checking bus 4, device 10: "/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2"
Apr 16 07:58:29 Desktop kernel: [238629.138807] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input31
Apr 16 07:58:29 Desktop kernel: [238629.139033] generic-usb 0003:046D:C318.001C: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:00:12.0-2/input0
Apr 16 07:58:29 Desktop mtp-probe: bus: 4, device: 10 was not an MTP device
Apr 16 07:58:29 Desktop mtp-probe: bus: 2, device: 6 was not an MTP device
Apr 16 07:58:29 Desktop kernel: [238629.146371] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input32
Apr 16 07:58:29 Desktop kernel: [238629.146631] generic-usb 0003:046D:C318.001D: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:00:12.0-2/input1
Apr 16 07:58:30 Desktop kernel: [238629.340535] scsi 18:0:0:0: Direct-Access     Memorex  Flashdrive 601B  PMAP PQ: 0 ANSI: 0 CCS
Apr 16 07:58:30 Desktop kernel: [238629.375991] sd 18:0:0:0: Attached scsi generic sg3 type 0
Apr 16 07:58:30 Desktop kernel: [238629.378638] sd 18:0:0:0: [sdc] 977664 512-byte logical blocks: (500 MB/477 MiB)
Apr 16 07:58:30 Desktop kernel: [238629.380594] sd 18:0:0:0: [sdc] Write Protect is off
Apr 16 07:58:30 Desktop kernel: [238629.380604] sd 18:0:0:0: [sdc] Mode Sense: 23 00 00 00
Apr 16 07:58:30 Desktop kernel: [238629.381735] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.381743] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.390968] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.390977] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.395238]  sdc: sdc1
Apr 16 07:58:30 Desktop kernel: [238629.397886] sd 18:0:0:0: [sdc] No Caching mode page present
Apr 16 07:58:30 Desktop kernel: [238629.397896] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Apr 16 07:58:30 Desktop kernel: [238629.397905] sd 18:0:0:0: [sdc] Attached SCSI removable disk
Apr 16 07:58:30 Desktop kernel: [238629.412445] usb 6-3: new full speed USB device number 42 using ohci_hcd
Apr 16 07:58:45 Desktop kernel: [238644.548488] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:00 Desktop kernel: [238659.788364] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:00 Desktop kernel: [238660.028369] usb 6-3: new full speed USB device number 43 using ohci_hcd
Apr 16 07:59:15 Desktop kernel: [238675.164425] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:31 Desktop kernel: [238690.404491] usb 6-3: device descriptor read/64, error -110
Apr 16 07:59:31 Desktop kernel: [238690.644449] usb 6-3: new full speed USB device number 44 using ohci_hcd
Apr 16 07:59:41 Desktop kernel: [238701.052456] usb 6-3: device not accepting address 44, error -110
Apr 16 07:59:41 Desktop kernel: [238701.188437] usb 6-3: new full speed USB device number 45 using ohci_hcd
Apr 16 07:59:52 Desktop kernel: [238711.596363] usb 6-3: device not accepting address 45, error -110
Apr 16 07:59:52 Desktop kernel: [238711.596417] hub 6-0:1.0: unable to enumerate USB device on port 3
Apr 16 07:59:52 Desktop kernel: [238711.772485] usb 10-1: new full speed USB device number 18 using ohci_hcd
Apr 16 07:59:52 Desktop bluetoothd[1459]: HCI dev 0 registered
Apr 16 07:59:52 Desktop bluetoothd[1459]: Listening for HCI events on hci0
Apr 16 07:59:52 Desktop kernel: [238712.089488] usb 3-5.1: new low speed USB device number 4 using ehci_hcd
Apr 16 07:59:52 Desktop bluetoothd[1459]: HCI dev 0 up
Apr 16 07:59:52 Desktop bluetoothd[1459]: input-headset driver probe failed for device 76:8E:46:66:20:4C
Apr 16 07:59:52 Desktop bluetoothd[1459]: input-headset driver probe failed for device A0:75:91:A0:54:8C
Apr 16 07:59:52 Desktop bluetoothd[1459]: Adapter /org/bluez/1459/hci0 has been enabled
Apr 16 07:59:52 Desktop pulseaudio[2183]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Apr 16 07:59:52  pulseaudio[2183]: last message repeated 2 times
Apr 16 07:59:52 Desktop NetworkManager[1167]: <warn> (76:8E:46:66:20:4C): failed to look up interface index
Apr 16 07:59:52 Desktop NetworkManager[1167]: <info> BT device ANDROID BT (76:8E:46:66:20:4C) added (DUN NAP)
Apr 16 07:59:52 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): new Bluetooth device (driver: 'bluez' ifindex: 0)
Apr 16 07:59:52 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): exported as /org/freedesktop/NetworkManager/Devices/17
Apr 16 07:59:52 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): now managed
Apr 16 07:59:52 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 07:59:52 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): deactivating device (reason 'managed') [2]
Apr 16 07:59:52 Desktop NetworkManager[1167]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Apr 16 07:59:52 Desktop NetworkManager[1167]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Apr 16 07:59:52 Desktop mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb3/3-5/3-5.1"
Apr 16 07:59:52 Desktop kernel: [238712.205276] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb3/3-5/3-5.1/3-5.1:1.0/input/input33
Apr 16 07:59:52 Desktop kernel: [238712.205554] generic-usb 0003:15CA:00C3.001E: input,hidraw2: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:03:06.2-5.1/input0
Apr 16 07:59:52 Desktop NetworkManager[1167]: <info> (76:8E:46:66:20:4C): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Apr 16 07:59:53 Desktop mtp-probe: bus: 3, device: 4 was not an MTP device
Apr 16 08:03:06 Desktop AptDaemon: INFO: Quitting due to inactivity
Apr 16 08:03:06 Desktop AptDaemon: INFO: Quitting was requested
Apr 16 08:03:06 Desktop dbus[1153]: [system] Activating service name='org.debian.apt' (using servicehelper)
Apr 16 08:03:07 Desktop AptDaemon: INFO: Initializing daemon
Apr 16 08:03:07 Desktop dbus[1153]: [system] Successfully activated service 'org.debian.apt'
Apr 16 08:03:07 Desktop AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Apr 16 08:03:07 Desktop AptDaemon.Trans: INFO: Simulate was called
Apr 16 08:03:07 Desktop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/c3e834b86fa04b30881cd44e9cbecb58
Apr 16 08:03:08 Desktop AptDaemon.Worker: INFO: Upgrade system with safe mode: 1

```

Xorg.0.log
```

[238523.072] (II) config/udev: removing device USB Optical Mouse
[238523.118] (II) USB Optical Mouse: Close
[238523.119] (II) UnloadModule: "evdev"
[238523.119] (II) Unloading evdev
[238523.830] (II) AIGLX: Suspending AIGLX clients for VT switch
[238523.837] (II) fglrx(0): Backup framebuffer data.
[238523.987] (II) fglrx(0): Backup complete.
[238544.562] (II) AIGLX: Resuming AIGLX clients after VT switch
[238544.692] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[238544.706] (II) fglrx(0): User Preference Output DFP1 using refresh rate 60.0 Hz.
[238544.831] (II) fglrx(0): Hot-plug event occurs on device: 1:0:0 
[238545.228] (II) config/udev: removing device Logitech Logitech Illuminated Keyboard
[238545.234] (II) Logitech Logitech Illuminated Keyboard: Close
[238545.236] (II) UnloadModule: "evdev"
[238545.236] (II) Unloading evdev
[238545.237] (II) config/udev: removing device Logitech Logitech Illuminated Keyboard
[238545.267] (II) Logitech Logitech Illuminated Keyboard: Close
[238545.269] (II) UnloadModule: "evdev"
[238545.269] (II) Unloading evdev
[238629.200] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event3)
[238629.200] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[238629.200] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[238629.200] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[238629.200] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[238629.200] (**) Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event3"
[238629.200] (--) Logitech Logitech Illuminated Keyboard: Found 1 mouse buttons
[238629.200] (--) Logitech Logitech Illuminated Keyboard: Found scroll wheel(s)
[238629.200] (--) Logitech Logitech Illuminated Keyboard: Found relative axes
[238629.200] (--) Logitech Logitech Illuminated Keyboard: Found absolute axes
[238629.200] (II) evdev-grail: failed to open grail, no gesture support
[238629.200] (--) Logitech Logitech Illuminated Keyboard: Found keys
[238629.200] (II) Logitech Logitech Illuminated Keyboard: Configuring as mouse
[238629.200] (II) Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[238629.200] (II) Logitech Logitech Illuminated Keyboard: Adding scrollwheel support
[238629.200] (**) Logitech Logitech Illuminated Keyboard: YAxisMapping: buttons 4 and 5
[238629.200] (**) Logitech Logitech Illuminated Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[238629.200] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input32/event3"
[238629.200] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD)
[238629.200] (**) Option "xkb_rules" "evdev"
[238629.200] (**) Option "xkb_model" "pc105"
[238629.200] (**) Option "xkb_layout" "us"
[238629.200] (**) Option "xkb_variant" "altgr-intl"
[238629.200] (**) Option "xkb_options" "lv3:ralt_switch"
[238629.200] (EE) Logitech Logitech Illuminated Keyboard: failed to initialize for relative axes.
[238629.200] (II) Logitech Logitech Illuminated Keyboard: initialized for absolute axes.
[238629.202] (**) Logitech Logitech Illuminated Keyboard: (accel) keeping acceleration scheme 1
[238629.202] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration profile 0
[238629.202] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration factor: 2.000
[238629.202] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration threshold: 4
[238629.206] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event2)
[238629.206] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[238629.206] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[238629.206] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[238629.206] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[238629.206] (**) Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event2"
[238629.206] (--) Logitech Logitech Illuminated Keyboard: Found keys
[238629.206] (II) Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[238629.206] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input31/event2"
[238629.206] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD)
[238629.206] (**) Option "xkb_rules" "evdev"
[238629.206] (**) Option "xkb_model" "pc105"
[238629.206] (**) Option "xkb_layout" "us"
[238629.206] (**) Option "xkb_variant" "altgr-intl"
[238629.206] (**) Option "xkb_options" "lv3:ralt_switch"
[238712.284] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[238712.284] (II) No input driver/identifier specified (ignoring)
[238712.287] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event6)
[238712.287] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[238712.287] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[238712.287] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[238712.287] (**) USB Optical Mouse: always reports core events
[238712.287] (**) USB Optical Mouse: Device: "/dev/input/event6"
[238712.287] (--) USB Optical Mouse: Found 3 mouse buttons
[238712.287] (--) USB Optical Mouse: Found scroll wheel(s)
[238712.287] (--) USB Optical Mouse: Found relative axes
[238712.287] (--) USB Optical Mouse: Found x and y relative axes
[238712.287] (II) USB Optical Mouse: Configuring as mouse
[238712.287] (II) USB Optical Mouse: Adding scrollwheel support
[238712.287] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[238712.287] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[238712.287] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb3/3-5/3-5.1/3-5.1:1.0/input/input33/event6"
[238712.287] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[238712.287] (II) USB Optical Mouse: initialized for relative axes.
[238712.289] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[238712.289] (**) USB Optical Mouse: (accel) acceleration profile 0
[238712.289] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[238712.289] (**) USB Optical Mouse: (accel) acceleration threshold: 4

```

---

### Post by alanwalterthomas on 2012-04-23
Bump.
I've also noticed that system boot is also screwed.
The system pauses for a good minute or so while booting. No hard drive activity. Just sits for a while, then it continues. When I finally get to the desktop my usb keyboard doesn't work for a short while, neither does my mouse for a short while longer, and my Conky setup won't start either.

This is a seriously annoying problem. Please help. Any other system info/logs can be provided.

---

### Post by audiomick on 2012-04-23
Hi Alan. I'm sorry I can't help with your problem, but I would like to suggest that you use code tags when you post long output like that. That is the button at the top of the posting window that is marked # .
When you click on it, you get tags like this
[tag] paste your out put here [/tag]
where "code" is in place of "tag".

It puts the content in a nice box
```
like this
```

that has a scroll bar if the content is really long.

Makes life easier for people reading the thread. ;)

---

### Post by alanwalterthomas on 2012-05-10
Bump. USB is still problematic after upgrading to 12.04. The Kobo won't connect properly, and I have to wait a few minutes to use the mouse after resuming from suspend.
Anyone who understands USB, please help!

---

