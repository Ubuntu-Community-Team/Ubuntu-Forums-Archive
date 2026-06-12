---
title: "How to install 10.10 through a 'USB' stick?"
date: 2011-02-17
forum: General Help
---

### Post by Saurabhdua on 2011-02-17
Hi Guys!

Though everything is mentioned in the 'Download' section in regard to installation through CD, & generally in every PC, first Boot device is always the CD Rom, what changes ought to be made to install Ubuntu 10.10 using a USB stick?

Will the BIOS section allow me to choose the first BOOT DEVICE as my thumb drive?, in order to install Ubuntu using it?

---

### Post by mikewhatever on 2011-02-17
It depends on the BIOS, no way of knowing in advance.

---

### Post by howefield on 2011-02-17
> **Saurabhdua said:**
> Will the BIOS section allow me to choose the first BOOT DEVICE as my thumb drive?, in order to install Ubuntu using it?

Most fairly modern computers should allow booting from USB. 

If you have created your startup up USB disk, give it a go ?

---

### Post by zhogan85 on 2011-02-17
To boot from a usb, if your BIOS menu won't let you choose to boot from a usb, most modern computers still have a method. On my Asus for example I have to tap esc while booting up. Try googling to find a method for your type of computer.

---

### Post by garyjmellor on 2011-02-17
Have you created your USB startup disk following the instructions on the download page ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)) - look in section two on this page.

Next, check your BIOS to see if you can boot off USB. When you power on the computer it should tell you what you need to press to enter setup (typically this is F8, although not always). Look for a section called 'Boot' and from there see if USB is an option.

If it is, move this higher up the boot order (i.e. before HDD and CD/DVD drive). Save the BIOS settings, plugin your USB stick and give it a go!

---

### Post by Saurabhdua on 2011-02-18
Thanks to you all!

I have confirmed that my BIOS do not offer any option to choose First Boot device as that to USB stick!

It do lists weird entries like ZIP100,LSC120 & even LAN..!? Will prefer burning a CD then.

---

