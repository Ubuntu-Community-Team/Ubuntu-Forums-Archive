---
title: "Grub menu gone??"
date: 2011-02-23
forum: General Help
---

### Post by Syed75 on 2011-02-23
So I'm on Widows cause my Linux Grub for Ubuntu is gone.

Now I've searched but nothing. I don't have a Live CD or ISO.

It's installed from WUBI.. Is there a way I can restore Grub from WIndows Vista?? :(

And no Shift doesn't work. I re-start I get a direct boot to windows.

---

### Post by wilee-nilee on 2011-02-23
> **Syed75 said:**
> So I'm on Widows cause my Linux Grub for Ubuntu is gone.

Now I've searched but nothing. I don't have a Live CD or ISO.

It's installed from WUBI.. Is there a way I can restore Grub from WIndows Vista?? :(

And no Shift doesn't work. I re-start I get a direct boot to windows.

So since this is a wubi install, is it the Ubuntu choice from the MS boot loader that is not showing? Or you choose it and it just doesn't go to Ubuntu?

Grub in the wubi is not the same as a standard install, so the way you describe it makes it convoluted.

So describe if you can more clearly. In a normal install of wubi you are using the MS bootloader/boot menu to get to Ubuntu, not grub. You just see a grub menu from that Ubuntu choice from the MS boot menu.

Additionally most likely your problem falls within the guidelines in this thread check it out.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Syed75 on 2011-02-23
> **wilee-nilee said:**
> So since this is a wubi install, is it the Ubuntu choice from the MS boot loader that is not showing? Or you choose it and it just doesn't go to Ubuntu?

Grub in the wubi is not the same as a standard install, so the way you describe it makes it convoluted.

So describe if you can more clearly. In a normal install of wubi you are using the MS bootloader/boot menu to get to Ubuntu, not grub. You just see a grub menu from that Ubuntu choice from the MS boot menu.

Additionally most likely your problem falls within the guidelines in this thread check it out.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

So I'm suppose to mount the root.disk file? 

Oh it gives me a black screen then restarts.

---

### Post by wilee-nilee on 2011-02-23
> **Syed75 said:**
> So I'm suppose to mount the root.disk file? 

Oh it gives me a black screen then restarts.

If your unsure, post the bootscript that is in my signature in that thread, the author is on every day.

It sounds like your on the correct track though. What you should have though is a live Ubuntu cd. This cd is actually quite useful for fixing both Ubuntu and Windows setups and for recovery from either if needed. It appears you will need one to fix this.

---

