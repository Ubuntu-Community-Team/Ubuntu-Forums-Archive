---
title: "Dual booting ubuntu and FDE windows -- GRUB"
date: 2011-05-30
forum: General Help
---

### Post by indefinitearticle on 2011-05-30
I've seen a bunch of threads about dual booting from separate drives, but I couldn't find anything on what I guess is a less common situation.    

My new build has two separate hard disks, and I intend to use one for 10.10 (perhaps with the remains of LFDE, or just the alternate disk encryption), and the other for Windows 7 with full disk encryption with Truecrypt. 

The problem I'm foreseeing is this:    Truecrypt's bootloader is unable to boot to linux, while grub is incapable of booting the encrypted windows.   Is there a way I can edit grub to send me to the truecrypt loader when I select the windows option?

---

### Post by dragonfly41 on 2011-05-30
You could try EasyBCD 2.0 in Windows ...

[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

