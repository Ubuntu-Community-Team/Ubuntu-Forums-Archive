---
title: "How to determine free space on USB stik with 12.04."
date: 2012-05-13
forum: General Help
---

### Post by Advait on 2012-05-13
Hi All,

See attached images.

I used the "Universal USB Installer" to install 12.04 onto a 4gb USB stik with about 2gb of persistent space. I've installed some software and updated 12.04. How can I tell how much available space there is for the 12.04 OS on the stik?

When I right click on the USB drive (called "casper-rw") in Ubuntu File Explorer, it doesn't tell me anything. When I try to open it it says "Could not find "/cow". (insert "missing cow" joke here) :P

Thanks!

Tom

---

### Post by Bucky Ball on 2012-05-13
Plug the stick in and open Gparted (partition editor). There is a drop down list at the top right. Find your stick (sd*, possibly sdb or sdc) and you will get all the details you're after.

---

### Post by newbuntuxx on 2012-05-14
open terminal and run:

```
cd /media
df -kh *

```

One of the output lines will be your usb stick.

---

### Post by Bucky Ball on 2012-05-14
Also, are you booting from the USB stick?

---

### Post by Advait on 2012-05-14
> **Bucky Ball said:**
> Also, are you booting from the USB stick?

Yes, I boot from the USB stik. I do not want to install 12.04. I only run it from the USB stik. Thanks!

Kind Regards,

---

### Post by Bucky Ball on 2012-05-14
So have you checked in Gparted?

---

### Post by Advait on 2012-05-14
> **Bucky Ball said:**
> So have you checked in Gparted?

Just did. Worked perfect. Thanks!

---

