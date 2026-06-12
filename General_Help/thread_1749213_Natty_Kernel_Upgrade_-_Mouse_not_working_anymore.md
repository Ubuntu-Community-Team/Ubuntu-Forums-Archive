---
title: "Natty Kernel Upgrade - Mouse not working anymore"
date: 2011-05-04
forum: General Help
---

### Post by xaitax on 2011-05-04
Hi,

since I just upgraded my Natty to the new Kernel my Logitech USB mouse won't work anymore. I checked it on another notebook and the mouse works fine Before the upgrade, everything was fine as well.

```
xaitax@w00t:~$ uname -a
Linux w00t 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:23:06 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

```
xaitax@w00t:~$ lsusb
Bus 003 Device 005: ID 046d:c526 Logitech, Inc. Nano Receiver

```

```
May  4 18:15:35 w00t kernel: [ 5001.982499] usb 3-3: new full speed USB device using xhci_hcd and address 5
May  4 18:15:35 w00t kernel: [ 5002.011330] xhci_hcd 0000:0f:00.0: WARN: Stalled endpoint
May  4 18:15:35 w00t kernel: [ 5002.013386] xhci_hcd 0000:0f:00.0: WARN: Stalled endpoint
May  4 18:15:35 w00t kernel: [ 5002.015417] xhci_hcd 0000:0f:00.0: WARN: Stalled endpoint
May  4 18:15:35 w00t kernel: [ 5002.026353] xhci_hcd 0000:0f:00.0: WARN: short transfer on control ep
May  4 18:15:35 w00t kernel: [ 5002.030359] xhci_hcd 0000:0f:00.0: WARN: short transfer on control ep
May  4 18:15:35 w00t kernel: [ 5002.034354] xhci_hcd 0000:0f:00.0: WARN: short transfer on control ep
May  4 18:15:35 w00t kernel: [ 5002.036739] xhci_hcd 0000:0f:00.0: ERROR: unexpected command completion code 0x11.
May  4 18:15:35 w00t kernel: [ 5002.036755] usb 3-3: can't set config #1, error -22

```

Does anyone have an idea? I guess the "error -22" is the interesting one.

Thanks in advance,
xai

---

### Post by xaitax on 2011-05-04
Seems to be a known bug for a while.
[http://permalink.gmane.org/gmane.linux.usb.general/45700](http://permalink.gmane.org/gmane.linux.usb.general/45700)

Nobody else ran into this issue?

/xai

---

### Post by xaitax on 2011-05-05
*selfbump*

Unfortunately, I cannot find anything on the Internet regarding this and I am running out of ideas.

/xai

---

### Post by iq2luc on 2011-05-05
Same problem. Seems commit 926008c9386dde09b015753b6681c502177baa30 is to be blamed. I hope they will fix it soon.

---

