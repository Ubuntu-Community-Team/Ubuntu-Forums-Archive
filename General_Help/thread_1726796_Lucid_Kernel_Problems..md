---
title: "Lucid Kernel Problems."
date: 2011-04-11
forum: General Help
---

### Post by Borfo on 2011-04-11
For the record, I'm having the same issue as the OP with Lucid with a backported 2.6.35-28 kernel and a Samsung scx-4623fw printer hooked up via USB.  Same symptoms - lsusb hangs until the printer is unplugged, devices aren't recognized, etc.  dmesg output includes a bunch of device descriptor errors:

[  603.091961] usb 7-1: new full speed USB device using ohci_hcd and address 9
[  618.241335] usb 7-1: device descriptor read/64, error -110
[  633.521986] usb 7-1: device descriptor read/64, error -110


I suddenly started having a bunch of USB issues (including complete system locks whenever I plugged in a logitech USB mic) around early march with the stock lucid kernel.  Everything was fine before that.

---

### Post by Borfo on 2011-04-11
...just rebooted into the 2.6.32-31 stock lucid kernel, still having the same problems.

---

### Post by uRock on 2011-04-11
Bump for move to separate thread.

---

### Post by Borfo on 2011-04-11
Somewhat surprisingly, I seem to have fixed this printer issue, at least temporarily, by turning the printer off and on.  Haha...  I've been having these usb "device descriptor" error issues with a bunch of different USB stuff since early march though, as I said, so I imagine there's more to this than just turning something off and on.  Nonetheless, things are ok for now apparently.

---

### Post by TeoBigusGeekus on 2011-04-11
Have you completely excluded hardware issues (motherboard I pressume)?
I'd try unplugging the power cord from it and reattaching it.
Just a suggestion...

---

