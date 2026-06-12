---
title: "Adding 8.10 Intrepid to 10.04 Lucid (dual boot)"
date: 2010-05-04
forum: General Help
---

### Post by StuartN on 2010-05-04
I would like to add Ubuntu 8.10 as a dual boot option to my Ubuntu 10.04 installation. It is not immediately obvious to me how to do so, because running the CD installation will presumably overwrite Grub2 with Grub (and might not successfully boot 10.04).

How do I install 8.10 without overwriting my Grub2, and then add 8.10 to the Grub2 menu?

---

### Post by dcstar on 2010-05-04
> **StuartN said:**
> I would like to add Ubuntu 8.10 as a dual boot option to my Ubuntu 10.04 installation. It is not immediately obvious to me how to do so, because running the CD installation will presumably overwrite Grub2 with Grub (and might not successfully boot 10.04).

How do I install 8.10 without overwriting my Grub2, and then add 8.10 to the Grub2 menu?

In the last part of the install process select the Advanced options and install Grub somewhere other than the MBR.

---

### Post by StuartN on 2010-05-04
> **dcstar said:**
> In the last part of the install process select the Advanced options and install Grub somewhere other than the MBR.

I do not want to install Grub at all because it will overwrite Grub2 - is there no method of installing an older version of Ubuntu and then adding it to the existing Grub2?

---

### Post by suryaccnamcse on 2010-05-04
Right now what do you have installed? is it 8.10 or 10.04?
if you have 10.04 installed and you are trying to add 8.10 to the grub options. Just pop in the CD and start the installation as usual and be assured that grub2 will not be overwritten. 
If you have it other way around, you should not face any issue.

---

### Post by dcstar on 2010-05-04
> **StuartN said:**
> I do not want to install Grub at all because it will overwrite Grub2 - is there no method of installing an older version of Ubuntu and then adding it to the existing Grub2?

You will **not** be overwriting anything if it is installed on a partition that isn't booted.

---

### Post by StuartN on 2010-05-04
> **suryaccnamcse said:**
> Just pop in the CD and start the installation as usual and be assured that grub2 will not be overwritten.

I have 10.04 installed. I want to install 8.10 to dual-boot beside the 10.04.

Is there any point in the installation where it will ask about Grub? I was assuming that 8.10 would be Grub2-unaware and would insist on installing Grub somewhere.

And do I have to run update-grub2 afterwards to add the new 8.10 installation to the menu?

---

### Post by suryaccnamcse on 2010-05-04
No there is no point in the installation where it asks about grub. Grub2 will recognize 8.10, you will have no issues. I have 9.10 and 10.04 installed and they work perfectly...no need to run update-grub2.

---

