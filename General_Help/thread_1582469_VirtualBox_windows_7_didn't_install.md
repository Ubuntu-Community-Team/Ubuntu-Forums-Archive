---
title: "VirtualBox: windows 7 didn't install"
date: 2010-09-26
forum: General Help
---

### Post by Chris1274 on 2010-09-26
I made my first attempt last night at installing windows 7 in a virtual machine using VirtualBox OSE, just to see if I could. The installation failed because (it said) the version of win7 I was trying to install is 64-bit while the VM only worked with 32-bit systems. But the laptop itself is a 64-bit laptop. Is there another version of VirtualBox for installing 64-bit systems?

---

### Post by Benbow on 2010-09-26
I am a novice with virtualbox but I have found out that there are several different versions. Perhaps if you mention which version you have installed it may draw some comment.
Sorry, missed the "OSE". There is an Oracle version which gives better support but you will have to download it from their web site. I am currently trying it out as it has usb support.

---

### Post by Merk42 on 2010-09-26
There is a separate entry in Virtualbox for 64 bit versions of OSs, so make sure you have Windows 7 (64bit) as the type of OS.

Also it may be that while your processor supports 64bit for the host OS, it may not support 64bit in the guest OS. I'm pretty sure this was only true of the first generation or so of 64bit processors though.

Go to the settings of your Windows 7 VM and then System  on the left and the Acceleration tab, hopefully you'll be able to check both of those boxes

---

### Post by Chris1274 on 2010-09-26
> **Merk42 said:**
> There is a separate entry in Virtualbox for 64 bit versions of OSs, so make sure you have Windows 7 (64bit) as the type of OS.

Also it may be that while your processor supports 64bit for the host OS, it may not support 64bit in the guest OS. I'm pretty sure this was only true of the first generation or so of 64bit processors though.

Go to the settings of your Windows 7 VM and then System  on the left and the Acceleration tab, hopefully you'll be able to check both of those boxes

Alas, there aren't separate entries for 32- and 64-bit versions, it just says "Windows 7".

I have an old XP reinstall CD, I'll give that a try. I don't really need it for anything crucial anyway.

---

### Post by Merk42 on 2010-09-26
> **Chris1274 said:**
> Alas, there aren't separate entries for 32- and 64-bit versions, it just says "Windows 7".

I have an old XP reinstall CD, I'll give that a try. I don't really need it for anything crucial anyway.

You may need the PUEL version for 64bit support of a guest OS. I don't know off hand as I normally just use the PUEL version anyway.

I can't check the differences between OSE and PUEL as Virtualbox's website appears to be down

---

### Post by yetiman64 on 2010-09-26
For 64 bit Ubuntu Lucid Lynx as host and Win 7 as guest,

This is a direct download link to the Oracle site download as the virtualbox.org sites seem to be down._ [virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_amd64.deb]("http://download.virtualbox.org/virtualbox/3.2.8/virtualbox-3.2_3.2.8-64453%7EUbuntu%7Elucid_amd64.deb")_This is the PUEL version.
> But the laptop itself is a 64-bit laptopJust make sure you are using the 64 bit install of Lucid with (it is possible to install 32 bit Lucid on 64 bit hardware - this could be a cause of the problem also),
```
uname -a
``` and look for an entry with "x86_64 GNU/Linux"

eg. (from my 64 bit install)
> Linux <hostname> 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 **x86_64 GNU/Linux**

---

### Post by Dr. C on 2010-09-26
My first question is are you running 64 bit Ubuntu and if so which version? If one is running 10.04 64bit Ubuntu and installs the OSE version of VBox from the repositories then one does get a choice for Windows 7 64bit when creating the VM. I suspect the problem may be 32bit Ubuntu on the 64bit machine.

---

