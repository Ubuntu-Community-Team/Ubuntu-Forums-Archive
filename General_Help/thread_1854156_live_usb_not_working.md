---
title: "live usb not working"
date: 2011-10-03
forum: General Help
---

### Post by NattyNoobCake on 2011-10-03
i was dual booting w7 and ubuntu 11.04 64 bit and i decided to re-install windows on it's partition. I know for sure i didn't clear out ubuntu. But, now i can't access it. I tried making a live usb with the directions from the ubuntu website but when i try to boot from usb, it just shows a blinking bar in the top left corner (the screen is black) and ubuntu never boots. How do i fix this?

---

### Post by dcstar on 2011-10-04
> **NattyNoobCake said:**
> i was dual booting w7 and ubuntu 11.04 64 bit and i decided to re-install windows on it's partition. I know for sure i didn't clear out ubuntu. But, now i can't access it. I tried making a live usb with the directions from the ubuntu website but when i try to boot from usb, it just shows a blinking bar in the top left corner (the screen is black) and ubuntu never boots. How do i fix this?

That happens sometimes as the Live USB gets confused by the existing Linux partition.

You may want to try creating a Live USB with an older version image of Ubuntu (like 10.04), it may allow you to boot up and repair Grub.

---

### Post by seawolf167 on 2011-10-04
You can also try to use something like [UNetbootin ]("http://unetbootin.sourceforge.net/")to create the LiveUSB (with optional persistence)

---

