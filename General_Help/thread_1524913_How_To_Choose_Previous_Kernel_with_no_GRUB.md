---
title: "How To Choose Previous Kernel with no GRUB"
date: 2010-07-05
forum: General Help
---

### Post by psychok7 on 2010-07-05
hi there.. i was wondering how do i choose a previous Kernel without a GRUB?? I have a netbook with only Ubuntu (UNR) installed so every time i update my kernel and so on i cannot see/choose the kernel version i want (i believe it enters the most recent one by default).
Is there a way to do that without a grub or i have to install it even if i dont have a second OS?

---

### Post by arpanaut on 2010-07-06
Try hitting the SHIFT key repeatedly during the boot process, It should bring you to the grub menu.  Sometimes it takes more than one boot attempt to "time" the shift key response.

---

### Post by bodhi.zazen on 2010-07-06
> **psychok7 said:**
> hi there.. i was wondering how do i choose a previous Kernel without a GRUB?? I have a netbook with only Ubuntu (UNR) installed so every time i update my kernel and so on i cannot see/choose the kernel version i want (i believe it enters the most recent one by default).
Is there a way to do that without a grub or i have to install it even if i dont have a second OS?

See this wiki page :

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I think you want one of the options in this section :

[https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29)

---

### Post by Yarui on 2010-07-06
When you say you don't have a grub do you mean you have set it up so that the grub menu doesn't show at startup?  I don't think you can just not have a grub unless you have set your system up to use some other boot manager.  You could try editing the /etc/default/grub file and make sure you have the following line:
```
GRUB_TIMEOUT=10
```10 meaning that it waits for you to make a selection for 10 seconds, this value can be changed to whatever you prefer.  If you have to change this line, be sure to run:
```
sudo update-grub
```This is a grub2 feature that builds your grub menu.  The /etc/default/grub file tells update-grub how to build your grub menu.  Update grub adds all the kernels in your /boot directory to your grub boot list so if this makes the boot menu show up it should allow for booting into old kernels so long as they are still installed on your machine.

EDIT: After looking at the grub2 documentation, it seems that the GRUB_HIDDEN_TIMEOUT line is the one you are probably interested in, not the GRUB_TIMEOUT line.  Changing the line to read:
```
#GRUB_HIDDEN_TIMEOUT=0
```
With a # in front will probably do what you are wanting.

---

