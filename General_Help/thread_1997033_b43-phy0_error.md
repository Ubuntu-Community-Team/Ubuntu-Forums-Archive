---
title: "b43-phy0 error"
date: 2012-06-04
forum: General Help
---

### Post by EmilioG on 2012-06-04
I've had Arch Linux on my Dell Latitude D610 for a while, but it's been kind of sluggish. I wanted to install Lubuntu and my new OS, so I created a bootable USB with Unetbootin. However, when i'm installing/booting it (I'm not sure which is happening when the error occurs), I get the error:
```
[49.183056] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[49.183181] b43-phy0 ERROR: Firmware file "b43-open/ucode.fw" no found
[49.183305] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

I went to the website and I'm still not sure what to do. I also can't click 'ctrl-alt-f1' to do download the firmware. Booting with the parameter "nomodeset" doesn't work either. What can I do?

---

### Post by wildmanne39 on 2012-06-04
Hi, if you have ubuntu installed on the hard drive you can do this:

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Thanks

---

### Post by EmilioG on 2012-06-04
Thanks for responding.

I currently do not have Ubuntu on my hard drive, it is still Arch Linux. Would I be able to do it through Arch? Would I be able to do this off a live CD/USB, without installing Ubuntu? Or do I have to completely install it?

Thank you in advance.

---

### Post by wildmanne39 on 2012-06-04
Hi, if you have the usb drive setup as persistent you should be able to or if you actually installed Arch to the usb drive.
Thanks

---

### Post by EmilioG on 2012-06-04
OKay, I've tried doing what you've told me, but nothing has seemed to work. I could not install Ubuntu, as it got stuck on "starting configure network device security". I then tried to extract the files in Arch, but I get the error "cannot create directory". What do I do now?

Thanks.

---

### Post by wildmanne39 on 2012-06-04
Hi, try nomodeset to install ubuntu.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You could also see if you can turn of wirless lan in the bios before installing.
Thanks

---

### Post by EmilioG on 2012-06-04
Okay, I've disabled all wireless devices in the bios, but now now Ubuntu is reporting the same error that I had with Lubuntu, the missing firmware. 

Also, I cannot seem to use "nomodeset" because I never see the splash screen with the keyboard on it. Is it because I'm using Unetbootin? I'm not sure. Any more suggestions? Sorry for asking so much.

Edit: Thinking it may be an error with Unetbootin, I burned Ubuntu to a disk and tried to boot, but it did not work at all. I believe the CD drive is broken.

---

### Post by wildmanne39 on 2012-06-04
Hi, did you set boot from cdrom first in your bios so it would try to boot from the cdrom? if so you should not have seen an Arch grub.
Thanks

---

### Post by EmilioG on 2012-06-04
Sorry, I didn't see your post when I re-edited. It turns out when I first burned the CD there was an error I didn't see, so the disk was actaully blank. I fixed the disk, but the CD drive makes a clicking sound now when I try to boot from it, so I'm assuming it may be broken.

---

### Post by wildmanne39 on 2012-06-04
Hi, that doe's not sound good, can you try the disc on another computer?

Sounds like the drive is having issues.
Thanks

---

### Post by EmilioG on 2012-06-04
Just tried the disc on another computer and it works perfectly. Booting Lubuntu also works perfectly from the USB. The problem is entirely within my old Dell (more specifically, the missing b43 firmware).

---

### Post by wildmanne39 on 2012-06-04
I have seen a solution to the issue on the forum recently but I can not find it.

---

### Post by EmilioG on 2012-06-04
Oh darn, okay. Thank you for trying, you were very helpful.

---

### Post by wildmanne39 on 2012-06-04
Hi, I found the thread.
[http://ubuntuforums.org/showthread.php?t=1966655&highlight=b43-phy0+ERROR](http://ubuntuforums.org/showthread.php?t=1966655&highlight=b43-phy0+ERROR)
Thanks

---

### Post by EmilioG on 2012-06-05
Awesome, thanks! I installed 11.10, and am now upgrading to 12.04 (it's working great!). Thank you very much for your patience and helpfulness, I really appreciate it.

---

### Post by wildmanne39 on 2012-06-05
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

