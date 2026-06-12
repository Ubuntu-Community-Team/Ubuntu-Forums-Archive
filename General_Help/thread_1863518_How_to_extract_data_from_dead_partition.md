---
title: "How to extract data from dead partition"
date: 2011-10-17
forum: General Help
---

### Post by shaka89 on 2011-10-17
I'm new to ubuntu ..... and after installing the upgrade to 11.10 my laptop won't boot .... it has all the data in it. I'm looking at it from a live Fedora disk, is there a way to extract the data, currently getting a denied permission error. sorry for the lack of info, i'm really new to ubuntu, and I don't know if it was a good linux distro to choose. any help would be greatly appreciated, I have a lot of work I don't want to lose.

---

### Post by e79 on 2011-10-17
Could you try and boot with a Ubuntu LiveCD to see if this denied permission error occurs as well ? You should be able to simply hook any external disk (ntfs, ext3/4, fat etc) and copy over your important stuff.

---

### Post by Bmonsterboy on 2011-10-17
Are you using root privelages?

---

### Post by shaka89 on 2011-10-17
if it helps, the booting process stops after checking battery ... might have something to do with lightdm ... i just don't know what to do, i read i need it to run the following commands:
sudo apt-get purge lightdm
sudo apt-get install ubuntu-desktop
but how can i run them if I can't boot?

---

### Post by e79 on 2011-10-17
Remove the battery and try to boot with the Ubuntu LiveCD (plug your laptop to the wall obviously). Don't type any commands at this point, just try to get to a desktop with the live CD and see if you can access your data that is on the disk.

BTW is Ubuntu throwing any errors when booting ?

---

### Post by fixerdave on 2011-10-17
> **shaka89 said:**
> if it helps, the booting process stops after checking battery ... might have something to do with lightdm ... i just don't know what to do, i read i need it to run the following commands:
sudo apt-get purge lightdm
sudo apt-get install ubuntu-desktop
but how can i run them if I can't boot?

First, before anything else, right away, like now... boot to a liveCD and copy your files over.  You can use 'sudo' if you're comfortable on the command-line, or you can run 'gksudo nautilus' from a terminal and get the regular window file manager (except with super-user privileges).  If neither of these will let you copy your files, then you might need to take ownership of the files... ask if needed.

When you get to the point where the boot process stops, you can hit cntrl-alt-F1 to get to a console session.  After you login with your account, that's where you can type the above commands.  You could also use this console to copy your files, but there's no graphic interface... all command-line from there.

---

### Post by shaka89 on 2011-10-17
> **fixerdave said:**
> First, before anything else, right away, like now... boot to a liveCD and copy your files over.  You can use 'sudo' if you're comfortable on the command-line, or you can run 'gksudo nautilus' from a terminal and get the regular window file manager (except with super-user privileges).  If neither of these will let you copy your files, then you might need to take ownership of the files... ask if needed.

When you get to the point where the boot process stops, you can hit cntrl-alt-F1 to get to a console session.  After you login with your account, that's where you can type the above commands.  You could also use this console to copy your files, but there's no graphic interface... all command-line from there.

it says i don't have the necessary permissions.

---

### Post by fixerdave on 2011-10-17
When does it say you don't have the necessary permissions?  Did you boot to a liveCD, run Terminal, and type 'gksudo nautilus' to bring up a file manager that has super-user privileges?  Did copying your file from your home folder to a USB drive give this error?

Alternatively... did you try to boot the system as it is and then try the cntrl-alt-F1 key combo to get a console session?

Where are you at?

---

### Post by shaka89 on 2011-10-18
> **fixerdave said:**
> When does it say you don't have the necessary permissions?  Did you boot to a liveCD, run Terminal, and type 'gksudo nautilus' to bring up a file manager that has super-user privileges?  Did copying your file from your home folder to a USB drive give this error?

Alternatively... did you try to boot the system as it is and then try the cntrl-alt-F1 key combo to get a console session?

Where are you at?
Sorry for the delay.. i ended up loading the liveCD and "upgrading" from 11.10 to 11.10 .... i didn't know i could do that ... kept all my files. thank for the help tho guys

---

