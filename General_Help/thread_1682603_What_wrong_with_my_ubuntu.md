---
title: "What wrong with my ubuntu?"
date: 2011-02-06
forum: General Help
---

### Post by crownclown on 2011-02-06
[IMG]http://i377.photobucket.com/albums/oo218/noob_crown/DSC00093.jpg

---

### Post by Smudge123 on 2011-02-06
Try booting by the cd or ISO if your using a program like virtual box and then I guess you will have to re-install.

---

### Post by coffeecat on 2011-02-06
@crownclown, there are many reasons why you might be dropping to a busybox shell, but you'll have to give us more information. Are you booting from a hard drive install, from a live CD or from a live USB? What version of Ubuntu? What hardware are you using? If you are booting from a hard drive install, was this working OK before, or have you just installed? Did you do any updates before this happened?

---

### Post by crownclown on 2011-02-07
> **coffeecat said:**
> @crownclown, there are many reasons why you might be dropping to a busybox shell, but you'll have to give us more information. Are you booting from a hard drive install, from a live CD or from a live USB? What version of Ubuntu? What hardware are you using? If you are booting from a hard drive install, was this working OK before, or have you just installed? Did you do any updates before this happened?


im very sorry forgot to insert the situation..
well i just come back home then, after i start my laptop it direct show the error...
so i ask my brother , he said that after i went out, my house got electricity block. so the electric went off..

i was running in hard drive not boot cd..
so i went blur and dont know what to do...
and i'm using ubuntu 10.10.....

why is this happend ? and what's the error does mean ?
sorry, if i have many question about this..
well im start to like to use this  ubuntu...

---

### Post by coffeecat on 2011-02-07
If your laptop was running without a battery and the mains power went off then the machine would have had a hard shutdown and that might have caused filesystem corruption. Although I'm not quite clear from your post whether that was what happened. If you think the machine may have had its power supply interrupted suddenly, then it might be worth doing a filesystem check and repair.

Boot from a live CD or live USB. Choose 'try Ubuntu' so that you are booted into the live desktop. Open Disk Utility from the System > Administration menu. Highlight the internal drive on the left and then your Ubuntu partition under 'Volumes'. If you are not sure which it is, it will be the ext4 one. Now click on 'Check File System'. If there is more than one ext4 partition, check each one.

If this does not solve the problem, I don't have any further ideas.

---

### Post by crownclown on 2011-02-08
> **coffeecat said:**
> If your laptop was running without a battery and the mains power went off then the machine would have had a hard shutdown and that might have caused filesystem corruption. Although I'm not quite clear from your post whether that was what happened. If you think the machine may have had its power supply interrupted suddenly, then it might be worth doing a filesystem check and repair.

Boot from a live CD or live USB. Choose 'try Ubuntu' so that you are booted into the live desktop. Open Disk Utility from the System > Administration menu. Highlight the internal drive on the left and then your Ubuntu partition under 'Volumes'. If you are not sure which it is, it will be the ext4 one. Now click on 'Check File System'. If there is more than one ext4 partition, check each one.

If this does not solve the problem, I don't have any further ideas.


yes that my problem...so i need to run live with the cd first ?
hurmm i will try it...

---

