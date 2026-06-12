---
title: "problem in installing ubuntu10.4"
date: 2010-07-23
forum: General Help
---

### Post by prakhar_garg009 on 2010-07-23
hello friends
i am using ubuntu9.4 and i want to iinstall ubuntu 10.4
today i download ubuntu 10.4 in my usb drive and when i restart my laptop it open direct my older version also when i boot my usb drive it doesn't show anything just open the older version of ubuntu
please tell me what should i do....

---

### Post by nidzo732 on 2010-07-23
Did you set boot priority in bios.

---

### Post by prakhar_garg009 on 2010-07-23
how to do that

---

### Post by nidzo732 on 2010-07-23
when you start your laptop there should be a message 
"press [some key(shold be F! or Esc or del...) for menu]". Press the key in the message and you will go to the BIOS menu. Search for "boot priority" or
"boot order" (menu can be diferent on diferent computers) and set usb to boot before HDD. Restart your laptop and it will boot into install usb.
After install change the boot prioryty so the HDD is first.

---

### Post by watupgroupie on 2010-07-23
A lot of Bios also have a one time boot menu. Select that option upon loading and boot off your USB.

---

### Post by prakhar_garg009 on 2010-07-23
no man it is not working 
try to give me some other way

---

### Post by watupgroupie on 2010-07-23
Be more specific. What happens you try to boot off your USB?

---

### Post by prakhar_garg009 on 2010-07-23
i have not try it yet but if i boot off usb than usb will not work so how than it install

---

### Post by watupgroupie on 2010-07-23
Do you have a CD drive? Use the LiveCD instead.

---

### Post by nidzo732 on 2010-07-23
how did you put ubuntu on USB. Did you just copy the image or did you use startup disk creator.

---

### Post by prakhar_garg009 on 2010-07-23
i just copy the image

---

### Post by nidzo732 on 2010-07-23
It won't work that way. Start the ubuntu (the one installed on your computer). Put your usb in and copy the image to your home folder. Then go to system>administration>startup disk creator. On the upper part click other and find the image in your home directory , on the lower part select your usb and click erase after that select your usb again and click "make startup disk".Then restar and boot from usb

---

