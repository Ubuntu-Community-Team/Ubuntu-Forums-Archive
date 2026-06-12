---
title: "How do i remove old versions of ubuntu 9.04 from the grub loader?"
date: 2009-10-24
forum: General Help
---

### Post by eulnuj on 2009-10-24
everytime that i want to boot into windows, i have to scroll all the way down to get it because ubuntu is now in it's 3rd update.

how do i remove the old version from the grub uploading list?

thanks

---

### Post by sgosnell on 2009-10-24
Remove the kernels. You can do that through synaptic, aptitude, or apt-get.  Synaptic is probably the safest, since you can see everything that is installed and only remove the ones you want.  Just remember you can't remove the kernel that's currently in memory, so make sure to boot to the latest version before you start.

---

### Post by malangaman on 2009-10-24
If you want to be able to do so easily, with safety and minimum hassle and no command line gibberish use Ubuntu Tweak:
[http://ubuntu-tweak.com/about](http://ubuntu-tweak.com/about)

Of course you can edit grub in text editor to just remove the entry from grub without removing the old kernel parts from your system as here:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by oakdeveloper on 2009-10-25
Hi,

Run the attached script as root user and it will remove the older updates from the GRUB and keep only the lastest one.

Regards,
Babu

---

