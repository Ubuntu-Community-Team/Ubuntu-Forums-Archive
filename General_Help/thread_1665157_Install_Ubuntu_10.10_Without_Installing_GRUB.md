---
title: "Install Ubuntu 10.10 Without Installing GRUB?"
date: 2011-01-11
forum: General Help
---

### Post by Socialsymbol on 2011-01-11
Is there any way to install Ubuntu without needing to install GRUB? When going through the installation process and getting to the point where you partition  your drives in 10.10, I see an option to select *where* to install GRUB, but there's no option to completely disregard it or to not install it.

The reason I want to install Ubuntu without GRUB is because I already have Arch on my primary drive with GRUB installed on the MBR, and even though I know I could just replace that grub with GRUB2 from the Ubuntu install, I really don't want to because personally I prefer GRUB greatly over GRUB2.

---

### Post by Quackers on 2011-01-11
That option is no longer available on the 10.10 installer. What I would suggest is plugging in a flash drive and installing grub to that. I suspect it will be ok, but I haven't tried it. At your own risk I'm afraid :-) If grub legacy manages to boot 10.10!

---

### Post by Socialsymbol on 2011-01-11
> **Quackers said:**
> That option is no longer available on the 10.10 installer. What I would suggest is plugging in a flash drive and installing grub to that. I suspect it will be ok, but I haven't tried it. At your own risk I'm afraid :-) If grub legacy manages to boot 10.10!
Raaaaaaage why would they do this.....

Edit: I might just install the new Debian Squeeze then and just hope for the best. Not sure though.

---

### Post by Quackers on 2011-01-11
I don't know. There are one or two "inconsistencies" in the 10.10 installer. For example, don't choose the "install alongside" option - it has a habit of eating existing operating systems!

---

### Post by Jay Car on 2011-01-11
> **Socialsymbol said:**
> Raaaaaaage why would they do this.....

Edit: I might just install the new Debian Squeeze then and just hope for the best. Not sure though.

Why would you be upset because of a Wubi install?  Installing Ubuntu inside of Windows is a nice way for people to test Ubuntu before they decide to install it on its own drive. I think Wubi is a rather clever piece of software, but I don't believe it was ever meant to be a permanent solution. To help you understand it better, here's a [really useful thread about Wubi]("http://ubuntuforums.org/showthread.php?t=1639198").

I'm curious, if you feel you can properly install Debian, why do you feel you can't properly install Ubuntu?  It's really not hard to do.

---

### Post by Socialsymbol on 2011-01-12
> **Jay Car said:**
> Why would you be upset because of a Wubi install?  Installing Ubuntu inside of Windows is a nice way for people to test Ubuntu before they decide to install it on its own drive. I think Wubi is a rather clever piece of software, but I don't believe it was ever meant to be a permanent solution. To help you understand it better, here's a [really useful thread about Wubi]("http://ubuntuforums.org/showthread.php?t=1639198").

I'm curious, if you feel you can properly install Debian, why do you feel you can't properly install Ubuntu?  It's really not hard to do.
What in my post makes you think I'm installing from the Wubi? I'm just booting the live disk and installing from there.

---

### Post by mike555 on 2011-01-12
Ubuntu requires Grub to start , but you can install grub to the partition your installing ubuntu to, and use a different bootloader to chain load to it ...... for instance a bootloader on a cd or usb stick ..

 that is what I do , I install grub to each partition I install Linux to , then I use a bootloader called " Gag "   ,   
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

