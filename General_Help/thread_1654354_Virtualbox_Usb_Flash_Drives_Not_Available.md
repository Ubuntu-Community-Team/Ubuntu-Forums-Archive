---
title: "Virtualbox Usb Flash Drives Not Available"
date: 2010-12-28
forum: General Help
---

### Post by gwm on 2010-12-28
Hi,
I have 64bit Maverick installed and am using VirtualBox 3.2.12 to run 32bit XP Home.
In the devices menu, nearly all the USB devices are grayed out. The printer is the only exception. It is working fine. If I plug in a flash drive (memory stick or whatever one wants to call it), Ubuntu sees it and it appears in the menu but is grayed out. When I remove the device, it disappears from the menu. This tells me that VirtualBox sees them.
How do I get to access these USB devices? What have I omitted to do?

---

### Post by Verbeck on 2010-12-28
you should add your user to vboxusers from
system>administration>users and groups>manage groups
then re-login

---

### Post by Ceiber Boy on 2010-12-28
> **Verbeck said:**
> you should add your user to vboxusers from
system>administration>users and groups>manage groups
then re-login
I had the same problem and this is the answer. but this function is not available in the version in the repositories so you have to use their free but not open source version from their web site.

---

### Post by gwm on 2010-12-28
Thanks,
I have been to the oracle site. I have replaced VirtualBox 3.2.12 with version 4. I have installed Guest additions. I have installed the Extension Pack (which is supposed to give USB 2.0 functionality).

Now I need to find this thing called vboxusers, to which I must add a user account. I've looked around in all the settings and menus I can find but I can't find anything suggesting such a setting.

Is it part of VirtualBox or is it somewhere inside the Windows XP Virtual Machine?

---

### Post by gradinaruvasile on 2010-12-28
vboxusers is a  group.

---

### Post by Verbeck on 2010-12-28
> **gwm said:**
> 
Now I need to find this thing called vboxusers, to which I must add a user account. I've looked around in all the settings and menus I can find but I can't find anything suggesting such a setting.

from ubuntu, go to system menu>administration>users and groups>manage groups

---

### Post by gwm on 2010-12-28
The confusion arose because of the wording of Verbeck's first post. Replace **from** with the word **in** and I would have understood first time.
I went there and found my user name was there already. So I checked the check box.
The "log out" and back in again also referred to Ubuntu and not to the virtual machine.
Now all is well in the camp of the Philistines.
Thank you for your help. :P

---

### Post by zbeckerd on 2011-01-29
Thanks.  Fixed it for me!

---

