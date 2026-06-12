---
title: "Dual Boot Problem After Update"
date: 2009-12-08
forum: General Help
---

### Post by Ciwan on 2009-12-08
Hi Guys

Disaster !! I have just done an update and now I am unable to load into my Windows 7 !!

It says Errors in Signatures then takes me back to the Window where I choose which OS to login into !!

I really need to use Windows !!

Please I need some urgent help :(

---

### Post by Ciwan on 2009-12-08
The Update was done for Ubuntu by the Way !

After the Ubuntu Update .. I am unable to login into Windows. How do I solve this ? :(

---

### Post by KommerszUnicum on 2009-12-08
Hi!

I had the same problem and found the woraround for it here:

[http://ubuntuforums.org/showthread.php?t=1264151&page=2](http://ubuntuforums.org/showthread.php?t=1264151&page=2)

I think you should check the device.map file.

Good luck!

---

### Post by Ciwan on 2009-12-08
Thank You Kommersz

This did it for me:

```
sudo apt-get install os-prober
sudo os-prober, made sure it showed both linux and windows
sudo mv /boot/grub/device.map /boot/grub/device.map.bak
sudo update-grub (came back clean)
reboot (all is well)
```

Thanks

---

