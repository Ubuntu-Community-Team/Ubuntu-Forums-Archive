---
title: "My Karmic does not have GRUB2"
date: 2009-12-21
forum: General Help
---

### Post by OldGrantonian on 2009-12-21
"GRUB 2 is the default boot loader and manager for Ubuntu 9.10"

That statement is in the following article:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

But when I open Synaptic Package Manager, I see that GRUB2 is not installed? The only green checked items are grub-common and grub-pc

Shall I install GRUB2?
.

---

### Post by Leppie on 2009-12-21
the grub2 package is only a dummy package. installing it will result in the installation of grub-common and grub-pc.

---

### Post by DeMus on 2009-12-21
> **OldGrantonian said:**
> "GRUB 2 is the default boot loader and manager for Ubuntu 9.10"

That statement is in the following article:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

But when I open Synaptic Package Manager, I see that GRUB2 is not installed? The only green checked items are grub-common and grub-pc

Shall I install GRUB2?
.

Did you do an update form an earlier version? Then Grub 1 is still there. Nothing to worry about.

---

### Post by SecretCode on 2009-12-21
What version of grub-pc do you have? In Karmic by default it's 1.97~beta4-1ubuntu1.4 - and that **is** Grub2.

---

### Post by Leppie on 2009-12-21
> **SecretCode said:**
> What version of grub-pc do you have? In Karmic by default it's 1.97~beta4-1ubuntu1.4 - and that **is** Grub2.

yes, grub2 consists of grub-common and grub-pc.

---

### Post by OldGrantonian on 2009-12-21
Thanks to everyone for all the usual fast and helpful responses :)

I can confirm that the installed version number for grub-pc is:

1.97~beta4-1ubuntu1.4

So, as everyone says, I have GRUB2 :)

---

### Post by Leppie on 2009-12-21
> **OldGrantonian said:**
> Thanks to everyone for all the usual fast and helpful responses :)

I can confirm that the installed version number for grub-pc is:

1.97~beta4-1ubuntu1.4

So, as everyone says, I have GRUB2 :)

yes, you do have grub2 installed. expect some grub updates to come through though (if you have update manager enabled).

---

