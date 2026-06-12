---
title: "Grub fails to load &quot;Error 2&quot;"
date: 2009-08-16
forum: General Help
---

### Post by BPWCOT on 2009-08-16
Hello there,
I was trying to install the Suse Grub, and looks like something went wrong, my grub doesn't load the menu.lst, I used a live cd to root and setup where the stage1 exists, and it goes successful but when I restart now it says "Error 2", I tried to re-install Ubuntu so I can get a fixed Grub again or something, but when the Partioning manager comes up, it doesn't allow me to use a free space, I only have two options avaible, Guided using the whole disk or Manual using the whole disk.. any ideas?

P.S when I'm using the live cd, I can access any part of my Harddisk, and I have Vista installed as well.

---

### Post by quixote on 2009-08-18
I suspect the reason it's not seeing free space for an install is because the failed install makes it look like all the space is occupied.  

When the partitioning manager comes up, do you know which is your Vista partition?  I assume you want to leave that alone.

Once you're sure which is your Vista partition, and any other partitions you don't want to touch, use the Manual install option.  It says "whole disk," but don't worry.  You can choose which partitions to work with.

In Manual install, it'll list all the partitions.  Just make sure your Vista ( and others you want to keep) are NOT ticked for formatting, and they'll be okay.

For the messed up partitions, you may need to delete them (turns them into free space) before it will let you format them.  When the window pops up where you decide how big to make a given partition, there's also an option "mount point".  At least one partition has to be "/" (ie root, where the system goes).

If you have enough space, make two partitions, one /, and one /home.  That way you can reinstall a new version in /, without reformatting /home.  All your personal settings and data in /home are not affected. 

Hope this helps.

---

