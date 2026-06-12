---
title: "A small issue with the boot process"
date: 2011-06-27
forum: General Help
---

### Post by Nyromith on 2011-06-27
Hello,

Every time I boot, and before the GUI loads, tty1 displays a login prompt, and the line below shows this:
```
usb_submit_urb(ctrl) failed
```

I looked at the kernel log, and found those two lines:
```

[   22.329298] generic-usb 0003:046D:C214.0001: usb_submit_urb(ctrl) failed
[   22.329309] generic-usb 0003:046D:C214.0001: timeout initializing reports

```

I don't have any hardware problems, but maybe there is a minor issue that should be resolved.

Thanks.

---

### Post by jerrrys on 2011-06-27
really haven't done any reading on this, but at first glance it looks like a minor bug

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=usb_submit_urb%28ctrl%29+failed&sa=Search&cof=FORID:9#896](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=usb_submit_urb%28ctrl%29+failed&sa=Search&cof=FORID:9#896)

---

