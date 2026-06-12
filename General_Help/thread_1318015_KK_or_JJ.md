---
title: "KK or JJ"
date: 2009-11-07
forum: General Help
---

### Post by tempus on 2009-11-07
I currently have 9.10 installed on my laptop. Can I install 9.04 beside it on the hard drive and have the option to boot into either version when booting up? I tried this with fedora and it did not play nicely. I lost the option to boot into version 9.10. How would I do this?  :popcorn::popcorn:

---

### Post by Rob_H on 2009-11-07
Yes, certainly possible. But it may involve manually editing /boot/grub/menu.lst. The specifics depend on how you've partitioned things, but there is good information available in the [GRUB wiki]("http://grub.enbug.org/").

---

### Post by karthik120 on 2009-11-07
Hi,

     Could you please try "http://unetbootin.sourceforge.net/" and see if it works for you. 



Regards,
Karthik
CollabNet

---

### Post by Shazaam on 2009-11-07
1. The Jaunty install should overwrite 9.10's grub and should pick up Karmic if you install grub to the mbr.
2. If you install Jaunty's grub to it's own partition then you will have to add Jaunty to Karmics grub.
Seems confusing but it's not.  :)

One way to learn things without wrecking a working installation is to try experiments using virtualization. Install whatever works for you (VirtualBox, VMWare, etc) and trash  virtual distros/dual-multi boots to your hearts content. This way a mistake won't do any harm to your system. Later on when you get comfortable with what you are doing go ahead and try real installs. This also helps when you want to try another linux distro.
The thing to remember is most virtualization programs do NOT utilize your real physical hardware and won't tell you how the distro will actually run as an normal install. 

aside...
karthic120- eh? Wrong thread? Spam?

---

