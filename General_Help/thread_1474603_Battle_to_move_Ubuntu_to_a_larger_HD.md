---
title: "Battle to move Ubuntu to a larger HD"
date: 2010-05-06
forum: General Help
---

### Post by tkoco on 2010-05-06
I had my venerable Ubuntu machine chugging along and a box popped up announcing that I was running low on hard drive space. Ohh! Some quick trash cleanup and deletion of old unwanted files helped free enough space to complete my project.
So, a trip to the computer store and I had a brand new shiny hard drive. But I had to ponder how to move the working Ubuntu installation to this new drive.
Clonezilla? Did not like handling the EXT4 format. Kept on insisting that the EXT4 format was a corrupted NTFS format.
Oakey Doakey!
RSYNC? It copied the info ok, but the GRUB2 configuration was too cryptic to figure out. Maybe someone with more experience working with GRUB2 would write a tutorial on manually updating the configuration when you copy over the working installation to a new hard drive.

A search of moving Ubuntu turned up this gem:
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/]("http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/")

So, I recorded the package selection per the instructions and placed the text file in the home directory.
Next, I powered down the machine and swapped harddrives and rebooted the machine using a Ubuntu LiveCD. I proceeded with a new installation of the same release of Ubuntu. By doing this, I avoided dealing with GRUB2 and partitioning was straight-forward.
Once the installation was finished, I powered down and installed the old harddrive. I rebooted to the LiveCD. I copied the home directory from the old harddrive to the new harddrive. And then rebooted to the new harddrive. Once the desktop was up, I followed the rest of the instructions to complete the upgrade. Once the apt-get procedure finished and a reboot, I **almost** had the original installation. 

The "fly in the ointment"? the Xorg would not go back to the working resolution of 1280x1024. It insisted on going to 1024x768. Plus I have the Nvidia drivers on the old installation. So, a quick Nvidia activation helped, but still unable to get 1280x1024. Hummm!
Since both harddrives were still installed, I rebooted to the LiveCD and copied over the /etc/X11 directory from old to new installations. A reboot to the new harddrive, and a quick configuration adjustment, the new Ubuntu installation was just like the old one! The old hardrive was removed.

Success!

---

