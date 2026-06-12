---
title: "how to disable apic on an installed ubuntu"
date: 2010-05-10
forum: General Help
---

### Post by tunznath on 2010-05-10
Hi 
A friend of mine has a problem on Karmic - he cant get past the screen just after the select the OS screen(grub screen) it says something about apic, but when he puts in the live CD, and presses F6 and selects expert and checks "no Apic" his computer boots, 
MY question - is there a way to get into the installed ubuntu on the HDD) to set the no apic so that he can boot from the installed distro.

Hope this is clear

thanks in advance
Nath

---

### Post by Iowan on 2010-05-10
I haven't (yet) tried to get acquainted with Grub2, but [here]("https://help.ubuntu.com/community/Grub2") is a help page I will use when I do...

---

### Post by efflandt on 2010-05-10
I believe from the grub menu you press "e" to edit the kernel parameters, so he could try doing that and adding **noapic** to the kernel parameters after **quiet splash** and a space.  In fact if he wants to see all boot messages, and in case usplash is a problem, he could delete the **quiet splash** and try **noapic** instead of that.

Other possibilities are **apic=off** or **lapic=off**.

Do not confuse "apic" (related to interrupts) with "acpi" (related to power features), same letters in a different order.

I had an old PC that would not automatically use acpi because its BIOS pre-dated 1999, and apparently had some problem with apic, so had to use lapic instead.  For it to work properly and power down completely I used: acpi=force lapic.  But again acpi and apic are two different things.

---

### Post by tunznath on 2010-05-11
Hi
thanks for the brain reminder EFFLANDT  it was ACPI - 
so thank for the 
"I had an old PC that would not automatically use acpi because its BIOS pre-dated 1999, and apparently had some problem with apic, so had to use lapic instead. For it to work properly and power down completely I used: acpi=force lapic. But again acpi and apic are two different things."


would i add "acpi=force lapic" to the kernel parameters after quiet splash and a space. as well
many htnaks to all who replied
Nath

---

### Post by efflandt on 2010-05-11
This is somewhat dated, but lists how to add boot options when booting a live CD or grub.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Nobody would really know what parameters you might need without knowing anything about the hardware (make/model of the PC, age, and/or output of **sudo lspci -v**). Once you find parameters that allow it to boot, look through dmesg (**dmesg | less**) for any errors related to acpi, apic, or lapic to see if you need to try something else or additional.

However, that link was written for legacy grub, so if you figure out what works and want to make it permanent for grub2, you would actually **gksu gedit /etc/default/grub** (or sudo nano that file) and then **sudo update-grub**.

The first line below is for regular kernels, or the 2nd line is for all kernels including recovery kernels.  You can add kernel parameters as a space separated list within the quotes.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

