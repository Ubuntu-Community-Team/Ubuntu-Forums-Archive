---
title: "setting default os"
date: 2010-12-17
forum: General Help
---

### Post by mshanthosh on 2010-12-17
After I had installed 2 windows os(win 7 32 bit & 64 bit), I installed the Ubuntu 10.04. By using the command "sudo gedit /etc/default/grub" I changed the default os number to windows loader. But It automatically starts with ubuntu os only. How can I set windows loader as default option.

---

### Post by WorMzy on 2010-12-17
Did you run
```
sudo update-grub
```
after making the changes to grub's config file?

Also, don't use "sudo" for graphical applications like gedit, use "gksu" or "gksudo". Using sudo for graphical applications can cause permissions problems in your home folder.

---

### Post by mshanthosh on 2010-12-18
> **WorMzy said:**
> Did you run
```
sudo update-grub
```
after making the changes to grub's config file?

Also, don't use "sudo" for graphical applications like gedit, use "gksu" or "gksudo". Using sudo for graphical applications can cause permissions problems in your home folder.

Thank you I changed the default os successfully...

---

