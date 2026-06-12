---
title: "Restore Ubuntu Splash Screen"
date: 2010-06-21
forum: General Help
---

### Post by PierreRobiquet on 2010-06-21
Hello,

I have recently installed mintmenu into my Ubuntu 10.04 install which is working perfectly, however it appears to of overwritten the Ubuntu Splash screen with Linux Mint one as well as changed the grub entry and removed "Ubuntu" and left it black leaving just the kernel version number.

Is there anyway I can easily revert the changes?

Thanks,

---

### Post by yetiman64 on 2010-06-21
Following info derived from this link, [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html.]("http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html")

Try in terminal,
```
sudo update-alternatives --config default.plymouth
``` (note I've changed the "&#8211;" before config to "--" to avoid a terminal error).

Then input the **number** for the entry (if your install is standard + mint menu then there should only be 2 entries to choose from),
> /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouthThen in terminal,
```
sudo update-initramfs -u -k all
```On reboot the plymouth splash screen should now be reset to the standard Ubuntu one. Good luck.

Edit1: for grub screen title info, this link may be of help to you, [--LINK--]("http://ubuntuforums.org/showthread.php?p=8082954#post8082954")

---

### Post by snymeister on 2010-06-30
I ran the code provided in this thread.
The splash screen was reverted to normal on the generic kernel, only.

I usually use the rt kernel. The kubuntu splash screen still shows. How do I change the splash screen for the other kernels on my system

---

### Post by yetiman64 on 2010-06-30
> **snymeister said:**
> I ran the code provided in this thread.
The splash screen was reverted to normal on the generic kernel, only.

I usually use the rt kernel. The kubuntu splash screen still shows. How do I change the splash screen for the other kernels on my system

Try
```
sudo update-initramfs -u -k all
```instead of 

```
sudo update-initramfs -u
```this is to update (-u) for kernels (-k) all (self explanatory). This should fix what you need, if you rerun the alternatives config first. Let us know if it works OK - for the benefit of other users ;).

Edit:<removed see post #6>

---

### Post by snymeister on 2010-07-01
> **yetiman64 said:**
> Try
```
sudo update-initramfs -u -k all
```instead of 

```
sudo update-initramfs -u
```this is to update (-u) for kernels (-k) all (self explanatory). This should fix what you need, if you rerun the alternatives config first. Let us know if it works OK - for the benefit of other users ;).

That worked. Thank you.

Edit:Alternatively, you could boot into each kernel and run the original fix above, individually, as you did for the generic kernel.

When I used the minimal -u (without -k all) it only updated the first kernel in the Grub list. I ran that while in the rt kernel, which was in the middle of the list. The rt kernel was not updated until I used the -k all switch.

---

### Post by yetiman64 on 2010-07-01
> **snymeister said:**
> When I used the minimal -u (without -k all) it only updated the first kernel in the Grub list. I ran that while in the rt kernel, which was in the middle of the list. The rt kernel was not updated until I used the -k all switch.

Will remove the edit in my second post to leave only the workable solution, thanks snymeister.

---

