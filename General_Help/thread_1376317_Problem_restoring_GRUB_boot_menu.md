---
title: "Problem restoring GRUB boot menu"
date: 2010-01-09
forum: General Help
---

### Post by erorr404 on 2010-01-09
Hi. I reinstalled Windows 7 (I have a Windows and an Ubuntu partition) and wanted to recover the GRUB boot menu which disappeared.

So I followed the instructions here (reinstalled GRUB from the latest Live CD): [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But now when I start the computer, I get a GRUB command prompt instead of the menu and can't start either operating system! Here is what the prompt looks like:
```
GNU GRUB version 0.97(636k lower/ 1505216k upper)
[Minimal BASH-like edditing is supported ......... ]

grub>
```

How do I fix this problem and get the boot menu to show?

Thanks,

erorr404

---

### Post by smerral on 2010-01-09
Hi,

Would like to help you out with this but am pretty new myself. I had a similar problem and solved it by updating grub to grub2 after I had used a start up disc to boot:

sudo grub-install /dev/sda
sudo update-grub
sudo update-grub2

Anybody else?

---

### Post by erorr404 on 2010-01-09
Thanks for the reply!

I already fixed the problem. The problem was that I used an Ubuntu 9.10 Live CD, which has a newer version of GRUB incompatible with my 9.0.4 install. I solved it by downloading a 9.0.4 CD and installing the older version of GRUB from there.

I guess I should have read the help page more closely:
> Ubuntu 9.10 (and later) uses Grub2, which differs considerably from Grub Legacy (the version of Grub used in Ubuntu 9.04 and earlier). Attempting this method with Grub2 will leave you in shell mode with no boot menu. If this happens, repeat the procedure with 9.04 or earlier (i.e. one that uses Grub Legacy).

---

