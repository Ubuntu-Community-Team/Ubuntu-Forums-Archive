---
title: "Asrock does not wake up after suspend"
date: 2011-09-09
forum: General Help
---

### Post by pezlin on 2011-09-09
Hi!

I ran Update manager a couple a days ago and after that the computer (Asrock 330) does not wake up from suspend. I noticed it when trying to use the remote control but neither this or the mouse (wireless) or keyboard (wired) is working to wake the computer up. *Edit* The computer wakes up if I press the power button or disconnects the keyboard from the usb port.

It has all been fine until after running Update manager. It was probably a couple of months since I last ran it so I don't know what was been updated.

Result from running cat /proc/acpi/wakeup:
SMB0      S4     disabled  pci:0000:00:03.2
USB0      S4     enabled   pci:0000:00:04.0
USB2      S4     disabled  pci:0000:00:04.1

I have tried to enable USB2 as well but it didn't help.

Current setup: Ubuntu 10.04 LTS 2.6.32-33-generic #70

Anyone has any suggestions?

---

### Post by pezlin on 2011-09-12
Noone?

---

### Post by raja.genupula on 2011-09-12
[http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep](http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep)

---

### Post by pezlin on 2011-09-13
> **raja.genupula said:**
> [http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep](http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep)
 
Sorry but this is no laptop so if I understood it correctly the link above did not give me anything. The starnge thing is that it has been working with 10.04 for a long time and it just stopped working after a recent update. I don't know what was updated but I have been using 10.04 for a while and it has been working before.

---

### Post by pezlin on 2011-09-21
No one else who has this problem?

---

### Post by pezlin on 2011-10-18
Hi again,
 
I have noticed that when the computer is in sleep mode pressing the remote control will wake the ir receiver but not the computer. Any suggestions?

---

