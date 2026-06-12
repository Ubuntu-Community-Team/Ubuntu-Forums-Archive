---
title: "how to uninstall??"
date: 2006-05-11
forum: General Help
---

### Post by Gaia on 2006-05-11
Hi,

How do i uninstall Ubuntu from my drive??

Thanks.

---

### Post by Ramses de Norre on 2006-05-11
Reformat the partition into whatever other file system you like.

What did you dislike about ubuntu?

---

### Post by morbid_bean on 2006-05-11
Uninstall linux!...whats wrong?

---

### Post by Hoffmann on 2006-05-11
[QUOTE=Gaia]Hi,

How do i uninstall Ubuntu from my drive??

Thanks.[/QUOTE]

Are you sure you want to uninstall your Ubuntu partition? What's wrong?

---

### Post by s_h_a_d_o_w_s on 2006-05-11
Put whatever OS in your cd drive, reboot, enter BIOS settings, choose ''CDROM'' as first boot device. Save and exit.  

PS. Ubuntu rocks, so you really shouldn't uninstall it.

---

### Post by s_h_a_d_o_w_s on 2006-05-11
Yeah, why are you uninstalling? UBUNTU RULES. MS is full of bugs, viruses and unstability.

---

### Post by Gaia on 2006-05-11
Lol. Calm down all now, I'm going to be putting it on another drive by itself :P.

Well see the thing is i have files handled by windows on the drive as well. I have 2 disks one with Windows on it, and one with 2 partitions, one for files from Windows and the other with Ubuntu installed on it. I just want to know the easiest way to remove the Ubuntu partion without deleting the whole drive.

---

### Post by halitech on 2006-05-11
Does windows see your ubuntu partition? if so, just right click and format it. will still have the boot loader installed but if you are reinstalling on another drive, shouldn't be too much of a problem.

---

### Post by s_h_a_d_o_w_s on 2006-05-11
Try looking around in the BIOS page seetings. To get there -> Boot up, at first text, press ''DELETE'', and look around. Don't forget to not save if you are unsure of your setting.

---

### Post by Gaia on 2006-05-15
Hey, i uninstalled Ubuntu by using Windows and deleting the partition but the bootloader is still in the boot sector. Now when i try to boot it says GRUB Error, error 17.

How can i remove Ubuntu from the MBR?

---

### Post by Slim Odds on 2006-05-15
[http://support.microsoft.com/kb/q69013/](http://support.microsoft.com/kb/q69013/)

---

### Post by markitect on 2006-05-15
Installing Ubuntu on your new drive will fix grub for you, 
alternatively if you boot off your windows CD go to the recovery council and type fixmbr and it will return it to just booting windows

---

### Post by rhiannonthewolf on 2006-05-15
and for the more challenging noobs, how do i uninstall it when its a stand alone on my hard drive?  no windows partition, and windows cant see the drive that it is on.  (installed it solo on a drive, want to ditch that and dual boot, which was the original plan before i messed it up)

---

### Post by joehill on 2006-05-15
Isn't the easiest way just to use a live CD (either Ubuntu or Knoppix or otherwise) and use qtparted or gparted from there?  That's what I would do.  Of course, that doesn't touch GRUB or mbr, but reinstalling takes care of that.

---

### Post by Gaia on 2006-05-15
I don't have a Windows XP Install disk, is there any way that if i use the Ubuntu Live CD (which i'm using now because my computer won't boot ) to fix the mbr?

---

