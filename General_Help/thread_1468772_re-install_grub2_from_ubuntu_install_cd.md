---
title: "re-install grub2 from ubuntu install cd"
date: 2010-05-01
forum: General Help
---

### Post by linuxhippy on 2010-05-01
I have a bit of a problem that could be solved with linux rescue from the ubuntu 9.10 install cd.  I don't see that option, though.  I figure if I had linux rescue boot me to a command line then I could just issue update-grub /dev/sda

My problem is that I cannot get Ubuntu to boot of my hard drive anymore because I installed CentOS beside Ubuntu 9.10 and Fedora Core 12.  CentOS only seemed to boot from Grub1 and not the Grub2 that Ubuntu uses now.  So, I let CentOS install grub1 to the MBR so I could boot that.  I found it difficult to get good help at their forums, though, and decided to go back to Ubuntu.  

I was able to boot into Fedora Core 12 with their install cd and do a chmod to reinstall grub.  It also is using grub1, though, and I couldn't get the menu.1st file to boot Ubuntu.

So, how can I have Ubuntu install grub2 to the MBR from the Ubuntu install cd?

---

