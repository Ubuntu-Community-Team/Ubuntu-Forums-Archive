---
title: "Boot selection Window"
date: 2010-09-02
forum: General Help
---

### Post by FahadMKS on 2010-09-02
I have an issue with the Ubuntu boot selection window.

I had purchased a Desktop and installed the Ubuntu OS first on a part of the HDD and then I installed the Windows XP to that on the remaining part and now after installing the XP to the computer, I am not getting the option to select the OS so as to boot to Ubuntu.

How can I get it back without reminstalling Ubuntu?

Any help from you guys will be appreciated.

Fahad Moideen KS

Note: If you can, please send me a mail on to [email]fahadmoideenks@gmail.com[/email] so as to get the result wherever I am.

---

### Post by chinoto on 2010-09-02
Boot from the Ubuntu disc
Mount your ubuntu install by click on it in the "Places" menu (uber simple :D)
Check your harddrive's device name with "System> Administration> GParted"
Type this into terminal "sudo grub-install --root-directory=/media/*ubuntu partition* /dev/*drive*" Try to save the output of it in case it doesn't work. (although it should since I used it just a couple hours ago)

---

