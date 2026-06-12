---
title: "Bootloaders Chainloading"
date: 2010-08-06
forum: General Help
---

### Post by Du7chManiac on 2010-08-06
So I installed Wubi 10.04, everything went well during the installation. After that it automatically rebooted my computer and the windows bootloader popped up (like it should) so I selected Ubuntu. Then somehow GRUB came up asking which OS I wanted to boot...Only my Windows was in the list, so I clicked Windows...then the Windows bootloader pops up again with Windows and Ubuntu in the list. It keep chainloading the 2 bootloaders all the time...

I never had any other bootloaders on my computer...

How can I fix this?

---

### Post by bcbc on 2010-08-06
> **Du7chManiac said:**
> So I installed Wubi 10.04, everything went well during the installation. After that it automatically rebooted my computer and the windows bootloader popped up (like it should) so I selected Ubuntu. Then somehow GRUB came up asking which OS I wanted to boot...Only my Windows was in the list, so I clicked Windows...then the Windows bootloader pops up again with Windows and Ubuntu in the list. It keep chainloading the 2 bootloaders all the time...

I never had any other bootloaders on my computer...

How can I fix this?

I saw another thread like this. Wubi installs but only offers windows in the grub menu (it's normal to offer windows as a boot option, but it's also supposed to offer ubuntu). I have no idea why this is happening. 
Perhaps you could post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). and then I'll create a bug for you (or you can do it yourself).

---

### Post by Du7chManiac on 2010-08-06
It says I need to boot into a linux os to run that script, but I can't get into Ubuntu...

Can't I just remove the grub bootloader somehow?

---

### Post by bcbc on 2010-08-06
> **Du7chManiac said:**
> It says I need to boot into a linux os to run that script, but I can't get into Ubuntu...

Can't I just remove the grub bootloader somehow?

Go to Add/Remove programs and click on Ubuntu to uninstall and delete all wubi/ubuntu files. It should boot straight into windows afterwards without showing the boot manager.

---

### Post by Du7chManiac on 2010-08-06
And you think if I then try install everything again it will be fixed?

---

### Post by bcbc on 2010-08-06
> **Du7chManiac said:**
> And you think if I then try install everything again it will be fixed?

Reinstalling didn't help the other person who had this issue. Can you post the wubi log file (you can get to it by entering %temp% in the address bar of Windows Explorer and then it's called wubi-xxx.log). Post it between [CODE[SIZE="1"] [/SIZE]][/CODE] tags. Note it identifies windows user name and location so mask these if you like.

Also, are you running wubi.exe downloaded from [http://wubi-installer.org/](http://wubi-installer.org/) or some other place? Did you download the .iso yourself? Which flavour did you install - regular Ubuntu/Netbook/Kubuntu etc?

This info might help to figure out what is wrong.

---

