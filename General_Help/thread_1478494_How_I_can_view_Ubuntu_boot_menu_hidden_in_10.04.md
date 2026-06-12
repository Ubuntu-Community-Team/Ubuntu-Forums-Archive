---
title: "How I can view Ubuntu boot menu hidden in 10.04?"
date: 2010-05-09
forum: General Help
---

### Post by kako13 on 2010-05-09
Hi,

I would like see to the boot menu which is hidden by default on Ubuntu 10.04.

---

### Post by _0R10N on 2010-05-09
> **kako13 said:**
> Hi,

I would like see to the boot menu which is hidden by default on Ubuntu 10.04.

What do you mean by "boot menu"? You can install startupmanager and set it to display some boot info but, still, I don't get what do you are trying to accomplish.

---

### Post by kako13 on 2010-05-09
> **_0R10N said:**
> What do you mean by "boot menu"? You can install startupmanager and set it to display some boot info but, still, I don't get what do you are trying to accomplish.

When I refer to the boot menu I am referring to Grub.

I had attached an image.

---

### Post by Catharsis on 2010-05-09
From the release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#No%20delay%20for%20boot%20menu%20with%20GRUB%202](http://www.ubuntu.com/getubuntu/releasenotes/1004#No%20delay%20for%20boot%20menu%20with%20GRUB%202)

---

### Post by kako13 on 2010-05-09
> **Catharsis said:**
> From the release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#No%20delay%20for%20boot%20menu%20with%20GRUB%202](http://www.ubuntu.com/getubuntu/releasenotes/1004#No%20delay%20for%20boot%20menu%20with%20GRUB%202)

[B]Boot  options hidden by default on Desktop and Netbook CDs   
[/B]

 The Ubuntu 10.04 LTS Desktop and  Netbook CDs feature a new boot interface that is noninteractive by  default.  To configure advanced boot options, press any key at the first  boot screen.   



That does not work for me.

---

### Post by Catharsis on 2010-05-09
That's not where that link sends you. It sends you to:
> **No delay for boot menu with GRUB 2**

When using the GRUB 2 bootloader included in Ubuntu 10.04 LTS, the first boot option will by default be loaded automatically without pausing for user input. To interrupt the boot, users can hold down the Shift key to bring up the boot menu, allowing them to select a different boot option or to configure kernel arguments. ([https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202](https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202))

---

### Post by malangaman on 2010-05-09
Use synaptic to install start up manager. This is easiest. You can also google grub2 tutorial if you enjoy the command line.

---

### Post by kako13 on 2010-05-09
> **Catharsis said:**
> That's not where that link sends you. It sends you to:

Ah sorry.  That did the trick.

Thanks!

---

