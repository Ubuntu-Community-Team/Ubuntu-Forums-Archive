---
title: "How to change default startup system in dualboot"
date: 2012-02-04
forum: General Help
---

### Post by Newbeatontheblock on 2012-02-04
Hi all,

I m running dualboot windows ubuntu since a few weeks. Ubuntu is set to boot as default.
I m not able to change this in windows as i install ubuntu after win.  Can anybody tell how to change this in ubuntu?

Thanks very much

---

### Post by sudodus on 2012-02-04
Edit the file /etc/default/grub
```
sudo nano /etc/default/grub
``` and change
**GRUB_DEFAULT**  - Sets the default menu entry. Entries may be numeric or "saved"

Look at the following link for more details

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Finally update grub and reboot
```
sudo update-grub
``````
sudo reboot
```

---

### Post by Newbeatontheblock on 2013-02-16
Hi,
I have done this and it worked thank you very much for your reply on this.
And apologies for my late reaction.

Thanks very much

---

