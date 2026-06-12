---
title: "Plugging in printer makes GRUB go bananas!"
date: 2010-03-11
forum: General Help
---

### Post by artheus on 2010-03-11
Hey!

I recently plugged in my HP Photosmart Plus B209a-m, to my Ubuntu 9.10 server. And restarted the server.

The boot stopped at GRUB saying 

```
GRUB Loading.
error: cannot get C/H/S values
grub rescue> 
```

And I tried to unplug my printer and then restart. And the boot worked normally.

I went in to BIOS Setup with my printer plugged in, and it saw the printer as a bootable device. And had set it as the first priority of the bootable devices. I removed it from the list. But GRUB still would not boot with the printer plugged in.

Any ideas would be dearly appreciated!

//Artheus

---

