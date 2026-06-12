---
title: "Repartition"
date: 2012-08-02
forum: General Help
---

### Post by cavaughan on 2012-08-02
OK, I have a system that has 3 different OS's on it. When it boots up Grub (1.98 as I recall) asks whether I want to boot into either Jolicloud or Windows XP. I choose Windows XP. Then comes a Windows boot prompt asking whether I want to boot into Windows or Ubuntu. I choose Ubuntu. At this point I'm asked by Grub (1.99-2 as I recall) whether I want to boot into Ubuntu or Windows. I choose Ubuntu. 

WHat I'd like to do is get rid of everything but Ubuntu. However I'm afraid I'll make it impossible to boot into Ubuntu. Any recommendations?

---

### Post by irv on 2012-08-02
From the sounds of your boot process you have done a few installs in the past with all the boot prompts.

My advice to you would be to start with a clean install if all you want is Ubuntu.

First boot into Ubuntu and backup any data files you want. Then make a list of all the applications you have or want to install. Download the iso you want and burn a DVD or create a USB using Ubootin. 

Then just do a fresh install using the entire Hard Drive.
You can boot into the Live DVD or USB and test to make sure your hardware is working. If everything is OK just do the install.

---

### Post by Megaptera on 2012-08-02
Is there a chance you made a Wubi install of Ubuntu within your Windows XP? That range of boot options in that sequence is what I had when I had a dual-boot and a Wubi install within my Windows 7.
If it is Wubi, you can remove it from within Windows XP through add/remove programmes, then you can follow the advice from irv (above) and re-install Ubuntu.

---

### Post by cavaughan on 2012-08-02
Yeh, i've thought about that, but there are so many customized apps, etc. that I really would rather figure out a way to first set up the first grub to see Ubuntu and boot straight to it, if that is possible. Then use something like gparted to resize the partitions and make Ubuntu the only OS on there.

---

### Post by Dylan1473 on 2012-08-02
If I correctly remember how this works, it sounds like you literally have Ubuntu installed within Windows. You can't get rid of Windows without also getting rid of Ubuntu. However, you will most definitely be able to save the Ubuntu partition within Windows and recover many files and settings, and MAY even be able to transfer the Ubuntu partition within Windows wholly outside of Windows, THEN get rid of Windows, to run it normally. I'm going to edit this in a bit with some more info.

EDIT: Okay, I found what I was looking for. _[This]("https://help.ubuntu.com/community/MigrateWubi")_ is a guide to doing exactly what you're trying to do. Note that it's possible to dual boot Ubuntu AND Windows should you want to keep both.

---

### Post by irv on 2012-08-02
> **cavaughan said:**
> Yeh, i've thought about that, but there are so many customized apps, etc. that I really would rather figure out a way to first set up the first grub to see Ubuntu and boot straight to it, if that is possible. Then use something like gparted to resize the partitions and make Ubuntu the only OS on there.

There is a way to do this.
First backup all your data, things could go wrong and sometime they really do.
Using gparted delete the Windows partition and apply the changes. Remember you are going to loose all the data in Windows. Next resize the Ubuntu partition to use all but the swap partition.
Next boot with the live CD/DVD and fix the grub to see only the Ubuntu OS. reboot and hopefully it will have only the Ubuntu on it. If things don't go well, you will end up doing a fresh install.

---

### Post by Dylan1473 on 2012-08-02
@irv:

I could be wrong but I think he installed within Windows through Wubi. If that's true, I'm pretty sure doing what you described would result in Ubuntu actually being deleted with XP. There isn't a separate Ubuntu partition. He has to make a new partition and then transfer his Ubuntu install to there, I think.

---

### Post by irv on 2012-08-02
> **Dylan1473 said:**
> @irv:

I could be wrong but I think he installed within Windows through Wubi. If that's true, I'm pretty sure doing what you described would result in Ubuntu actually being deleted with XP. There isn't a separate Ubuntu partition. He has to make a new partition and then transfer his Ubuntu install to there, I think.

OK, Let me ask. Did you install the Wubi or did you install Ubuntu in it own partition? Dylan1473 is right. If it was Wubi install deleting Windows will delete Ubuntu. It sound like it was install both ways. Which one are you using? the Windows installed Ubuntu or the one on it's own partition. Maybe you should show us a screen shot of gparted before doing anything.

---

### Post by cavaughan on 2012-08-02
You guys are great!! The Wubi-move utility worked perfectly. Now it's all Ubuntu!!!! Thanks! Now I can use gparted and expand the HD.

---

### Post by irv on 2012-08-03
> **cavaughan said:**
> You guys are great!! The Wubi-move utility worked perfectly. Now it's all Ubuntu!!!! Thanks! Now I can use gparted and expand the HD.

Like we said, just be careful and backup your data. changing partitions in gparted can go wrong and we don't want you to loose your data. I myself have had good luck with doing this, but it sometimes goes wrong.

---

