---
title: "Virtualbox - No USB."
date: 2009-09-15
forum: General Help
---

### Post by Roasted on 2009-09-15
I have the latest version from the Virtualbox web site.
I have USB enabled in the settings menu.
I have guest additions installed.
I've rebooted my Ubuntu host machine + XP virtual machine.

USB doesn't work.

What can I do?

---

### Post by DasEi on 2009-09-15
Have you also set it under machine > usb ?

---

### Post by steveneddy on 2009-09-15
[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by Roasted on 2009-09-15
steven - thanks for the link, but I had it working before my hard drive crashed when I redid everything without doing those edits. Is that really a solution or some sort of a workaround, because I hear those directions being posted a lot, yet I didn't use them before and I had it working.

DasEi - I don't see USB under "machines."

For the record I'm using Version 3.0.6.

---

### Post by steveneddy on 2009-09-15
You must add yourself as a user under vboxusers.

System --> Administration --> Users and Groups

Unlock

*password*

Manage Groups button

Scroll down to **vboxusers**

Select vboxusers, touch the Properties button

Add yourself as a user

Close

Finally, follow [this link]("https://help.ubuntu.com/community/VirtualBox/USB") and use the instructions for the version of Ubuntu that you are using.

Easy Peasy

---

### Post by Roasted on 2009-09-15
> **steveneddy said:**
> You must add yourself as a user under vboxusers.

System --> Administration --> Users and Groups

Unlock

*password*

Manage Groups button

Scroll down to **vboxusers**

Select vboxusers, touch the Properties button

Add yourself as a user

Close

Finally, follow [this link]("https://help.ubuntu.com/community/VirtualBox/USB") and use the instructions for the version of Ubuntu that you are using.

Easy Peasy


So, uh... hate to say it but... I'm already part of that group..

See why I'm confused now? :(

---

### Post by steveneddy on 2009-09-17
> **Roasted said:**
> So, uh... hate to say it but... I'm already part of that group..

See why I'm confused now? :(

well........

---

### Post by PureLoneWolf on 2009-09-17
For me, it wouldn't work without a reboot after adding myself to the group.

Have you restarted the PC since you installed?

---

### Post by The Thug on 2009-09-17
Did you upgrade VB through Synaptic ?

I lost the ability to use my USB ports after upgrading through Synaptic. As far as I can tell, the Synaptic version is the OSE version and doesn't allow the USB options.

I had to d/load the PUEL version, re-install and then followed the guidelines on this thread [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by Roasted on 2009-09-17
> **PureLoneWolf said:**
> For me, it wouldn't work without a reboot after adding myself to the group.

Have you restarted the PC since you installed?

Oh yeah, several times. I had it working before and then I got a popup with Virtualbox one day that a newer version was available on the web site. So I downloaded the newer version. Weeks later I had noticed I lost USB functionality. I do admit I don't use USB in virtual machines pretty much... ever... but I had to install a Windows app to adjust something on my phone. That's when I realized my phone wasn't mounting as a storage device, which it always did prior and still does in Ubuntu.

---

### Post by yellowbread on 2009-09-17
steveneddy, what's that saying about horses and water?

Anyway Roasted, yes that's the solution suggested in the vbox documentation. Edit the fstab file as suggested. Your usb will work.

---

### Post by Roasted on 2009-09-17
> **yellowbread said:**
> steveneddy, what's that saying about horses and water?

Anyway Roasted, yes that's the solution suggested in the vbox documentation. Edit the fstab file as suggested. Your usb will work.

I understand. It's just confusing how I had it before without the fstab.

---

### Post by yellowbread on 2009-09-18
Yeah, it seems that I once had it working without the fstab edit too. Can't remember how anymore.

---

