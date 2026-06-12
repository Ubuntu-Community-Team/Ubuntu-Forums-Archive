---
title: "changing default kernel"
date: 2011-03-31
forum: General Help
---

### Post by soap1 on 2011-03-31
Hello, I am rather new to ubuntu and need a bit of help.  I have a wirless usb adapter that my cousin installed for me.  After accidentally upgrading my kerenel I had no access to Internet.  Now everytime I boot up I need to go into the grub to boot from the kernel that does allow the wireless usb adapter to work.  How can I change the default kernel so that it boots to the one that I want?

---

### Post by TeoBigusGeekus on 2011-03-31
```
gksu gedit /etc/default/grub
```
Find the GRUB_DEFAULT section and change it according to your needs (entries begin with 0: if you want the second grub entry put 1, if you want the third put 2, etc.)
Save and exit.
Run
```
sudo update-grub
```
and you're done.

---

