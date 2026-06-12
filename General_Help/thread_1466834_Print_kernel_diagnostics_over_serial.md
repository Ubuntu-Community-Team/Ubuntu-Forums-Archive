---
title: "Print kernel diagnostics over serial?"
date: 2010-04-30
forum: General Help
---

### Post by theevilhamster on 2010-04-30
Hi,

I have a serial text only printer hocked up to /dev/ttyUSB0, and I want to print all new kernel diagnostics messages form dmesg as they happen. The following prints all messages, but I only want new ones, so I have a hardware log if that makes sense!

```
sudo dmesg > /dev/ttyUSB0
```

Many thanks all!

---

