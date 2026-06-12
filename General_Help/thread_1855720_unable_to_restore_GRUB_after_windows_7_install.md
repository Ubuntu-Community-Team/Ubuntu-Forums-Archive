---
title: "unable to restore GRUB after windows 7 install?"
date: 2011-10-06
forum: General Help
---

### Post by NattyNoobCake on 2011-10-06
i created a livedisc usb for ubuntu 11.04 and 10.04 (both 32 and 64 bit) and tried to boot from USB after installing windows 7. However, the liveusb doesn't ever load. Instead, I just get a black screen with a blinking underscore bar "_" in the top left corner. Help Please?

---

### Post by oldfred on 2011-10-06
Did these liveUSBs work before you installed Windows?

How did you create them? Unetbootin, Ubuntu Start-up disk creator, or pendrive? From Windows or Ubuntu?

You may be booting and have video issues or not booting. Have you tried a cold boot from a total shutdown just to see if that made any difference?

---

### Post by NattyNoobCake on 2011-10-06
Yeah, I used one to restore GRUB when i accidentally deleted the Ubuntu partition from my hard drive. I used Unetbootin, linuxlive usb creator, and universal usb from windows. None of them worked.

---

### Post by NattyNoobCake on 2011-10-08
can you please respond to my post. I need help and i've posted twice in this forum already with 0 responses.

---

### Post by Mark Phelps on 2011-10-08
> **NattyNoobCake said:**
> can you please respond to my post. I need help and i've posted twice in this forum already with 0 responses.

You need to show more patience and -- check your math!  From what I can see, oldfred has already responded once in this thread.  That counts as one, not zero.

Disconnect your Win7 drive, so that no hard drives are in the PC, and THEN try booting from the USB stick.  This way, there is no Win7 to interfere with the boot.

If it still does not boot, then one of the following is true:
1) Your BIOS boot sequence is not set up properly.  Modern BIOS setting have one for the sequence of devices (CD, Hard drive, network) and a second for the sequence of hard drives.  Some BIOS see USB as a hard drive -- which means you have to insert the USB stick, boot into the BIOS, and change the hard drive sequence to have the USB boot first.
2) Your PC simply will not boot from USB. Not all will, only the most recent BIOS have that option.  You need to check your BIOS settings to confirm that it WILL boot from USB.
3) Your USB stick is not actually bootable -- meaning, files got copied to it but it doesn't have the boot loader installed.

---

### Post by oldfred on 2011-10-08
I cannot really tell what problem it. Do BIOS let you boot USB and have you selected it correctly?

My Desktop BIOS had many USB boot options, none of which worked. I used my flash drive on my portable and it worked so I knew I had installed it correctly. Then one day I moved grub from sda to sdb and was choosing hard drives (f12 one time choice) and fortunately had flash plugged in as it is seen as another hard drive not a USB device.  Never had problems since.

A few users have had issues and only were able to solve them with a different flash drive. Not sure if download was not verified first time or not installed correctly but change worked. I have used Kingston & Microcenter house brand USB flash drives without issue.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Allows extra space on flash to be used
[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

