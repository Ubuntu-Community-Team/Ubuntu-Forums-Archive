---
title: "Grub 2 not booting..."
date: 2009-10-28
forum: General Help
---

### Post by tempus on 2009-10-28
Hello,
After following the instructions provided to upgrade to Grub 2 my laptop will not boot. It says the following...
Grub Loading stage1.5
GRUB loading, please wait...
Error 15

So how can I repair this...or is it possible?

Should i do a clean install of karmic Koala?

thanks.:popcorn:

---

### Post by ElSlunko on 2009-10-28
Clean install should fix it, however there are many ways to resolve the issue without having to do so.

My favorite solution would be to boot using supergrub installed on a usb pen drive. The unetbootin utility makes setting the drive easy.

Assuming you can boot from USB, simply restart, boot from USB, navigate the supergrub menus, and once you've gotten back to your Ubuntu install re-install grub-pc in synaptic. That worked for me.

---

### Post by tempus on 2009-10-28
> **ElSlunko said:**
> Clean install should fix it, however there are many ways to resolve the issue without having to do so.

My favorite solution would be to boot using supergrub installed on a usb pen drive. The unetbootin utility makes setting the drive easy.

Assuming you can boot from USB, simply restart, boot from USB, navigate the supergrub menus, and once you've gotten back to your Ubuntu install re-install grub-pc in synaptic. That worked for me.
I don't have ubuntu on a usb so it will have to be the live cd somehow.

---

### Post by sahabcse on 2009-10-28
Please follow below url for fixing the grub issue

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

---

### Post by tempus on 2009-10-28
> **sahabcse said:**
> Please follow below url for fixing the grub issue

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

I tried it and is says grub not installed. hmmm

---

### Post by sahabcse on 2009-10-28
Grub 2 troubleshooting section [https://wiki.ubuntu.com/Grub2#Errors](https://wiki.ubuntu.com/Grub2#Errors)

---

### Post by theozzlives on 2009-10-28
Looks like your useing the old GRUB or a combination of the two. Alas GRUB2 is new and I don't know how to fix it. If it were me I'd try to uninstall the old GRUB and re-install the new.

---

