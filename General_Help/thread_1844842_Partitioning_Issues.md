---
title: "Partitioning Issues"
date: 2011-09-15
forum: General Help
---

### Post by MisterCrazy8 on 2011-09-15
I have a Google Cr-48 notebook. The SSD only has 6 gb that I am comfortable allocating to Ubuntu. I need to move /usr to an external HDD. I also will move my /Home to another partition on the drive. I am going to specify the requirements that I must meet.

I CANNOT install Ubuntu again
I CANNOT use LiveUSB or LiveCD or LiveDVD
I CANNOT boot the entire OS from the USB Drive
I CANNOT do anything that requires GRUB (GRUB IS NEITHER INSTALLED NOR UTILIZED, TRUST ME I AM CERTAIN)
I CANNOT boot into Recovery Mode (reboot recovery or pressing button as both require GRUB) at all
I want to know if it can be done and how it can be done in detail. I have tried this many times. Each time something new went wrong.

I am asking for assistance on how to do something, I don't want anyone saying "moving the /usr directory is a bad idea" or anything of that nature. If I had another option that I felt comfortable with I wouldn't be asking this question.

Any assistance that anyone could provide would be greatly appreciated. I will provide more details in the future if requested/required. I am sorry for my pessimism, but after 5 re-installs my patience grows a little thin.

Thank you!

I have also posted this at askubuntu.com

---

### Post by searchfgold6789 on 2011-09-15
You can do this by moving the files into your desired partition. Then **add the partition to your fstab file** (important) and make a symbolic link to the files. Let me know if you need step-by-step. I would hesitate greatly to do this with the /usr directory.
There is a GUI for doing this exact thing called ubuntu-tweak! I highly recommend it!

---

### Post by haqking on 2011-09-15
> **searchfgold6789 said:**
> You can do this by moving the files into your desired partition. Then **add the partition to your fstab file** (important) and make a symbolic link to the files. Let me know if you need step-by-step. I would hesitate greatly to do this with the /usr directory.
There is a GUI for doing this exact thing called ubuntu-tweak! I highly recommend it!

+1

see here for info on fstab [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

and [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

