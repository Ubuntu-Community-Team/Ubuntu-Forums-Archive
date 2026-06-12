---
title: "Regain USB Host Control in VirtualBox"
date: 2010-11-29
forum: General Help
---

### Post by tylerannosaurus on 2010-11-29
I recently tried using iTunes inside a virtual box with Windows 7 to update my iPhone 3GS which involved handing control of this device to the guest OS.

My question is whether it's possible to give that control back to my host system (Lucid).

I've tried removing USB support from the virtual box device dropdown but that didn't work.

Any thoughts? If all else fails I could likely restore using someone else's computer but I'd prefer not to.

---

### Post by akand074 on 2010-11-29
I haven't used virtual box in a long time. But if I remember correctly, when I "safely removed drive" from my guest OS my USB devices just mounted in Ubuntu immediately.

---

### Post by tylerannosaurus on 2010-11-29
When I right click on my phone in my computer it doesn't have the option to safely remove. I tried a similar approach using iTunes to eject it but it was still displayed in my computer.

---

### Post by akand074 on 2010-11-29
Well in windows you should have that "removable hardware" icon or whatever its called in the system tray, usually everything is there where you can safely remove. Otherwise if you go to My Computer your devices should be there and you can right click and select "Eject" or something. Ipods might be different I don't have much experience with them but seeing as it's an Apple product I wouldn't be surprised if it went by it's own rules.

---

### Post by tylerannosaurus on 2010-12-01
I was thinking the same thing, however, it doesn't show up in tray and it won't allow me to eject from within Windows. It acts as if it's a separate piece of hardware as opposed to a removable media.

I assume that there must be some setting that's allowing my host OS to ignore this device and if there is a way to give it control back. Any thoughts? I'm going to look through some of the virtual box settings to see what I find.

---

### Post by tylerannosaurus on 2010-12-02
I talked to a buddy of mine today and he suggested removing the modules for Vbox. I tried this and still nothing.

Anyone have thoughts for using terminal to mount my phone manually or know how USB ports are handled in Vbox?

---

### Post by mister_playboy on 2010-12-02
You need to disable the pass-through option for that particular USB device in the VM settings if you want to use it with the host while VB is running.

There is no way to hand control of the device back and forth once the VM is running.

---

### Post by tylerannosaurus on 2010-12-02
> **mister_playboy said:**
> You need to disable the pass-through option for that particular USB device in the VM settings if you want to use it with the host while VB is running.

There is no way to hand control of the device back and forth once the VM is running.

So that's the option in the settings where you click enable USB controller?

I unchecked that on the machine in hopes that it would allow me to use it with the host, but this didn't work...if that is what you are suggesting.

Since then I've deleted the original VB machine in hopes that there was some setting that would be erased to grant access to the USB via host.

By the way, the help is very appreciated! Having nothing on an iPod is kind of lame :/

---

