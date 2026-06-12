---
title: "Will updates (Kernel etc.) work if I use my own Bootmanager..?"
date: 2012-03-08
forum: General Help
---

### Post by sirbender on 2012-03-08
Hi,

for various reasons I use my own boot manager - Grub Legacy. Thus when I  install Ubuntu I uncheck the option where the Ubuntu installer places  Grub2 in my MBR.

I noticed however later updates (like 10.04, 10.04.1, 10.04.2, 10.04.3,  10.04.4, etc.) install a new kernel. Normally these updates just edit  the Grub2-boot file and add the new kernels as a new default boot  option.

Since I use manual boot I miss out on these new kernels.

Any suggestions what I can or should do? (Switching to Grub2 and let Ubuntu manage it is not an option!)

Thanks,
sb

---

### Post by WorMzy on 2012-03-08
You could always install the kernel updates and then update grub legacy yourself.

I use grub legacy too; although I don't use Ubuntu these days, I used to keep my menu.lst updated manually.

---

### Post by sirbender on 2012-03-08
Thanks. That's what I plan to do.

Do you have any idea when the Kernel is updated? Theoretically every time the update manager is called or only after a new subversion like between 10.04 and 10.04.1 ?

Do I have to regularly look for new kernel files and enter them manually or is there a way to get informed whenever the kernel updates?

Thanks,
sb

---

### Post by WorMzy on 2012-03-08
Sorry, I've never understood Ubuntu's release policy regarding anything; but I believe that you should get alerted to kernel updates whenever they're available so long as you have the linux-image-generic package installed.

Ubuntu tends to stick with outdated kernels, rather than following the bleeding edge of kernel development, so you probably won't get that many kernel updates between releases (there's been a release candidate of kernel 3.3.0 every week for the past six weeks, to give you some indication of how fast kernel development moves).

---

### Post by sirbender on 2012-03-08
Thanks!

I did more reading on Grub2 since I will probably use it at some point anyways. I get the impression you shouldn't touch grub.cfg but auto-generate it. With Grub-Legacy it was all manual...at least that's how I used it. Maybe I understand Grub2 wrong?

Thanks,
sb

---

