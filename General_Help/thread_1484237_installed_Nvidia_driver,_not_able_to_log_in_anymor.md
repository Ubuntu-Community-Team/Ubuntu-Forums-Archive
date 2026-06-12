---
title: "installed Nvidia driver, not able to log in anymore"
date: 2010-05-15
forum: General Help
---

### Post by emaloli on 2010-05-15
Hi!

I installed ubuntu 10.04 on my desktop computer, (i had 9.10), and tried to install the Nvidia driver that was working fine with the 9.10.

I dowloaded the driver 96.16 etc etc
I manually installed it, and it seemed everything was fine

and now I can't even log in! when it asks me the password it just stops... I can log in using Ctrl+Alt+F1, but that's all..

How can I uninstall the driver?

And most of all, why was it working fine on ubuntu 9.10 and not on the this new Lucid Lynx? Anyone with the same problem?

Thanks a lot!

---

### Post by ankit singh on 2010-05-15
lucid is a nvidia disaster,i myself has lot of trouble.

Run the code: 

[COLOR="Red"]sudo nvidia-xconfig[/COLOR]

and if u want to uninstall its every trace run the installer and append unistall

[COLOR="red"]sudo sh NVIDIA-Linux-x86-195.36.24-pkg1.run --uninstall[/COLOR]

---

### Post by ankit singh on 2010-05-15
> **ankit singh said:**
> 
[COLOR="red"]sudo sh NVIDIA-Linux-x86-195.36.24-pkg1.run --uninstall[/COLOR]

here you should correct ur version(in short name of ur installation )

---

### Post by HiImTye on 2010-05-15
the nvidia drivers in the 'hardware drivers' module work fine for me

---

### Post by emaloli on 2010-05-15
Thanks!

I succeded in uninstalling the driver..
The problem with "hardware drivers" is that it installed the 96.13 version, which is old and caused me some problems.. 
I'll keep on my desperate search for a nvidia trouble-free driver!

---

