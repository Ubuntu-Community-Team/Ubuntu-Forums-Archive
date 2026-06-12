---
title: "The Boot Splash Screen"
date: 2006-06-26
forum: General Help
---

### Post by Sagotis on 2006-06-26
Hi All!

I was wondering if there was a way to remove the splash screen from the boot process?

I would like to boot fully in text mode like debian, where there is no splash boot screen.

If anyone one can help I would appreciate it.

Thanks

Sagotis

---

### Post by caserio on 2006-06-26
Hi, 

Uninstall usplash and edit your /boot/grub/menu.lst: delete the splash option (kernel line).

---

### Post by Sagotis on 2006-06-26
[QUOTE=caserio] Remove usplash [/QUOTE]

I assume u mean apt-get remove usplash?

The only problem with this is that it also wantes to remove the ubuntu-desktop with it :neutral: 

There has to be a way to disable this without the removal of Gnome?

Sagotis

---

### Post by aysiu on 2006-06-26
Removing *ubuntu-desktop* doesn't remove Gnome. That's just a pointer to all the default applications in Ubuntu. Removing the pointer removes only the pointer--nothing else.

---

### Post by Sagotis on 2006-06-26
[QUOTE=aysiu]Removing *ubuntu-desktop* doesn't remove Gnome. That's just a pointer to all the default applications in Ubuntu. Removing the pointer removes only the pointer--nothing else.[/QUOTE]


And what is a **pointer** of defult applications mean?

Sagotis

---

### Post by caserio on 2006-06-26
I'm using kubuntu. I did remove the kubuntu-desktop and is's OK.

---

### Post by aysiu on 2006-06-26
[QUOTE=Sagotis]And what is a **pointer** of defult applications mean?

Sagotis[/QUOTE]
It means that if you say to Ubuntu "install *ubuntu-desktop*," it'll look to see what all the applications are that *ubuntu-desktop* points to (GAIM, Firefox, usplash, etc.) and install all of those programs.

When you say to Ubuntu "uninstall *ubuntu-desktop*," it'll uninstall the pointer but all the other programs will stay installed (GAIM, Firefox, usplash, etc.).

From Synaptic's description of the pointer package: > **The Ubuntu desktop system**
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).

---

### Post by Sagotis on 2006-06-26
[QUOTE=aysiu]It means that if you say to Ubuntu "install *ubuntu-desktop*," it'll look to see what all the applications are that *ubuntu-desktop* points to (GAIM, Firefox, usplash, etc.) and install all of those programs.

When you say to Ubuntu "uninstall *ubuntu-desktop*," it'll uninstall the pointer but all the other programs will stay installed (GAIM, Firefox, usplash, etc.).[/QUOTE]

Hmmm so from this then it is ok to uninstall Ekiga, even though it wants to also uninstall unbuntu-desktop as well?

Btw thank you aysiu :D

Sagotis

---

### Post by aysiu on 2006-06-26
[QUOTE=Sagotis]Hmmm so from this then it is ok to uninstall Ekiga, even though it wants to also uninstall unbuntu-desktop as well?

Btw thank you aysiu :D

Sagotis[/QUOTE]
Yes. But if you ever want to upgrade to Edgy Eft (say, in about four months), you should reinstall *ubuntu-desktop* before you upgrade.

---

### Post by Sagotis on 2006-06-26
[QUOTE=caserio]Hi, 

Uninstall usplash and edit your /boot/grub/menu.lst: delete the splash option (kernel line).[/QUOTE]

Coudl I just edit the /boot/grub/menu.lst by deleting the splash option?

Sagotis

---

### Post by aysiu on 2006-06-26
Yes, you could do that, too. If there's a kernel upgrade, though, you'll have to remove the option again, though.

---

### Post by Sagotis on 2006-06-26
[QUOTE=aysiu]Yes, you could do that, too. If there's a kernel upgrade, though, you'll have to remove the option again, though.[/QUOTE]

I see.

Thank you both, caserio and aysiu for you speedy replies and thorough explanations!

Sagotis

---

