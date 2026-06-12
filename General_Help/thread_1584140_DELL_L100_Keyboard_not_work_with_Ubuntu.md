---
title: "DELL L100 Keyboard not work with Ubuntu"
date: 2010-09-28
forum: General Help
---

### Post by Like2Learn on 2010-09-28
I have a virtual machine running Ubuntu Linux with VMware Player at my Windows XP desktop. The keyboard model is L100 by DELL. However, at  Ubuntu applications, such as Terminal and Text Editors, some keystroke generates invisible characters. For example, '/' is shown as 'é'. Under "System" -> "Preference" -> "Keyboard",  for Tab "Layout", I chose "Dell" as Vendor, and "Dell" as Model. However, it didn't solve the problem. Then I tried all models under Dell, and none of them work!
Anybody has a solution for me? Thanks!

---

### Post by Tylerjd on 2010-09-28
Changing the keyboard in the VM of Ubuntu shouldn't make any difference, as it is virtualized... Do you have VMWare Tools installed? What about trying another Linux OS or other OS? One last thing, make sure your mouse and keyboard are "captured" by the VM.

---

### Post by Like2Learn on 2010-09-28
> **Like2Learn said:**
> I have a virtual machine running Ubuntu Linux with VMware Player at my Windows XP desktop. The keyboard model is L100 by DELL. However, at Ubuntu applications, such as Terminal and Text Editors, some keystroke generates invisible characters. For example, '/' is shown as 'é'. Under "System" -> "Preference" -> "Keyboard", for Tab "Layout", I chose "Dell" as Vendor, and "Dell" as Model. However, it didn't solve the problem. Then I tried all models under Dell, and none of them work!
Anybody has a solution for me? Thanks!
 
 
Well, I solved my problem by simply choosing "USA" as keyboard layout instead of "Canada".

---

### Post by Tylerjd on 2010-09-28
Well thats good that you figured out what the problem was. Are you using a USA or Canada keyboard right now on the host computer?

---

