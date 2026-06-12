---
title: "Can You Install FROM (Not TO) a USB Thumbdrive?"
date: 2010-05-01
forum: General Help
---

### Post by Bezmotivnik on 2010-05-01
Man, I have spent the past two days trying unsuccessfully to install 10.04 on a machine.

First problem is that it won't load from the installation CD because of I/O errors, presumably.

I did all the workarounds for that, none worked.

OK, so, I tried minimal install and installing from online.  After somewhere between twenty and thirty tries, I gave up on that as every server I tried either failed to download a file or some file was corrupt on install.

I have a good installation .ISO file with proper checksum.  Is there a way I can write this to a 1G thumbdrive, boot to it and install to the machine from that?

This has been incredibly frustrating, the hardest install I've done...or *tried* to!

Thanks for any help!

---

### Post by dragonboss on 2010-05-01
Yes, you can easily install from a thumb drive. You have to first load the iso on the drive using usb startup disk creator(installed by default under System>Administration) or unetbootin(terminal > sudo apt-get install unetbootin/ synaptic and search) (I give the option because for me usb startup disk creator hangs at 99% forever sometimes but still works and unetbootin installs its own bootloader on the drive) which i did just this morning to install my 10.04 desktop.

---

### Post by robvas on 2010-05-01
This page shows you how to do it from Linux or Windows

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Bezmotivnik on 2010-05-02
> **robvas said:**
> This page shows you how to do it from Linux or Windows

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Cool.  Thanks, I'll give it a try later.

---

### Post by dino99 on 2010-05-02
there is an other nice idea, not used myself right now, with grub directly booting iso

need to search about grub+iso or vmlinux+iso

---

