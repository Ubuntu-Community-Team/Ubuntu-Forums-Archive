---
title: "GRUB Error 17, please help, I haven't found any help so far."
date: 2009-10-19
forum: General Help
---

### Post by Zombii on 2009-10-19
I have searched, and searched, and... Well, you get the idea. I have read this thread:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

And every link in there is dead, and no other threads/posts/or articles have helped me. So, I did a dumbass thing, I was going to reformat my drive as NTFS so I could try out the Windows 7 Beta on my laptop and I missed a step and forgot to completely delete everything so now my GRUB and drive is ****** up. I have created a bootable usb drive with Xubuntu on it, and set boot priorities and everything correctly. However, it gives me a GRUB Error 17 when trying to boot from the HDD **AND FROM TRYING TO BOOT FROM AN EXTERNAL SOURCE.** Please help. My laptop is ruined if I can't fix this.:(


My laptop is an Acer Aspire One 1'st gen.

---

### Post by Giblet5 on 2009-10-19
How far did you go down the path of installing Win7?

Did you select the drive and get the "copying files" dialog?

If so, you may as well complete the Win7 install because you toasted the Ubuntu install. Now, you have Win7 halfway installed, Ubuntu overwritten, and a Grub menu that points off into the weeds.

Grub will still come up, but Error 17 is what you would get.

You don't have to "clean up" anything when doing an all-out install of Win7 or Ubuntu. The defaults will toast everything and use all available space.

The last thing Win7 will do is overwrite Grub.

---

### Post by Zombii on 2009-10-19
...
No. I'm a dumbass, when it comes to Linux. I uh... Accidentally only halfway formatted. My Xubuntu install is toasted, it no longer exists, it was nuked. But, the GRUB bootloader is still searching for it's files, which it can't find because I accidentally didn't uninstall GRUB and the HDD now has GRUB looking for it's files, which no longer exist. At least, this is the conclusion I've come to. I'm thinking of just buying a new HDD and putting it in.

---

### Post by mechro on 2009-10-19
> **Zombii said:**
> ...
No. I'm a dumbass, when it comes to Linux. I uh... Accidentally only halfway formatted. My Xubuntu install is toasted, it no longer exists, it was nuked. But, the GRUB bootloader is still searching for it's files, which it can't find because I accidentally didn't uninstall GRUB and the HDD now has GRUB looking for it's files, which no longer exist. At least, this is the conclusion I've come to. I'm thinking of just buying a new HDD and putting it in.

So you want to delete Grub? Once it's deleted what do you want to boot into?

---

### Post by Zombii on 2009-10-19
> **mechro said:**
> So you want to delete Grub? Once it's deleted what do you want to boot into?

One of my three bootable USB drives. Which contain XP, 7, and Xubuntu. Also, I don't want to delete it. I just want to be able to BOOT INTO **SOMETHING**. As it is now I can't boot from ANYTHING. Much less the HDD.

---

### Post by Giblet5 on 2009-10-19
> **Zombii said:**
> One of my three bootable USB drives. Which contain XP, 7, and Xubuntu. Also, I don't want to delete it. I just want to be able to BOOT INTO **SOMETHING**. As it is now I can't boot from ANYTHING. Much less the HDD.

Well, you may as well install something on that wiped out drive. You can't even edit the Grub config to use the USB drives until you do that much.

Finish a Windows install. You can always select what drive to boot from via the popup boot menu in your BIOS.

I can't help but think that you're doing a lot of easy things in really REALLY hard ways. Sure, it will make you strong, but it'll also make you really cranky. ;)

---

### Post by Zombii on 2009-10-19
I would install something, but I can't! That's the problem! I can't boot from a LiveCD, nor a USB drive with Xubuntu on it, nor an external HDD. GRUB WILL NOT LET ME BOOT INTO ANYTHING.

Here's how it goes:

Power on>F12>Boot Selection>USB>GRUB Loading stage1.5 GRUB loading, please wait... Error 17

---

### Post by mechro on 2009-10-19
Why can't you boot from a LiveCD? Have you tried? That might be sorted through a BIOS setting. Grub has nothing to do with booting from a CD.

---

### Post by linuxwl on 2009-10-19
You can boot  from a livecd ,find out root(hdx,x),then set up grub.

---

### Post by Giblet5 on 2009-10-19
> **mechro said:**
> Why can't you boot from a LiveCD? Have you tried? That might be sorted through a BIOS setting. Grub has nothing to do with booting from a CD.

I'm guessing he didn't actually try...

Further, I'm guessing that none of those USB drives has an MBR or an active partition.

---

### Post by K.Mandla on 2009-10-19
> **linuxwl said:**
> You can boot  from a livecd ,find out root(hdx,x),then set up grub.
Or even just boot to a live CD and possibly rescue your files, if nothing else.

---

### Post by PrePenguin on 2009-10-19
By the way with Acers tapping F11 while booting will enable windows rescue partition and repair your system to factory settings.. This is assuming you didnt delete the hidden restore partition.

---

