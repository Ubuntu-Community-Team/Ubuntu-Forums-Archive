---
title: "Minor Dual Boot/partition issue with karmic and win7"
date: 2010-03-14
forum: General Help
---

### Post by ho0ola on 2010-03-14
Hey partners` I got a minor issue.

       I know your gunna gimme guff for wanting to dual boot linux w/ windows,but its for game playing ease... 
       Basically im new to this whole partitioning/dualboot/Grub shenanigans and i ran into a problem. I had Karmic working fine, and got a copy of windows 7. The installation readme told me to setup a 15gb NTFS partition for win7. So I did. I installed win7 fine, and made it to the desktop. When i went to reboot, wanting to get back into karmic, I configured BIOS to boot from first hard disk. When computer rebooted it booted into windows7 w/o a boot options menu (which is what id like) AHHH!!!! So I stuck in the karmic live-cd and booted that way. I went into System-admin-disk utility to check stuff out. My partition for Karmic was there, but the 'bootable' tick was unchecked. So, I checked it, restarted and removed the live-cd. I config'd BIOS, and recieved 'No Operating System' (or something along those lines, sry its late) 
       I would simply reinstal Karmic, but there are a couple files I would like to grab off my Orginal Karmic partition, which i cannot access through live-cd (or can I)
      Any advice?? Its nothing serious i can always try to completely reboot it all, but for timesaving and data recovery reasons id rather not ;) 

Thanks, any ideas out there?

---

### Post by spiky001 on 2010-03-14
Hi i think the problem is you need to reinstall grub, have alook here
[http://ubuntuforums.org/showthread.php?t=1318757&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=1318757&highlight=reinstall+grub)

---

### Post by wilee-nilee on 2010-03-14
Step 11 on this wiki has several methods to reinstall grub2; if you were running grub2.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by oldfred on 2010-03-14
The boot flag (active partition) has to be on the windows boot partition. Windows uses it, linux does not, but some BIOS will not boot without a flag somewhere.

Windows is not aware of any other operating system so it always overwrites the MBR.

---

