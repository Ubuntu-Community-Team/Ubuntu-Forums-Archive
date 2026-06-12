---
title: "Cant instal wireless drivers on netbook"
date: 2011-01-03
forum: General Help
---

### Post by pc999 on 2011-01-03
Hi,

I am trying to install both the proprietary drivers for "broadcom B43 wireless driver" and "Broadcom STA wireless" on my netbook but I get  this on both "SystemError: installArchives() failed".

I am using Ubuntu 10.10 desktop edition.


Anyone know how can I solve this? I really need wireless...

Thanks in advance.

---

### Post by nothingspecial on 2011-01-03
Have you tried this from a wired connection using (in the menu) System > Administration > Additional Drivers ?

---

### Post by pc999 on 2011-01-03
Yes, I did it that way, it is the same way I am posting this.

Thats fast :)

---

### Post by nothingspecial on 2011-01-03
Try this```


sudo apt-get install firmware-b43-lpphy-installer
```

Then reboot.

---

### Post by pc999 on 2011-01-03
> **nothingspecial said:**
> Try this```


sudo apt-get install firmware-b43-lpphy-installer
```Then reboot.


Funny at first I just read the reboot part, 


I did it, then tried again I could instal  one of them, when I instal the other it deactivate the one I instaled first. ( I did tried to run that comand, but it seems I am not that good using the console


**But it looks like I do have wireless internet ? So I guess it is solved?** Even it just one of the drivers instaled.


Should I report it like a bug or something?

Thanks again.

---

