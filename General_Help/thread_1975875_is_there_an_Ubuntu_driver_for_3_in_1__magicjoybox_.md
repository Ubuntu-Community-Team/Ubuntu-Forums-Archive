---
title: "is there an Ubuntu driver for 3 in 1  magicjoybox adapter"
date: 2012-05-08
forum: General Help
---

### Post by thed0ctor on 2012-05-08
I'm using the dolphin emulator and am wanting to use this 3 in 1 MagicJoyBox adapter I used for my Windows installation to connect my Gamecube controller. 

Is there a driver for this?

I did a couple lsusb's and it is registering but it doesn't appear to be a known device:

**Plugged in:**
```
thed0ctor@Tardis:~/Escritorio$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:0808 Logitech, Inc. Webcam C600
Bus 002 Device 003: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 005 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 004 Device 002: ID 050d:0084 Belkin Components F8T003v2 Bluetooth
**Bus 004 Device 004: ID 0926:2526 **
```

**Not plugged in:**
```

thed0ctor@Tardis:~/Escritorio$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:0808 Logitech, Inc. Webcam C600
Bus 002 Device 003: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 005 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 002: ID 050d:0084 Belkin Components F8T003v2 Bluetooth
```

**Plugged in again:**
```

thed0ctor@Tardis:~/Escritorio$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:0808 Logitech, Inc. Webcam C600
Bus 002 Device 003: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 005 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 005: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 004 Device 002: ID 050d:0084 Belkin Components F8T003v2 Bluetooth
**Bus 004 Device 006: ID 0926:2526  **
```

---

