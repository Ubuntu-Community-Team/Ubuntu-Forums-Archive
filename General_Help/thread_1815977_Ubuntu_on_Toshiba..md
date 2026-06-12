---
title: "Ubuntu on Toshiba."
date: 2011-08-01
forum: General Help
---

### Post by bals on 2011-08-01
I installed ubuntu 10.10 on a Toshiba laptop of my friend. He was not at all happy with the installation. The bluetooth did not work on his system, and the battery charge indicator was also not present. I tried a lot but nothing happened. Then when 11.04 came, i installed it. But the installation was not getting completed.

Is there any compatibility issues for Toshiba with Ubuntu?

---

### Post by lisati on 2011-08-01
I use a Toshiba without any problems, but mileage can vary. What model Toshiba are you using?

---

### Post by bals on 2011-08-01
the model is L650.

---

### Post by Topsiho on 2011-08-01
My Ubuntu runs well on my Toshiba A50 laptop.

But that does not mean that all Toshiba laptops do this. I don't think that T. produces laptops for running Linux, and if the laptops do, you are lucky, though I think most of them do.

Topsiho

---

### Post by Toz on 2011-08-01
> **bals said:**
> But the installation was not getting completed.
Can you be a little more specific? What didn't finish? Any error messages? At what point does it stop?

---

### Post by sammiev on 2011-08-01
I'm using a L650 as well as L500's with no problems to report with 11.04 and 11.10. All my Toshiba's are Intel based. They worked right out of the box without having to look for any extra drivers. GL :)

---

### Post by IWantFroyo on 2011-08-01
I have a Toshiba 235D S1360. With Ubuntu 10.10, it wouldn't even boot up without turning off acpi or using pci=noacpi. And as the kernel gets newer, it gets even more problems (???).

---

### Post by bals on 2011-08-01
> **Toz said:**
> Can you be a little more specific? What didn't finish? Any error messages? At what point does it stop?

Actually, i could install ubuntu from pen drive. But to complete installation, it has to boot into ubuntu after restarting. This was not happening. It would show ubuntu and the dots below and the system freezes. I had to force shutdown after that...

---

### Post by bals on 2011-08-01
> **sammiev said:**
> I'm using a L650 as well as L500's with no problems to report with 11.04 and 11.10. All my Toshiba's are Intel based. They worked right out of the box without having to look for any extra drivers. GL :)

Are you getting the battery charge indicator? Is your bluetooth working?

---

### Post by Toz on 2011-08-01
> **bals said:**
> Actually, i could install ubuntu from pen drive. But to complete installation, it has to boot into ubuntu after restarting. This was not happening. It would show ubuntu and the dots below and the system freezes. I had to force shutdown after that...

Do you have the latest bios installed? See: [http://ubuntuforums.org/showpost.php?p=9622930&postcount=3]("http://ubuntuforums.org/showpost.php?p=9622930&postcount=3")

You could also try the following kernel parameters:
```
acpi_osi=Linux
acpi_osi=\"Linux\"
acpi=copy_dsdt
```
To test them, see: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")

Also, blacklisting intel_ips worked in 10.10 - might work in 11.04. See: [http://ubuntuforums.org/showthread.php?p=10331367]("http://ubuntuforums.org/showthread.php?p=10331367")

---

### Post by sammiev on 2011-08-01
> **bals said:**
> Are you getting the battery charge indicator? Is your bluetooth working?

I use gnome3 and yes the battery charge indicator works fine and for the bluetooth, I don't have any bluetooth drive. GL :)

---

### Post by asmahakkim on 2011-10-09
hey did you sort out the battery issue?
i just installed ubuntu with wubi and have the same problem :(

---

