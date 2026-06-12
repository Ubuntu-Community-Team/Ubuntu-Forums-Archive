---
title: "Booting OS takes minutes"
date: 2012-09-23
forum: General Help
---

### Post by StarFishes on 2012-09-23
Hi @ll,

I'm running Ubuntu Server 12.04 with a Raid-5-array, system 's running fine, only one problem occurs when booting the machine. Then it takes up to three minutes to boot. When I initially installed the system, the booting procedure was pretty fast, I don't know what's causing the problem. Here is the syslog:

```
Sep 23 17:41:16 Aristoteles kernel: [    9.829321] usbcore: registered new interface driver btusb
Sep 23 17:41:16 Aristoteles kernel: [   10.572306] r8169 0000:09:00.0: eth0: link up
Sep 23 17:41:16 Aristoteles kernel: [   10.574017] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 23 17:41:16 Aristoteles kernel: [   21.520023] eth0: no IPv6 routers present
Sep 23 17:41:16 Aristoteles kernel: [  203.235511] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
Sep 23 17:41:16 Aristoteles kernel: [  203.379232] init: failsafe main process (1037) killed by TERM signal
Sep 23 17:41:16 Aristoteles kernel: [  203.440921] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 23 17:41:16 Aristoteles kernel: [  203.440930] Bluetooth: BNEP filters: protocol multicast
Sep 23 17:41:16 Aristoteles kernel: [  203.470569] Bluetooth: RFCOMM TTY layer initialized
S
```

Do you guys have an idea what could be wrong? Whether it is the network interface or the md I cannot tell. 

Any ideas or hints that could bring my system to former performance?

Thanks in advance, best regards
StarFishes

---

### Post by gordintoronto on 2012-09-23
Your syslog is incomplete.

Do you really need bluetooth on a server?

---

### Post by StarFishes on 2012-09-30
Hi again,

I thought this part of the log could support the least necessary information. I've added a complete syslog of the booting process (see the attachments).

The reason for bluetooth is easy: there is none! ;) I've just used a mainboard and use the machine as a file server, nothing else.

Does the log provide any further information?

Thanks!
StarFishes

---

### Post by HiImTye on 2012-10-01
```
Sep 30 12:38:30 Aristoteles bluetoothd[1083]: Adapter /org/bluez/1083/hci0 has been enabled 
Sep 30 12:38:33 Aristoteles kernel: [  206.823757] init: plymouth-upstart-bridge main process (1079) killed by TERM signal 
Sep 30 12:41:02 Aristoteles dbus[1072]: [system] Activating service
```this suggests that there is some error with the 'plymouth-upstart-bridge' process. I don't know much about plymouth unfortunately, but at least it gives you an idea of where to look

---

