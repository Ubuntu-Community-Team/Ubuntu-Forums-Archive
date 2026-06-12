---
title: "help me to uninstall ubuntu from school pc"
date: 2010-09-14
forum: General Help
---

### Post by crack_stein on 2010-09-14
Ok. Today I installed ubuntu latest version on Dell Vostro 3300 which also runs windows xp. Now I want to uninstall ubuntu from it because wireless is not working. The problem is this is school pc and I have no access to hard disk partition to delete ubuntu. Someone from yahoo answers tell me to uninstall ubuntu from Add/Remove programs but there's no such 'ubuntu' application under Add/Remove programs.

How should I uninstall ubuntu from this situation. Any ideas?

---

### Post by DeMus on 2010-09-14
> **crack_stein said:**
> Ok. Today I installed ubuntu latest version on Dell Vostro 3300 which also runs windows xp. Now I want to uninstall ubuntu from it because wireless is not working. The problem is this is school pc and I have no access to hard disk partition to delete ubuntu. Someone from yahoo answers tell me to uninstall ubuntu from Add/Remove programs but there's no such 'ubuntu' application under Add/Remove programs.

How should I uninstall ubuntu from this situation. Any ideas?

How did you install it? Did you use Wubi or did you do a normal install?

---

### Post by howefield on 2010-09-14
If this is a school pc, isn't there a system administrator there who can help you out ?

---

### Post by snowpine on 2010-09-14
Stop what you are doing (before you make it worse) and ask your teacher for help.

There is no simple way to "uninstall" Ubuntu; you need to boot from a Live CD, delete the partition, resize the Windows partition, and then fix the Windows boot loader.

---

### Post by crack_stein on 2010-09-14
> **snowpine said:**
> Stop what you are doing (before you make it worse) and ask your teacher for help.

There is no simple way to "uninstall" Ubuntu; you need to boot from a Live CD, delete the partition, resize the Windows partition, and then fix the Windows boot loader.

I even deleted partition where ubuntu is installed from ubuntu live cd but ubuntu just can't be deleted in this case. If I hand it back to IT guy, he would at least screw me back. :D

---

### Post by crack_stein on 2010-09-14
> **DeMus said:**
> How did you install it? Did you use Wubi or did you do a normal install?

I mounted it on a dvd and booted from cd/dvd drive.

---

### Post by snowpine on 2010-09-14
> **crack_stein said:**
> I even deleted partition where ubuntu is installed from ubuntu live cd but ubuntu just can't be deleted in this case. If I hand it back to IT guy, he would at least screw me back. :D

He should; it is not your computer. :( Ask for help before you get in more trouble; you are in over your head. :)

---

### Post by ajgreeny on 2010-09-14
> **crack_stein said:**
> I even deleted partition where ubuntu is installed from ubuntu live cd but ubuntu just can't be deleted in this case. If I hand it back to IT guy, he would at least screw me back. :D
From this comment it sounds as if you have perhaps deleted the ubuntu partition but left yourself with grub on the MBR of the internal hard disk.  However, without the ubuntu partition, grub is useless, as all the config files for grub were there, and are now gone.

The way to get everything back where it should be, if I am correct in my supposition about grub, is to boot to a windows install CD, and choose to fix the MBR.

I think this will be a salutary lesson to you not to do things to school IT equipment that does not belong to you, particularly if you don't know exactly what you are doing, and what the consequences may be.

Bite the bullet and ask for help from the IT guy.  He may even be interested in what you were doing, and then investigate ubuntu for himself, if he does not know it already.

---

### Post by pricetech on 2010-09-14
Man up (Woman up) and admit what you've done.  The school probably has IT people who can fix it.  Then accept whatever disciplinary action they dole out.

Chalk it up as a learning experience.

---

### Post by raafaell on 2010-09-14
runnn runnn! :p

---

### Post by marshag63 on 2010-09-14
I guess you didn't know you can install Ubuntu to a USB flash drive while booted to the live CD.  I must admit, I had a similar experience when learning linux, but it was not with a school PC -- it was actually my mother's computer and I learned about partitions real quick :)

I'd get a flash drive and experiment on it if I were you.  If you make your USB install via the USB creator, you can have a persistent environment (changes stick - install more programs and they stay installed, etc), just make sure to make the storage area as big as possible via that option in the USB creator.  

If you use something like unetbootin, you have the equivalent of a live CD on a USB stick (you can try many, many distros out this way without wasting a CD).  

Here's a little fun homework - get the Ubuntu User Guide and have a look.  (Google)  You will also want to research how to troubleshoot wireless - first step is to figure out what wifi adapter is in the laptop.  You will make short work of this problem if you learn a little bit about the command line and a couple of the commands regarding networking.

Hope the school IT guys aren't excessively hard on you and let you have a laptop hereafter.  Let us know how it goes, okay.

MarshaG.

---

