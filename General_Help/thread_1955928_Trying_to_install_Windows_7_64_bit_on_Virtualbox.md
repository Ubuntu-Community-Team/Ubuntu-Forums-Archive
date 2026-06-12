---
title: "Trying to install Windows 7 64 bit on Virtualbox"
date: 2012-04-10
forum: General Help
---

### Post by Basher101 on 2012-04-10
i made all the settings for 64 bit, selected the .iso (which i ripped with Imgburn on my laptop, it does work as i installed windows twice on my desktop with it) and now i get this..


google did not help much as it does not really provide  a solution to this specific problem

---

### Post by Cheesemill on 2012-04-10
You could try booting directly from the DVD instead of the ISO file just in case there was a problem with the image creation.

Also you need to be running a 64 bit linux installation and have virtualization enabled in your BIOS (either VT-x or AMD-V depending on your processor).

---

### Post by Basher101 on 2012-04-10
> **Cheesemill said:**
> You could try booting directly from the DVD instead of the ISO file just in case there was a problem with the image creation.

Also you need to be running a 64 bit linux installation and have virtualization enabled in your BIOS (either VT-x or AMD-V depending on your processor).

i got no blank DVDs to burn it...i have been installing windows and linux from USB sticks since 2008

also virtualization is enabled

---

### Post by Basher101 on 2012-04-10
Nevermind, i am facepalming right now, because i took a look in the BIOS and saw the HDD controller was set to IDE, which was why my windows did not boot anymore. It WAS set to AHCI, but somehow got reset, and i knew the cause, but not what it exactly it did. Now my Windows 7 dualboot works again. I wont go into detail here. Thanks that you made me double check my BIOS, here is some popcorn :popcorn:

meanwhile i will continue facepalming and make a backup...

---

