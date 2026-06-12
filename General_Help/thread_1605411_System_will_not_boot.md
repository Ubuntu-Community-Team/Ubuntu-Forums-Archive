---
title: "System will not boot"
date: 2010-10-25
forum: General Help
---

### Post by theronstar on 2010-10-25
I have a Dell Inspiron 1545 I got last week. I had Win7 preinstalled and I wanted Ubuntu for university so I installed that too. I came out of Ubuntu after installing it and went into Windows for something. I shut down but the next morning - ever since I power up the laptop - I get this message saying "Module name not found. Aborted. Press any key to exit".

Dell tech support were unaware of this problem previously but they have offered to come round and put the pc back to factory settings. Do you think this is the only way I can go forward from this?

Thanks in advance.

---

### Post by katykat on 2010-10-25
[QUOTE=theronstar;10023864]I have a Dell Inspiron 1545 I got last week. I had Win7 preinstalled and I wanted Ubuntu for university so I installed that too. I came out of Ubuntu after installing it and went into Windows for something. I shut down but the next morning - ever since I power up the laptop - I get this message saying "Module name not found. Aborted. Press any key to exit".

Your Win7 boot sector might be trashed. 

Grub2 overwrote it when installing. 

To fix ASAP and get Win back, boot to a BOOTCD such as Hirens, or perhaps GRML (havent tried thjat last yet) get to a DOS prompt and type fdisk /mbr

That SHOULD  take grub off the machine and allow you to boot.

---

