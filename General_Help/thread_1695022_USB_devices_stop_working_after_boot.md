---
title: "USB devices stop working after boot"
date: 2011-02-25
forum: General Help
---

### Post by Sirion on 2011-02-25
Hi all,

I hope this is the right board for my question. I have a very strange problem with my Ubuntu 10.04 installation on one of my machines (but it also happens when using the live CD of 10.10, both x64 and the x86 alternative installer): 

When grub starts, I can use my USB-keyboard to choose, after that, neither keyboard nor mouse or external harddrive are recognized by the system.

The mouse does still get power from the usb (the red sensor-light (?) is still working), but I cannot use it.
I tried the 10.10 x64 live CD with the same result - I can choose language and keyboard-layout and start the live-system using my usb-keyboard, but cannot use it after that.

Then I tried booting from a usb-stick with a 32-bit version and the same problem occurred, also with the alternate installer iso - as soon as the language choice menu (of the installer) was shown, my keyboard stopped working.

It worked flawlessly in the past, but I don't really know since when the problem exists, because I use the machine via synergy and only noticed it when i tried to attach an external drive.

I deduct from that, that it can neither be a hardware issue nor a problem of the specific ubuntu version or the used architecture (x86 vs. x64).

Did anyone of you ever encounter a problem like this and maybe has a tip for me what I can try to narrow down (or fix) the problem?

Best regards,
Jens

PS: Pardon my English, it's not my native language.

---

### Post by rnerwein on 2011-02-25
hallo
ich hab da leider keine lösung - aber wenn es dich etwas tröstest schau dir  die folgenden einträge meines kern.log an:Feb 25 15:38:20 tschang kernel: [ 1502.854989] 2:3:1: cannot get freq at ep 0x84
Feb 25 15:39:41 tschang kernel: [ 1584.363507] 2:3:1: cannot get freq at ep 0x84
Feb 25 16:00:23 tschang kernel: [ 2825.840257] usb 2-5: reset high speed USB device using ehci_hcd and address 5
Feb 25 16:01:39 tschang kernel: [ 2901.842729] usb 2-5: reset high speed USB device using ehci_hcd and address 5
Feb 25 16:03:13 tschang kernel: [ 2995.842524] usb 2-5: reset high speed USB device using ehci_hcd and address 5
Feb 25 16:11:05 tschang kernel: [ 3467.840085] usb 2-5: reset high speed USB device using ehci_hcd and address 5
Feb 25 16:14:17 tschang kernel: [ 3659.842525] usb 2-5: reset high speed USB device using ehci_hcd and address 5

du bist also nicht allein.
anbei - boote ich windoof oder suse ist da kein problem.
bei mir ist es "zum glück" nur die web-cam.
ciao

---

### Post by Sirion on 2011-02-25
(Ich schreibe weiter auf Englisch um möglist viele potentielle Helfer zu erreichen)

I have tested what entries were added to the log-files when plugging in (and out) USB devices by watching the change date of all files in the "/var/log"-directory

I used the following command while watching the modification date of the files:
```
sudo watch "ls -lhat /var/log/ | grep -v \.gz"
```

Result: Nothing changed. No messages were added to any of the log files. :-(

---

### Post by Sirion on 2011-02-25
I grepped /var/log/dmesg for all USB-related messages, this was the output:

```

[    0.420224] usbcore: registered new interface driver usbfs
[    0.420224] usbcore: registered new interface driver hub
[    0.420224] usbcore: registered new device driver usb
[    0.570623] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.571199] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.590114] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.590250] usb usb1: configuration #1 chosen from 1 choice
[    0.590284] hub 1-0:1.0: USB hub found
[    0.590369] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.600717] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.652467] usb usb2: configuration #1 chosen from 1 choice
[    0.652507] hub 2-0:1.0: USB hub found
[    0.652602] uhci_hcd: USB Universal Host Controller Interface driver
[    1.300037] usb 2-3: new low speed USB device using ohci_hcd and address 2
```

Does any of those messages hint at a problem?

---

### Post by Sirion on 2011-02-25
I found a solution - there is a new Bios version out for the mainboard which solved the problem. Which is weird, because it worked with the old bios version before.

Thank you,
Jens

---

