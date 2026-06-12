---
title: "Insatall  a New Logitech Wireless Track Ball Mouse"
date: 2009-10-17
forum: General Help
---

### Post by waltwin on 2009-10-17
I purchased and just received a new Logitech,Wireless Trackball mouse. I have the software disk and I have spent the last several hours trying to install the software.

When I insert it into my CD drive it loads but I can't seem to figure out what to do next. I have been reading several documents on line but I just can't seem to get my arms around this loading procedure. 

I have been trying to use the document referenced by ubuntu: Ubuntu pocket guide and reference by Keir Thomas but I still don't get it.

I would appreciate any help and perhaps some other reference material.

Thank you 

waltwin :confused:

---

### Post by Sef on 2009-10-17
What happens when you plug the base in? Does it detect the mouse?

---

### Post by waltwin on 2009-10-17
> **Sef said:**
> What happens when you plug the base in? Does it detect the mouse?
NO. It's not like when I plug in a corded mouse which was detected immediately.

---

### Post by Sef on 2009-10-17
1) Have you made sure the batteries are good?

2) Have you (from the terminal) typed in **lsusb** to see if the mouse is being detected at all.  Paste the results here.


Open the Terminal: Applications > Accessories > Terminal

---

### Post by waltwin on 2009-10-17
> **Sef said:**
> 1) Have you made sure the batteries are good?

2) Have you (from the terminal) typed in **lsusb** to see if the mouse is being detected at all.  Paste the results here.


Open the Terminal: Applications > Accessories > Terminal
walt@walt-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 002: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
walt@walt-desktop:~$

---

### Post by waltwin on 2009-10-17
> **waltwin said:**
> walt@walt-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 002: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
walt@walt-desktop:~$
II did check the battery and it is good. I, for the umpteenth time hit the connect buttons on the receiver and mouse and now it seems to work OK. Its all magic I guess.

---

### Post by waltwin on 2009-10-17
> **waltwin said:**
> II did check the battery and it is good. I, for the umpteenth time hit the connect buttons on the receiver and mouse and now it seems to work OK. Its all magic I guess.
Everything seems to be working now. Thanks for the help.

waltwin

---

