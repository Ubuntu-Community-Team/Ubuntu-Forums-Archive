---
title: "How do I reinstall GRUB2? (Or at the least, reconfigure it)"
date: 2009-12-22
forum: General Help
---

### Post by TheOnlyMrK on 2009-12-22
I have a thread here about what started the problem [http://ubuntuforums.org/showthread.php?t=1360073](http://ubuntuforums.org/showthread.php?t=1360073) , long story short I switched out my 80pin IDE cable (that my CD drives were plugged into) for a 40pin one temporarily and now GRUB will take 5+minutes to load even after the 80pin IDE has been put back. So now I want to see if reinstalling GRUB2 will fix the problem. Is their an easy way to do this that anyone knows of?

---

### Post by HappyFeet on 2009-12-22
See [this]("https://help.ubuntu.com/community/Grub2")

---

### Post by oldfred on 2009-12-22
If you are in your working Ubuntu and want to reinstall and choose which drive you can run this, like the initial install screens:
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc

---

### Post by TheOnlyMrK on 2009-12-24
Thanks for showing me how, unfortunately it didn't help at all, but it was worth a try I suppose.

---

