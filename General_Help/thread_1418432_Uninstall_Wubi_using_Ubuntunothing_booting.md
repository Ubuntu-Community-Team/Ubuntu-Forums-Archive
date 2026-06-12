---
title: "Uninstall Wubi using Ubuntu/nothing booting"
date: 2010-02-28
forum: General Help
---

### Post by don_leno on 2010-02-28
Okay. First off, I installed Ubuntu so that i could learn more about it, I'm hardly a code monkey or good at technicalities. Second, the computer i'm having trouble with is not connected to the internet, but if it must be I can figure that out.

Here we go. I recently installed Ubuntu 9.10 onto my old computer using Wubi. I installed it, rebooted it, and walked away so it booted straight into XP. From there, I changed the default OS to Ubuntu from XP. I rebooted again and it worked, so I shut the computer off(it was late). Today, when i woke up, i turned on the computer and it took me to a GRUB page where i could choose these options:
Ubuntu, Linux 2.6.31-14 generic
Ubuntu, Linux 2.6.31-14 generic(recovery mode)
Ubuntu (on /dev/sda1)
Windows NT/2000/XP (on /dev/sda2)

The first option, sporadically, either goes to Ubuntu login or goes to a command prompt with the message "usb_id[426]: unable to access '/devices/pci0000:00/0000:00:0b.0/usb2/2-8" , then brings me to Ubuntu login after a few minutes.
The second option goes through a large command line then ends at "error probing SMB1"
Upon choosing the last 2 options, i get "error: unknown command 'drivemap'


id like to just copy everything from my old computer onto an external and move it to my new one, but Ubuntu doesnt recognize my external, a 500 GB WD My Book with nothing on it. 

I have the restore disks for XP, but id like to get some files off the computer first.

Is there any way to get XP to work again? To uninstall Ubuntu USING Ubuntu? To get the external to register? Any help is welcome.

---

### Post by garvinrick4 on 2010-02-28
You must have a Live CD that will get you into your xp install and delete the WUBI in C: drive right next to Users. Take your install CD to start with and put in machine then restart
select go into ubuntu without changing. When it comes to a desktop (GUI) look under drop down menu in upper left for Places click on it, hopefully your installs are there to fix. Report back here of what is going on.

---

### Post by don_leno on 2010-02-28
I found a way to make an XP live disk, but it needs the XP install disk, which i dont have. A friend is getting me one thursday, once i get XP to work i should be fine on my own. Thank you for the suggestion.

---

