---
title: "Will Ubuntu still work if I get rid of Grub?"
date: 2010-04-17
forum: General Help
---

### Post by cufflink87 on 2010-04-17
I have 2 internal hard drives, one runs windows and the other runs Ubuntu. I was wondering if I really needed Grub since I can choose which hard drive to boot from in the bios.

If you don't know off the top of you head, its ok. I can find out, but it would take an hour or more. Thank you

---

### Post by scouser73 on 2010-04-17
No.

---

### Post by howefield on 2010-04-17
Yes, you will still need Grub.

You can install it to various places if you don't like where you have it at the moment, but you can't not have it, (or at least some other form of bootloader).

The Bios may know which disk to boot from, but if there is nothing on the disk to say what to load....

---

### Post by cufflink87 on 2010-04-17
Thank you very much! If it weren't for you guys, I would've figure it out the hard way

---

### Post by elliotn on 2010-04-17
> **scouser73 said:**
> No.

yes its posible, i use to do that, when u have hardrives and each setup on a separate one u can choose on the bios which to load, except maybe (not sure) if grub is written in the windows drive then ur gona need it to boot ubuntu

---

### Post by cufflink87 on 2010-04-17
> **elliotn said:**
> yes its posible, i use to do that, when u have hardrives and each setup on a separate one u can choose on the bios which to load, except maybe (not sure) if grub is written in the windows drive then ur gona need it to boot ubuntu

So it will still work if i get rid of grub?

---

### Post by howefield on 2010-04-17
> **elliotn said:**
> yes its posible, i use to do that,

So, you have Windows on one drive and Ubuntu on the other but no grub or alternative bootloader.

In your world, how do you boot Ubuntu ?

---

### Post by elliotn on 2010-04-17
if i were u i would disconnet the drive that have windows and install grub on a drive that have ubuntu. Then grub will only have ubuntu and windows bootloader will have only windows. Then by choosing which drive to booth it would go to that os

---

### Post by d3v1150m471c on 2010-04-17
Why would you want to remove the grub?

---

### Post by mcduck on 2010-04-17
> **elliotn said:**
> yes its posible, i use to do that, when u have hardrives and each setup on a separate one u can choose on the bios which to load, except maybe (not sure) if grub is written in the windows drive then ur gona need it to boot ubuntu

No, that's not true.

If you want, you can choose to install Grub on the Linux drive instead of on the MBR of the first hard drive you boot from, but you will definitely need Grub (or some other bootloader) to load the Linux kernel into RAM and start it.

Just like Windows can't boot without it's bootloader (ntldr or winload.exe depending on the Windows version).

---

### Post by scouser73 on 2010-04-17
> **elliotn said:**
> yes its posible, i use to do that, when u have hardrives and each setup on a separate one u can choose on the bios which to load, except maybe (not sure) if grub is written in the windows drive then ur gona need it to boot ubuntu

Shows how much I know, lol,  I assumed it wouldn't work once grub was removed.

---

### Post by jocko on 2010-04-17
> **scouser73 said:**
> Shows how much I know, lol,  I assumed it wouldn't work once grub was removed.
It won't. A boot loader is ALWAYS needed, no matter which OS you use.

---

### Post by egalvan on 2010-04-17
> **jocko said:**
> It won't. A boot loader is ALWAYS needed, no matter which OS you use.

To amplify a bit...

Microsoft's boot loader isn't visible because it assumes...

one user
booting one OS
on one machine

so no need to have the boot loader operation showing anywhere.

Linux boot loader assumes...

nothing


it does not know how many users
it does not know how many OS's
it does not know how many machines...

so it's operation is totally open, so one can CHOOSE.

Choice, it's what's for Linux!



Seriously, the first question you need to ask...

WHY do you want to remove GRUB?

---

