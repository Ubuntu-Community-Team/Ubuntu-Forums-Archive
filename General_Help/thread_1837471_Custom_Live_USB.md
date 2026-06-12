---
title: "Custom Live USB"
date: 2011-09-01
forum: General Help
---

### Post by carmenat250 on 2011-09-01
I've made my own custom live CD and love using it.

But I just thought of something.  Rather then burning to a CD, is it possible to make a custom live USB key?

I still have the original .iso file and it would sure save on CDs.  Just wondering if there are any tutorials on this?

Thank you

---

### Post by zealibib slaughter on 2011-09-01
just use unetbootin to create a live usb from your ISO.

---

### Post by varunendra on 2011-09-02
> **carmenat250 said:**
> I've made my own custom live CD and love using it.

But I just thought of something.  Rather then burning to a CD, is it possible to make a custom live USB key?

I still have the original .iso file and it would sure save on CDs.  Just wondering if there are any tutorials on this?

Thank you
Apart from using inbuilt "USB Startup Disk Creator", you can also use unetbootin as zealibib suggested. Changes to a Live USB, by default, are persistent (that is, applications you install, customizations, files created, etc.). But when installing from that USB, it won't carry the changes/customizations to the installation. If you want to 'carry' the changes over to installations, consider using 'Remastersys' (in natty, it needs to be installed from the downloaded debian package), or follow these guides:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

But if if you already have a customized iso, just create the Live USB from it. The USB should work the same way as a CD created from that iso.

---

