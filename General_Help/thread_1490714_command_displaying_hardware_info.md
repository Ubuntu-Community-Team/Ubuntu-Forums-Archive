---
title: "command displaying hardware info"
date: 2010-05-22
forum: General Help
---

### Post by pizza-is-good on 2010-05-22
Hi all.

I feel really stupid. Just last week I used this command that displayed all of your hardware info, with serial numbers and ports were it was plugged in, but now I can't remember it. I've googled and looked, but can't find it. I've also tried to look through my shell's history, but it doesn't go that far back.

I know it was nothing too mysterious...

Anyway, now I need it to find which port my rfid card is plugged into.

Thanks.

~pizza

---

### Post by Zemblan on 2010-05-22
"sudo lshw" will show a pretty comprehensive list of the hardware your machine has. Might want to pipe it through grep to search for the specific entry you want.

---

### Post by pizza-is-good on 2010-05-22
Thanks, that was the one I was looking for.
I looked through all of it and I can't find my smart card reader however. Any idea on how I might do that?
I need to find which port it is plugged in to.

---

### Post by Zemblan on 2010-05-22
If you know a string that is likely to turn up in the output of 'lshw'(like the manufacturer's name) then you can pipe the output to 'grep' and use grep to search for it, so:

"sudo lshw | grep -s -B 2 -C 2 <some relevant string>"

You could also try "lspci"

---

### Post by pizza-is-good on 2010-05-22
ok, since I read from some other forum that the card was plugged in via usb, I went ahead and tried lsusb.

Here is what I got:```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor[/COLOR]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 046d:c50c Logitech, Inc. Cordless Desktop S510
Bus 001 Device 006: ID 044f:b106 ThrustMaster, Inc. 
Bus 001 Device 005: ID 0c45:63f8 Microdia Sonix Integrated Webcam
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 002: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```The one in red is my rfid card. Where is it mounted? Is it /dev/ttyUSB2, or what would it be?

---

### Post by pizza-is-good on 2010-05-22
OK, actually, the thread is solved, so I'll mark it as such and start a new one for the rfid reader problem.

Thanks for the help.

~pizza

---

