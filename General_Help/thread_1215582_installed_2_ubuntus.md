---
title: "installed 2 ubuntus"
date: 2009-07-17
forum: General Help
---

### Post by zeroblackcat on 2009-07-17
wile trying to install ubuntu i picked side by side first than i reinstalled ubuntu than clicked entire harddrive so my windows vista is gone but i think the ubuntu os from before is not gone so how do i delete the other os 
i am new so please go easy on the ubuntu 

thank you guys

---

### Post by NightwishFan on 2009-07-17
Boot into the Ubuntu live cd and use the partition editor to arrange things like you want, then reinstall grub in recovery mode.

---

### Post by zeroblackcat on 2009-07-17
> **NightwishFan said:**
> Boot into the Ubuntu live cd and use the partition editor to arrange things like you want, then reinstall grub in recovery mode.

what is ubuntu live cd and what is grub  ? i

---

### Post by NightwishFan on 2009-07-17
Yes, my apologies. That response must seem curt. :(

The Ubuntu live CD is what you used to install. It runs the desktop from the CD only. Just pick Try Ubuntu when you restart with the CD in. Then when the desktop loads, go to System -> Administrator -> Partition Editor.

Attach a screenshot of the partition editor here, and I will help you fix your drive.

When we get that done, we can boot into rescue mode to repair grub and remove the old Ubuntu entries. (If you are using the newest one. Jaunty 9.04.)

To boot into recover mode, on the OS select screen, choose Ubuntu Recovery Mode. If you do not see this screen, reboot, and press esc when it prompts you to. Then you should get a menu that allows you to run fixes. Choose to fix the grub boot loader. If you need help, I will walk you through it.

---

### Post by zeroblackcat on 2009-07-17
i went to system > admin > 
but i cant find partion editor

and yes i have the newest verson of ubuntu

never mind i downloaded add and remove

---

### Post by ~sHyLoCk~ on 2009-07-17
> **zeroblackcat said:**
> i went to system > admin > 
but i cant find partion editor

and yes i have the newest verson of ubuntu

never mind i downloaded add and remove

Are you sure you installed using a "Live CD" or an alternate cd?

---

### Post by zeroblackcat on 2009-07-17
here is what i found in the editer

---

### Post by zeroblackcat on 2009-07-17
> **~sHyLoCk~ said:**
> Are you sure you installed using a "Live CD" or an alternate cd?

i installed it from a blank cd off the ubuntu site

---

### Post by NightwishFan on 2009-07-17
It seems you only have 1 Ubuntu installed. Do you have another hard drive?

---

### Post by zeroblackcat on 2009-07-17
> **NightwishFan said:**
> It seems you only have 1 Ubuntu installed. Do you have another hard drive?

yes i do have 2 hard drives

---

### Post by NightwishFan on 2009-07-17
Use the drop down in the top right to show me the other drive.

Edit: Actually, I have to go. Someone should sort you out allright. Good luck.

---

### Post by zeroblackcat on 2009-07-17
well thank you anyway

---

### Post by Elfy on 2009-07-17
I would guess that you are confusing the normal boot option and the recovery option, if it looks like this - more or less

title		Ubuntu 9.04, kernel 2.6.28-13-generic
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)

that is the case, the other drive you are showing is the swap drive.

If that is not the case - run these commands please from your normal boot - not the livecd

```
sudo fdisk -l
cat /boot/grub/menu.lst |grep title
```

Post the results please.

---

### Post by zeroblackcat on 2009-07-17
here is the result   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38162   306536233+  83  Linux
/dev/sda2           38163       38913     6032407+   5  Extended
/dev/sda5           38163       38913     6032376   82  Linux swap / Solaris

---

### Post by zeroblackcat on 2009-07-17
# title        Windows 95/98/NT/2000
# title        Linux
title        Ubuntu 9.04, kernel 2.6.28-13-generic
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
title        Ubuntu 9.04, kernel 2.6.28-11-generic
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
title        Ubuntu 9.04, memtest86+

---

### Post by Elfy on 2009-07-17
One linux installed, you have had a kernel update - from -11 to -13. Each kernel has two options - normal and recovery mode. All is normal here as long as it boots ok.

---

### Post by zeroblackcat on 2009-07-17
thank you man at lest i don't have 2 os's i am still new at these

---

### Post by Elfy on 2009-07-17
welcome :)

---

### Post by ~sHyLoCk~ on 2009-07-17
> **zeroblackcat said:**
> thank you man at lest i don't have 2 os's i am still new at these

If you want you can edit your grub 
sudo gedit /boot/grub/menu.lst and remove these entries:
```
title Ubuntu 9.04, kernel 2.6.28-11-generic
title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
```

---

