---
title: "How to suspend to disk/memory?"
date: 2011-03-02
forum: General Help
---

### Post by RobotGymnast on 2011-03-02
I installed a minimal build of Ubuntu, and I'm having difficulty getting my Hibernate and Standby options back. Could somebody help me?

Thanks for any help!

---

### Post by RobotGymnast on 2011-03-06
Anybody?

---

### Post by WorMzy on 2011-03-06
Never used such functions myself, but I believe that you need a large swap partition for them to work. What size is yours?

---

### Post by RobotGymnast on 2011-03-06
> **WorMzy said:**
> Never used such functions myself, but I believe that you need a large swap partition for them to work. What size is yours?

According to gparted, it's 2GB. I have about 3GB of memory. Would this hinder both suspend to disk and suspend to RAM?

---

### Post by WorMzy on 2011-03-06
Pass.

You may need to install the uswsusp package, if you haven't done so already.

This article may be of use to you: [https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate)

---

### Post by RobotGymnast on 2011-03-06
> **WorMzy said:**
> Pass.

You may need to install the uswsusp package, if you haven't done so already.

This article may be of use to you: [https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate)

Hmm.. I have neither pm-utils nor anything to do with acpi installed (except powermgmt-base). Do I need these?

---

### Post by ankspo71 on 2011-03-06
Hi,
I'm not sure if this will help or not with a manually triggered suspend or hibernate, but a default Ubuntu 10.10 desktop installation has 'gnome-power-manager' installed and it is enabled in the System > Preferences > Startup Applications list.

Name: Power Manger
Command: gnome-power-manager
Comment: Power management daemon

It think it also provides the Power Management preferences at System > Preferences > Power Management. For example, it lets you choose what to happen when you press the power button on your computer: (Ask Me, Suspend, Hibernate, Shutdown)

Hope this helps.

---

### Post by RobotGymnast on 2011-03-06
> **ankspo71 said:**
> Hi,
I'm not sure if this will help or not with a manually triggered suspend or hibernate, but a default Ubuntu 10.10 desktop installation has 'gnome-power-manager' installed and it is enabled in the System > Preferences > Startup Applications list.
...

Thanks, but I already have that installed. It doesn't show the hibernate or standby options.

---

