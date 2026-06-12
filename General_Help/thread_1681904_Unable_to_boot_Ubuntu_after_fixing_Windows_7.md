---
title: "Unable to boot Ubuntu after fixing Windows 7"
date: 2011-02-05
forum: General Help
---

### Post by Quadunit404 on 2011-02-05
So I was bit by the "NTLDR is missing" message a few minutes ago, which was a... rather easy fix as I had a live USB of Ubuntu handy. Now I am able to boot to Windows just fine now - but Ubuntu? Nothing happens. I select the Ubuntu command in BURG and then... nothing.

I'll try again later on today. For now, I... guess I'll play games or something as I usually do on Windows :|

---

### Post by wilee-nilee on 2011-02-05
If you left grub in place when you installed burg you can just reload grub2 with the link. When you get in you just install burg back to /dev/sdX=mbr.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You could also download supergrub2, get into Ubuntu and reload the mbr.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Quadunit404 on 2011-02-05
Last time I looked in my /boot (which was to confirm that the kernels still exist :lol:) the "grub" folder still existed.

I think I'll reinstall BURG by loading it and the PPA onto a live USB, then installing it again to /dev/sda on that live USB and HOPEFULLY that should work... right?

---

### Post by wilee-nilee on 2011-02-05
> **Quadunit404 said:**
> Last time I looked in my /boot (which was to confirm that the kernels still exist :lol:) the "grub" folder still existed.

I think I'll reinstall BURG by loading it and the PPA onto a live USB, then installing it again to /dev/sda on that live USB and HOPEFULLY that should work... right?

Probably, I think you can use that grub2 link 3rd method to chroot in as well that, the link defaults to method 1.

---

### Post by Quadunit404 on 2011-02-05
BTW, BURG still shows up during boot, it's just that only the Windows 7 option works for now... :|

---

### Post by Quadunit404 on 2011-02-05
So I reinstalled BURG... and IT'S ALIVE!!! I can boot both OSes now!!!

Marked as solved.

---

