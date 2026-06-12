---
title: "Windows Virtualized under Linux, Virus"
date: 2009-10-01
forum: General Help
---

### Post by linux4life88 on 2009-10-01
I was wondering something about virtualizing Windows under Linux. I understand that even when virtualizing you probably still can get a virus on Windows. So if you can get a virus will this affect your Linux install? I was wanting to install Windows 7 under Virtual Box OSE under Kubuntu.

---

### Post by vishy1618 on 2009-10-01
Yes, there is definitely a chance of getting a virus _in your windows virtual installation._ But this will never affect Kubuntu.

Go ahead with the installation of Windows 7. From my experience, Win 7 is a lot more immune to viruses (but not at all 100%)!

Also, if you use Virtualbox OSE, then you may not be able to access some features like USB, etc.

Good Luck!

---

### Post by linux4life88 on 2009-10-01
I had forgotten that you can not use USB support under Virtual Box OSE. So another question, is there another good virtualization software that adds USB support?

---

### Post by Vunutus on 2009-10-01
> **linux4life88 said:**
> I had forgotten that you can not use USB support under Virtual Box OSE. So another question, is there another good virtualization software that adds USB support?

You might want to look into Sun's version of VirtualBox. It is the same as OSE except with lots of extra features (USB support is one of them). It's technically "nonfree" but that doesn't mean it will cost you money. It's still published under the PUEL license which means individuals are allowed to use it freely. If you are just using this for yourself (in other words, not for a company), and don't need to manipulate the source code, Sun VirtualBox should serve you well.

---

### Post by falconindy on 2009-10-01
Get the PUEL version of VirtualBox.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by linux4life88 on 2009-10-01
> **Vunutus said:**
> You might want to look into Sun's version of VirtualBox. It is the same as OSE except with lots of extra features (USB support is one of them). It's technically "nonfree" but that doesn't mean it will cost you money. It's still published under the PUEL license which means individuals are allowed to use it freely. If you are just using this for yourself (in other words, not for a company), and don't need to manipulate the source code, Sun VirtualBox should serve you well.

This is simply for personal use and fun. Thanks for all the help.

---

### Post by cariboo on 2009-10-01
Once you have installed Win 7 in a vm, don't forget to install the guest additions. It is located in the Device menu when you have the vm running.

---

