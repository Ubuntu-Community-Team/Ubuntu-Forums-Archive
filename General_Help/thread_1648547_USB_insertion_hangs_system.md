---
title: "USB insertion hangs system"
date: 2010-12-18
forum: General Help
---

### Post by _Duhhh on 2010-12-18
I'm running Ubuntu 10.10, 64-bit on an HP 8740w. Sometimes (I don't have the frequency yet, but it has happened a half-dozen times in the past couple of weeks) when I insert a USB storage device the system hangs, requiring a power-cycle. I have been careful to either eject or "safely remove" every USB device, but it still happens. I believe it only happens when I remove a device and later re-insert it, but I don't have enough data points to be sure.

Most of the time, I'm running VirtualBox, but I haven't captured the USB device in a VM.

First question - how can I go about figuring out what might be going wrong? Once it happens, my options are extremely limited (power switch). When this happened one time I left the system for 30+ minutes, and it did not recover.

Of course, when I wanted to see it, I did 10 insertions/removals without a hang. :mad:

Thanks for any suggestions

---

### Post by HermanAB on 2010-12-19
Hmm, I once had to find a problem in an aircraft system that happened once in 6000 tries...

You should look at the main system log file:
$ sudo tail -n 1000 -f /var/log/messages

You got to go back to before the current startup, to find the spot where it died.  The -n parameter will do that.  Read the tail man page for details.

---

### Post by _Duhhh on 2010-12-19
The log gives no clue. Here's the log from the time I inserted the USB key, then pulled it out, and a minute later re-inserted it, which locked up the system, and I had to power off.

```

Dec 18 22:42:38 HP8740w kernel: [22261.894914] usb 3-3: new high speed USB device using xhci_hcd and address 0
Dec 18 22:42:38 HP8740w kernel: [22261.917657] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Dec 18 22:42:38 HP8740w kernel: [22261.919778] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Dec 18 22:42:38 HP8740w kernel: [22261.921772] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Dec 18 22:42:38 HP8740w kernel: [22261.923947] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Dec 18 22:42:38 HP8740w kernel: [22261.925087] scsi12 : usb-storage 3-3:1.0
Dec 18 22:42:39 HP8740w kernel: [22262.958796] scsi 12:0:0:0: Direct-Access     Kingston DataTraveler G3  PMAP PQ: 0 ANSI: 0 CCS
Dec 18 22:42:39 HP8740w kernel: [22262.960921] sd 12:0:0:0: Attached scsi generic sg2 type 0
Dec 18 22:42:40 HP8740w kernel: [22264.169718] sd 12:0:0:0: [sdb] 15622144 512-byte logical blocks: (7.99 GB/7.44 GiB)
Dec 18 22:42:40 HP8740w kernel: [22264.170151] sd 12:0:0:0: [sdb] Write Protect is off
Dec 18 22:42:40 HP8740w kernel: [22264.173147]  sdb: sdb1
Dec 18 22:42:40 HP8740w kernel: [22264.200174] sd 12:0:0:0: [sdb] Attached SCSI removable disk
Dec 18 22:43:31 HP8740w kernel: [22315.719460] usb 3-3: USB disconnect, address 2
Dec 18 22:44:24 HP8740w kernel: [22368.646691] usb 3-3: new high speed USB device using xhci_hcd and address 0
Dec 18 22:44:24 HP8740w kernel: [22368.673666] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Dec 18 22:44:24 HP8740w kernel: [22368.675723] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Dec 18 22:44:24 HP8740w kernel: [22368.677743] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Dec 18 22:44:24 HP8740w kernel: [22368.679818] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Dec 18 22:44:24 HP8740w kernel: [22368.681254] scsi13 : usb-storage 3-3:1.0
Dec 18 22:44:26 HP8740w kernel: [22369.713384] scsi 13:0:0:0: Direct-Access     Kingston DataTraveler G3  PMAP PQ: 0 ANSI: 0 CCS
Dec 18 22:44:26 HP8740w kernel: [22369.715523] sd 13:0:0:0: Attached scsi generic sg2 type 0
Dec 18 22:44:27 HP8740w kernel: [22370.922778] sd 13:0:0:0: [sdb] 15622144 512-byte logical blocks: (7.99 GB/7.44 GiB)
Dec 18 22:44:27 HP8740w kernel: [22370.923242] sd 13:0:0:0: [sdb] Write Protect is off
Dec 18 22:44:27 HP8740w kernel: [22370.926065]  sdb: sdb1
Dec 18 22:44:27 HP8740w kernel: [22370.952959] sd 13:0:0:0: [sdb] Attached SCSI removable disk
Dec 18 22:52:58 HP8740w kernel: imklog 4.2.0, log source = /proc/kmsg started.

```Both insertions look the same, it's just that the second one caused it to hang.

I knew this one was going to be tough.

---

### Post by drumsticks on 2010-12-29
Me too!  I'm running Ubuntu 10.10 Maverick 64-bits on a Dell XPS 15 (L501x) and have exactly the same problem: infrequent unpredictable lockups requiring power cycles.  Log messages gives no hint as to what the problem might be (and it looks almost the same as Duhhh's).

The same USB stick works perfectly on another installation of Ubuntu 10.10 Maverick 64-bits on a Dell XPS M1530.

---

### Post by _Duhhh on 2011-01-03
I have not been able to recreate the hang in a week, and the only thing I've changed is that I make sure I'm running top whenever I insert or remove a USB device.

The only thing I've done to my system since installation was to get ACPI to work. I added:
```
SUSPEND_MODULES=xhci-hcd
```to /etc/pmconfig.d/00sleeep_module and /etc/pm/config.d/unload_module. That allowed the system to sleep, but then I had to add:
```
echo disable > /sys/firmware/acpi/interrupts/gpe01
```to /etc/rc.local, which kept kacpid from chewing up CPU on resume.

If I could replicate the hang with any regularity, I might be able to figure out if there is a conection.

---

### Post by drumsticks on 2011-01-05
Duhhh, why would top make any difference?  How did you come to that idea?  I'll try doing the same for awhile and see what happens, but I don't understand why it would make any difference at all!

---

### Post by _Duhhh on 2011-01-05
It shouldn't make any difference, but when the system hangs, I want some indication of what's running at the time. If the video doesn't hang, and top is running, I can at least see what processes are still running. Unfortunately, I got a hang yesterday, and the display was also frozen, so I got no new info (although I did get a hint - I had let a VirtualBox VM touch the USB device, and after releasing it, the system hung).

---

### Post by _Duhhh on 2011-01-05
I found a new wrinkle. If I involve VirtualBox, it seems to happen a lot more frequently. I have been able to get it to happen by connecting the USB device to a VM, and then shutting the VM down, or by connecting it to the VM and then disconnecting it. In some cases this works (and the device is re-mounted). Other times it isn't re-mounted, and if I unplug it, the system hangs.

Here's a log from yesterday, which seems to show that the device was reclaimed from the VM, but that caused the hang.

```

Jan  4 18:05:14 HP8740w kernel: [ 2552.933368] usb 3-3: new high speed USB device using xhci_hcd and address 0
Jan  4 18:05:14 HP8740w kernel: [ 2552.956146] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:14 HP8740w kernel: [ 2552.958142] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:14 HP8740w kernel: [ 2552.960140] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:14 HP8740w kernel: [ 2552.962388] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:14 HP8740w kernel: [ 2552.963601] scsi9 : usb-storage 3-3:1.0
Jan  4 18:05:15 HP8740w kernel: [ 2554.001200] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler G3  PMAP PQ: 0 ANSI: 0 CCS
Jan  4 18:05:15 HP8740w kernel: [ 2554.003252] sd 9:0:0:0: Attached scsi generic sg2 type 0
Jan  4 18:05:16 HP8740w kernel: [ 2555.208888] sd 9:0:0:0: [sdb] 15622144 512-byte logical blocks: (7.99 GB/7.44 GiB)
Jan  4 18:05:16 HP8740w kernel: [ 2555.209131] sd 9:0:0:0: [sdb] Write Protect is off
Jan  4 18:05:17 HP8740w kernel: [ 2555.211446]  sdb: sdb1
Jan  4 18:05:17 HP8740w kernel: [ 2555.237532] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Jan  4 18:05:24 HP8740w kernel: [ 2562.710869] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:24 HP8740w kernel: [ 2562.932171] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:24 HP8740w kernel: [ 2562.936918] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:24 HP8740w kernel: [ 2562.942161] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:24 HP8740w kernel: [ 2562.948794] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:24 HP8740w kernel: [ 2562.952665] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:24 HP8740w kernel: [ 2562.958003] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:24 HP8740w kernel: [ 2562.960899] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:24 HP8740w pulseaudio[1897]: ratelimit.c: 469 events suppressed
Jan  4 18:05:37 HP8740w kernel: [ 2575.852682] usb 3-3: reset high speed USB device using xhci_hcd and address 2
Jan  4 18:05:37 HP8740w kernel: [ 2575.875219] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jan  4 18:05:37 HP8740w kernel: [ 2575.875409] xhci_hcd 0000:45:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021d458880
Jan  4 18:05:37 HP8740w kernel: [ 2575.875415] xhci_hcd 0000:45:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021d4588c0
Jan  4 18:05:37 HP8740w kernel: [ 2575.876441] scsi10 : usb-storage 3-3:1.0
Jan  4 18:05:38 HP8740w pulseaudio[1897]: ratelimit.c: 472 events suppressed
Jan  4 18:05:38 HP8740w kernel: [ 2576.873154] scsi 10:0:0:0: Direct-Access     Kingston DataTraveler G3  PMAP PQ: 0 ANSI: 0 CCS
Jan  4 18:05:38 HP8740w kernel: [ 2576.874300] sd 10:0:0:0: Attached scsi generic sg2 type 0
Jan  4 18:05:38 HP8740w kernel: [ 2576.875359] sd 10:0:0:0: [sdb] 15622144 512-byte logical blocks: (7.99 GB/7.44 GiB)
Jan  4 18:05:38 HP8740w kernel: [ 2576.875586] sd 10:0:0:0: [sdb] Write Protect is off
Jan  4 18:05:38 HP8740w kernel: [ 2576.877693]  sdb: sdb1
Jan  4 18:05:38 HP8740w kernel: [ 2576.880063] sd 10:0:0:0: [sdb] Attached SCSI removable disk
Jan  4 18:06:08 HP8740w pulseaudio[1897]: ratelimit.c: 485 events suppressed
Jan  5 11:36:14 HP8740w kernel: imklog 4.2.0, log source = /proc/kmsg started.

```

---

### Post by happyhamster on 2011-01-05
Does the hang perhaps happen with the usb 3.0 ports only? I ask because the xhci_hcd driver appears to be in active development still (see for example: [http://groups.google.com/group/linux.kernel/browse_thread/thread/0b412b077f38d777/ad9ee08ae3b43297?lnk=raot](http://groups.google.com/group/linux.kernel/browse_thread/thread/0b412b077f38d777/ad9ee08ae3b43297?lnk=raot))

Try testing the regular usb 2.0 port (which should default to the older ehci/ohci drivers).

---

### Post by _Duhhh on 2011-01-05
Good idea! I hadn't been using the EHCI ports because they're on the wrong side of the box, but a quick test could not duplicate a hang (far from conclusive, but promising). I'll keep working down this avenue, and check out the problem from an exclusively XHCI angle.

---

### Post by drumsticks on 2011-01-05
I hadn't realised that I even had a USB2 port on my computer (Dell XPS15 L501x)!  I thought all 3 ports were USB3.  Turns out one of them is a USB2/eSATA port.  I'll try sticking to this USB2 port for now :)

Also, as pointed out, the frequency of occurrence seems to increase with virtual machines, though I use VMware instead of Virtualbox.

---

### Post by drumsticks on 2011-01-17
After a week of using the system, it looks like all is well if I used the USB2 port.  Problem effectively solved, though it would be nice to be able to use the other ports without fear of lockup!

---

### Post by dubski on 2011-04-28
I'm also getting this hanging problem. Seems to happen when I start copying to or from the device. Looks like it's using USB 2 driver. It happens 99% of the time. The system hangs and you can't even CTRL ALT F1 to a terminal login. It's been happening for months. On the same computer it doesn't happen when I boot into Win XP so it's not obvious (bus possible) that this is a hardware fault.


```
Apr 28 17:27:38 Baelrion kernel: [  265.036522] Bluetooth: HCI device and connection manager initialized
Apr 28 17:27:38 Baelrion kernel: [  265.036524] Bluetooth: HCI socket layer initialized
Apr 28 17:27:38 Baelrion kernel: [  265.092900] Bluetooth: L2CAP ver 2.14
Apr 28 17:27:38 Baelrion kernel: [  265.092906] Bluetooth: L2CAP socket layer initialized
Apr 28 17:27:39 Baelrion kernel: [  265.976542] Bluetooth: RFCOMM TTY layer initialized
Apr 28 17:27:39 Baelrion kernel: [  265.976555] Bluetooth: RFCOMM socket layer initialized
Apr 28 17:27:39 Baelrion kernel: [  265.976561] Bluetooth: RFCOMM ver 1.11
Apr 28 17:29:39 Baelrion kernel: [  386.433182] lo: Disabled Privacy Extensions
Apr 28 17:33:22 Baelrion kernel: [  609.500051] usb 2-6: new high speed USB device using ehci_hcd and address 2
Apr 28 17:33:23 Baelrion kernel: [  609.688340] Initializing USB Mass Storage driver...
Apr 28 17:33:23 Baelrion kernel: [  609.688670] scsi6 : usb-storage 2-6:1.0
Apr 28 17:33:23 Baelrion kernel: [  609.689171] usbcore: registered new interface driver usb-storage
Apr 28 17:33:23 Baelrion kernel: [  609.689176] USB Mass Storage support registered.
Apr 28 17:33:24 Baelrion kernel: [  610.685918] scsi 6:0:0:0: Direct-Access     pqi      IntelligentStick 0.00 PQ: 0 ANSI: 2
Apr 28 17:33:24 Baelrion kernel: [  610.687846] sd 6:0:0:0: Attached scsi generic sg4 type 0
Apr 28 17:33:24 Baelrion kernel: [  610.689394] sd 6:0:0:0: [sdd] 31582352 512-byte logical blocks: (16.1 GB/15.0 GiB)
Apr 28 17:33:24 Baelrion kernel: [  610.690022] sd 6:0:0:0: [sdd] Write Protect is off
Apr 28 17:33:24 Baelrion kernel: [  610.694524]  sdd: sdd1
Apr 28 17:33:24 Baelrion kernel: [  611.001875] sd 6:0:0:0: [sdd] Attached SCSI removable disk
Apr 28 17:36:34 Baelrion kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr 28 17:36:34 Baelrion rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1184" x-info="http://www.rsyslog.com"] (re)start
Apr 28 17:36:34 Baelrion rsyslogd: rsyslogd's groupid changed to 103
Apr 28 17:36:34 Baelrion rsyslogd: rsyslogd's userid changed to 101
Apr 28 17:36:34 Baelrion kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 28 17:36:34 Baelrion kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 28 17:36:34 Baelrion kernel: [    0.000000] Linux version 2.6.35-29-generic-pae (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #51-Ubuntu SMP Fri Apr 15 18:57:47 UTC 2011 (Ubuntu 2.6.35-29.51-generic-pae 2.6.35.12)
```

---

