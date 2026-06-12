---
title: "Grub problems?"
date: 2010-10-22
forum: General Help
---

### Post by goplayer on 2010-10-22
Hello all,
 
I am a new convert to Ubuntu and I love it. I have installed Ubuntu on an external USB drive using my home computer running windows XP Pro. I did this so that I can actually take the drive with me and use it at work. Everything worked fine until yesterday when I was using the drive at work and did an update--work computer runs Vista. When I went home I plugged the drive into my computer and I got the Grub> prompt. 
I am not sure why this happened I think it may have to do with the update--I am not quite sure why though. Is this something to be expected everytime I update Ubuntu using another computer than the installation one?
If this happens how can I boot? I am completely ignorant when it comes to GRUB and am still learning linux and any insight is greatly appreciated.
 
PS. the Ubuntu version installed is 10.04 LTS.

---

### Post by goplayer on 2010-10-23
I managed to boot finally but I had to first boot from disk and then edit grub.cfg file to change root = (hd0,1) --it was set by grub-update to root = (hd1,1). I looked in all the files used during grub-update to see where this can be set but did not find anything. Should I set root=(hd0,1) in the custom script to be used in the future?

---

### Post by drs305 on 2010-10-23
With the USB drive attached boot to your USB Ubuntu installation. Then check to see which drive/partition is mounted with the "mount" command. For demonstration purposes, I'll assume it is mounted on sdb1.

From the USB-running Ubuntu, run the following:
```
sudo grub-install /dev/sd**b**
```
That should rewrite Grub to the sdb MBR and sdb1 /boot/grub.

Reboot with the USB disconnected. Do you have Ubuntu installed on your main system's drive? **If so**, boot again to Ubuntu and run:
```
sudo grub-install /dev/sd**a**
```
This should now write Grub to the sda MBR and /boot/grub files.
**If not**, leave it alone (don't install grub to sda) and booting Windows.

Set the hard drive's BIOS boot the USB drive first. Now if the USB drive is connected at boot it will boot to the USB Ubuntu. If it is not connected, it will boot to sda's Ubuntu (if installed) or Windows if it's not.

---

