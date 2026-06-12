---
title: "live cd does not boot"
date: 2012-06-06
forum: General Help
---

### Post by rdh61 on 2012-06-06
Hi,

I am trying to install Ubuntu 12.04 on my Acer TravelMate 4001LMi laptop (at present running Ubuntu 10.04). Trouble is, it will not even begin to boot from the live cd. It just goes straight to the grub screen. I have tried with various other live cd versions, even the old 10.04 one, same result. I tried F12 for boot options and selected the cd drive, same result. Tried switching boot options in BIOS to boot first from the cd drive, same result. The cd drive works. If I put the live CD in once my computer has booted up, I can open it and explore its contents. I have used the same cd to install Ubuntu successfully on another laptop.

Please help! Many thanks.

---

### Post by codemaniac on 2012-06-06
It can be graphics driver use , that is barring you from botting off the live cd .You should try manipulate the default booting options in the grub .
nomodeset or acpi= off .
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by rdh61 on 2012-06-06
Thanks for the reply which may help others.

The solution was to remove my USB drive, which seems to have been interfering even though I set BIOS to boot from the CD first.

---

