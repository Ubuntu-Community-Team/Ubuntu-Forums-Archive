---
title: "Switching from Ubuntu 11.10 to Fedora 16"
date: 2011-11-22
forum: General Help
---

### Post by bruno9779 on 2011-11-22
I am switching from Ubuntu Oneiric to Fedora 16 and I need some help.

My current setup has /home on a separate partition and I need to know which files and folders I need to remove before reinstalling Fedora over it.

I have found several posts about this, but they all seem to be related to the Gnome Desktop, not to Unity.

Any help is appreciated

---

### Post by jjex22 on 2011-11-22
Hi there, obviously gotta add the obligatory back up now warning :)

But yes, as Ubuntu and fedora both use Gnome, I'd recommend creating a different user name for the fedora install so as not to confuse any settings.

In my experience it goes like this-
-on your current /home partition copy all the directories into a folder called data using the fedora live cd
-install Fedora with the /home partition in the / partition, using a different user name.
-Boot into fedora.
-mount you ubuntu /home partition at /mnt
-Copy the contents of /home to /mnt/ubuntu's-home-partition
-unmount the ubuntu home partition.
-move /home to something like /home_old - so that you now don't have a /home partition
-make the new /home directory
-mount the partition in /home
-edit /etc/fstab to mount at boot

then copy your personal data from the folders in data to the locations you want them, then delete the data folder.

The guide I use can be found [here]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") - it's a bit old but it still works!

Hope that helps!

---

