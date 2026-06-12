---
title: "Kernel update why?"
date: 2006-05-22
forum: General Help
---

### Post by flipkick on 2006-05-22
I'm seeking information on the following questions. 

- What use does it make to update to the next version ( 2.6.12.10 -386 ) ?
- Am I loosing my OpenGL Driver installation ? (Ati Radeon 9800 Pro)
- Is the Kernel not in relation to other updates ? E.G. Can I only get gnome 2.14 with the newest Kernel ?

Thank you very much.

:-#

---

### Post by Ensnared on 2006-05-22
The point of updating the kernel is mostly bugfixes and perhaps performance improvements in the newer version. If the old version works for you, there's usually no need to update it unless there's some kind of security-fix in the newer version.

The driver for your ATI-card is installed in the modules-directory for the kernel, so you'll need to reinstall the module in order to make use of the driver if you change to a different kernel (which is what you do when you upgrade the kernel). Depending on how you installed the driver, you'll probably just need to run a couple of commands to reinstall the module. If you've followed [this guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide) to install the downloaded driver from ATI's website, all you need to do is run the following commands after booting into the new kernel:```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant a-i fglrx
```

As for the last question, I'm not entirey sure what you mean. You can have any version of Gnome (or any other desktop environment or window manager) with any version of the kernel - the two items are completely separate.

---

### Post by flipkick on 2006-05-22
I think the commands for "reregistering" the module worked fine for me. Thanks.
> 
§fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5582 (8.21.7)


I was thinking about the update system in ubuntu, that maybe some newer software versions would only be shipped with the newest kernel installation. But this is not the case I assume now.

I appreciate your fluid and readable answer.

:)

---

