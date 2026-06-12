---
title: "Dual boot"
date: 2010-09-18
forum: General Help
---

### Post by Kareta on 2010-09-18
I had a clean 1tb harddrive, which I installed Ubuntu on, works great. 

However, I have an old 500gb harddrive sitting around which I loaded windows 7 on earlier today. How can I set up dual boot between the two hard drives? GRUB?

WITHOUT messing up my linux hard drive, it has much more important data then my windows does. 

Any help is appreciated.

---

### Post by andrewthomas on 2010-09-19
Updating grub with both drives plugged in should pick up the windows install and add it to your grub. Is this not the case?

---

### Post by 3dgard on 2010-09-19
Well if you have both hard drives plugged in at the same time and it picks up Windows 7 instead of Ubuntu... download EasyBCD to modify the bootloader.

If you are in ubuntu, the update your grub... I think its by running:

sudo apt-get upgrade grub

But i could be wrong... google it!!

---

### Post by Rubi1200 on 2010-09-19
> **3dgard said:**
> Well if you have both hard drives plugged in at the same time and it picks up Windows 7 instead of Ubuntu... download EasyBCD to modify the bootloader.

If you are in ubuntu, the update your grub... I think its by running:

sudo apt-get upgrade grub

But i could be wrong... google it!!
No, the correct command is ```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-09-19
You could just plug it in the USB port and choose the USB drive to boot in your BIOS.
That way you do not have to do anything at all. Ubuntu boots on sda by default and then
you can choose the sdb (external) when you want that to boot it. Do not plug it in when
you are not going to use.
Look in your BIOS for settings, they are there. It gives you choice to set defaults and it also gives you choice on each boot if you want. That is what you want. Then one drive has grub2 and one drive has Windows boot manager. Set CD as first to boot when in BIOS as default so if anything ever go's wrong with anything you can boot off of CD to fix and that is any Operating System.

---

### Post by Dustin2128 on 2010-09-19
I'm thinking you should also change the pins on the secondary drive to slave if they're not already.

---

