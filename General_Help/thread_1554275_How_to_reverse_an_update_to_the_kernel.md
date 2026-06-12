---
title: "How to reverse an update to the kernel?"
date: 2010-08-16
forum: General Help
---

### Post by jre6 on 2010-08-16
I am using Ubuntu 9.10 and had updated the kernel from 2.6.31-14generic to 2.6.31-22generic, hoping to resolve a problem with a Huawei modem. However, it proved to be useless and even broke the workarounds that I used. Is there any way to remove 2.6.31-22generic?

---

### Post by colin.p on 2010-08-16
I kind of did the same thing in lucid. I updated to 2.6.34 from 2.6.32, but it didn't do what I was hoping, so all I did was reboot and choose the earlier kernel. Then while back in, I looked in synaptic for the kernel I wanted to remove. Found it and tagged it for removal. I then double checked in ubuntu tweak, under "clean packages", and removed any left overs.
Next boot, it was gone.

---

### Post by sgosnell on 2010-08-16
Yes, just boot from the earlier kernel using the menu, and then remove the later kernel through Synaptic.  Just make sure you're removing the correct kernel, or you'll have problems.  Removing the kernel that is currently booted is not recommended.

---

### Post by jre6 on 2010-08-18
> **colin.p said:**
> I kind of did the same thing in lucid. I updated to 2.6.34 from 2.6.32, but it didn't do what I was hoping, so all I did was reboot and choose the earlier kernel. Then while back in, I looked in synaptic for the kernel I wanted to remove. Found it and tagged it for removal. I then double checked in ubuntu tweak, under "clean packages", and removed any left overs.
Next boot, it was gone.

Yes, this worked.

---

