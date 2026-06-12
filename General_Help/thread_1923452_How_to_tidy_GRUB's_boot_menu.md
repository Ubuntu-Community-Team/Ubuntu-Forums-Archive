---
title: "How to tidy GRUB's boot menu"
date: 2012-02-10
forum: General Help
---

### Post by Chris62 on 2012-02-10
Hello,

I recently did a clean install of Ubuntu 11.10 on my dual boot computer having first tried unsuccessfully to upgrade 11.04 over the internet.

I found after installing it that the GRUB boot menu had several entries for the kernel as well as an entry for "Previous versions of Linux".

By using Synaptic and 'sudo update-grub' afterwards I was able to get rid of some of the kernel entries but I can't see how to get rid of the "Previous versions of Linux" entry. Can anyone help, please?

Clicking on this entry reveals that I could boot with version 3.0.0.15 whereas the main entry says that I can use version 3.0.0.15-pae which seems to work OK although I am not sure what 'pae' is

---

### Post by frone on 2012-02-11
Have you tried using the StartUp-Manager?  It is available from the Software Center and may help you resolve your issues.

---

### Post by Bucky Ball on 2012-02-11
[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

... all you need. ;)

But remember; it is always a good idea to keep the current (stable) kernel and its recovery kernel in the menu, PLUS the previous kernel (hopefully stable or one that is) and its recovery in case something breaks in either and you need a fall back (for instance, if you can't boot one of the kernels).

---

### Post by Cookieh on 2012-02-11
I think there are stable current versions of Grubs out there which are latest version, for instance, you can use the new Grub of Precise Pangolin for 11.10 as i have seen the code of my friends work.

---

### Post by ottosykora on 2012-02-11
>Clicking on this entry reveals that I could boot with version 3.0.0.15 whereas the main entry says that I can use version 3.0.0.15-pae which seems to work OK although I am not sure what 'pae' is<

not sure how you got all that, but the kernels have version with and without pae , where the pae version is useful on computer with lot of ram, as 32bit operating systems were not able to access all the memory. The pae kernels have an extension to enable you to use all the ram you have in your computer.
If during the installation, bigger ram is detected then standard kernel can handle, the pae version in picked.
(pae = physical address extension)

---

