---
title: "Something strange happened!"
date: 2010-04-09
forum: General Help
---

### Post by astro4travel on 2010-04-09
I recently replaced my C: drive with Window's XP on it and did a reinstall. My Ubuntu Karmic was still on the second hard drive. Now I have been trying to boot with a live CD, as my grub2 was overwritten by lovely Windows. I can hear the Ubuntu startup music logo, but I can't get a display. My monitor button turns yellow and I just hear things running and I have to force shut down with the 'ole button. I tried a Knoppix cd and it booted fine with display. Not sure what is going on. Any help would sure be appreciated. Thanks in advance. Michael

---

### Post by howefield on 2010-04-09
Are you using the same Live CD as you used for your Ubuntu install ? If it is a different edition, it might just be having issues with your hardware.

---

### Post by astro4travel on 2010-04-09
Yes it was the same CD. I'm going to give it another go now. The funny thing about it I also have a copy of Ubuntu 9.04 LTS and it also responded the same way.

---

### Post by lisati on 2010-04-09
> **astro4travel said:**
> Yes it was the same CD. I'm going to give it another go now. The funny thing about it I also have a copy of Ubuntu **9.04 LTS** and it also responded the same way.

Typo? :confused: Do you mean 10.04? 9.04 wasn't LTS

---

### Post by astro4travel on 2010-04-09
Yes, sorry. Senior moment!:confused:

---

### Post by howefield on 2010-04-09
So it isn't the same edition ?

You have Karmic installed on the hard disk, but are trying to boot with a 10.04 pre release CD ?

Try booting with a Karmic CD, you know that works.

---

### Post by astro4travel on 2010-04-10
No,
Much confusion abounds! I was running Ubuntu 9.10 version. That dvd does not work. I'm going to try and make a new dvd, and try running that. I will keep everyone posted as that is how we all learn. Thank all of you so far for your support. This is a great community! Michael

---

### Post by astro4travel on 2010-04-12
I burned new CD and the symptoms are the same. I can hear it starting (by the sound of the introductory sound byte) but the monitor is still black with the button yellow instead of green. Now, by pushing F5 or others I'm able to get to terminal. Is there any command I could use to jump start the Xorg file or some other command I could use? I tried Startx but it basically tells me that it is running already. thanks.

---

### Post by astro4travel on 2010-04-12
To add a little more clarity, Ubuntu starts up then shuts the monitor off. It is still running in the backround. When I go to bash, the monitor turns back on. I am running a ATI-9600 All-In-Wonder video card.

---

### Post by astro4travel on 2010-04-16
Hmmm,
May try and update the drivers for the ATI card.
The latest update on this mess is as follows: I did manage to get grub2 back and went to load my old installation of Ubuntu Karmic. Same deal, monitor would shut off and it still would be running in the backround. So, what I did next is this. I installed (with alternative install disk) The beta2 of 10.4. I did this so I could maby see the files on the old Karmic installation and maby transfer them over. Well, I went to Disk Manager and loaded it and just the window appeared but now drives! So I really can't see any other drives on my computer. Unless I find a fix for this, I will uninstall the beta2 and reinstall 9.10 and maby transfer over the settings and files from the old installation. Thats where I am now.

---

### Post by astro4travel on 2010-04-19
The latest update on this mess is as follows: I did manage to get grub2 back and went to load my old installation of Ubuntu Karmic. Same deal, monitor would shut off and it still would be running in the backround. So, what I did next is this. I installed (with alternative install disk) The beta2 of 10.4. I did this so I could maby see the files on the old Karmic installation and maby transfer them over. Well, I went to Disk Manager and loaded it and just the window appeared but now drives! So I really couldn't see any other drives on my computer. Unless I find a fix for this, I will uninstall the beta2 and reinstall 9.10 and maby transfer over the settings and files from the old installation. Thats where I am now.
 Michael

---

### Post by astro4travel on 2010-04-19
The latest update on this mess is as follows: I did manage to get grub2 back and went to load my old installation of Ubuntu Karmic. Same deal, monitor would shut off and it still would be running in the backround. So, what I did next is this. I installed (with alternative install disk) The beta2 of 10.4. I did this so I could maby see the files on the old Karmic installation and maby transfer them over. Well, I went to Disk Manager and loaded it and just the window appeared but now drives! So I really can't see any other drives on my computer. Unless I find a fix for this, I will uninstall the beta2 and reinstall 9.10 and maby transfer over the settings and files from the old installation. Thats where I am now.

---

### Post by astro4travel on 2010-05-12
Finally found the problem. It was a hardware issue with the VGA connector on the monitor. Fixed that and I am now back in business. Thanks for all of the help.

---

