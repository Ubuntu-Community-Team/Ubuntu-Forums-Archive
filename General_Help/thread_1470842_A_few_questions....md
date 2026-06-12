---
title: "A few questions..."
date: 2010-05-03
forum: General Help
---

### Post by BlindSoul on 2010-05-03
Hey.

 I'm new here, And i'm interested to run Linux ubuntu on my PC. But first i wanna check it on a Virtual PC. Like VMware , Virtual Box or any of these softwares.
 Now there's one problem. My graphic card is NVIDIA GeForce 240GT and there's no driver available for this graphic card on the NVIDIA Site.
 Now my question is. There's even an option to use in graphics with a virtual machine?
 Also, What software would you suggest me to use that might run Linux ubuntu the best.
 And what should i do about the driver? Do you know maybe what can i use instead?


 Thank you very much!
 Ryan.

---

### Post by dino99 on 2010-05-03
> **BlindSoul said:**
> Hey.

 I'm new here, And i'm interested to run Linux ubuntu on my PC. But first i wanna check it on a Virtual PC. Like VMware , Virtual Box or any of these softwares.
 Now there's one problem. My graphic card is NVIDIA GeForce 240GT and there's no driver available for this graphic card on the NVIDIA Site.
 Now my question is. There's even an option to use in graphics with a virtual machine?
 Also, What software would you suggest me to use that might run Linux ubuntu the best.
 And what should i do about the driver? Do you know maybe what can i use instead?


 Thank you very much!
 Ryan.

[http://www.nvidia.com/object/linux-display-ia32-195.36.24.html](http://www.nvidia.com/object/linux-display-ia32-195.36.24.html)

virtualbox is a nice solution working with is built-in video driver, so no trouble

---

### Post by BlindSoul on 2010-05-03
[B] Thanks for the fast reply, I will try it now and will update you.
 Btw, Would i have to install the driver by myself? Or it'll be on the installation like on Windows 7?[/B]

---

### Post by Ryan Dwyer on 2010-05-03
You can boot from the CD and run it in a live environment without touching your existing operating system. It's good for testing hardware compatibility.

---

### Post by Ryan Dwyer on 2010-05-03
If the driver isn't installed automatically, you should be able to go to System > Administration > Hardware Drivers and follow the prompts to install it.

---

### Post by dino99 on 2010-05-03
[http://en.kioskea.net/faq/5868-installing-nvidia-drivers-on-ubuntu](http://en.kioskea.net/faq/5868-installing-nvidia-drivers-on-ubuntu)

---

### Post by BlindSoul on 2010-05-03
Okay, I downloaded Ubuntu 10.4 and VirtualBox as you offered me. Installed Virtual Box and i'm now on the Linux Installation. But when i start it it gives me a warning.
 You can see the warning on this image:
 [http://img41.imageshack.us/img41/8472/exampley.png](http://img41.imageshack.us/img41/8472/exampley.png)

 And when i click on OK, It just goes black and shows me this sign: _

 I think it's stuck though. o.o

 Well, What am i suppose to do? I don't get what this warning means. :(

---

### Post by John Bean on 2010-05-03
Did you install the VirtualBox Guest Additions?

---

### Post by dino99 on 2010-05-03
> **BlindSoul said:**
> Okay, I downloaded Ubuntu 10.4 and VirtualBox as you offered me. Installed Virtual Box and i'm now on the Linux Installation. But when i start it it gives me a warning.
 You can see the warning on this image:
 [http://img41.imageshack.us/img41/8472/exampley.png](http://img41.imageshack.us/img41/8472/exampley.png)

 And when i click on OK, It just goes black and shows me this sign: _

 I think it's stuck though. o.o

 Well, What am i suppose to do? I don't get what this warning means. :(

hey, maybe you need to answer: your screenshot explain all about, remember to tweak each prog before using it, its the b-a ba

---

### Post by Vaphell on 2010-05-03
i tried to install 10.04 on jaunty host and got the same 'stuck at black screen with _ in the top left corner' problem. After pressing anything at the keyboard=human screen you get to cd menu and most probably you need to set 'acpi=off' from F6. You should be able to continue from here but be warned. Complete install will probably require modifying its grub settings (adding acpi=off to config), otherwise you'll end with the same _ screen.
Sun needs to update virtualbox - until then workaround is pretty much necessary - at least i think so.

---

### Post by BlindSoul on 2010-05-03
> **dino99 said:**
> hey, maybe you need to answer: your screenshot explain all about, remember to tweak each prog before using it, its the b-a ba

 I've been looking for the 16Bit / 32Bit thing on the display options but there's nothing about it. >.> Also, I tried using it with the latest VMware and it didn't work too. It keeps showing me this black screen with the _...

---

