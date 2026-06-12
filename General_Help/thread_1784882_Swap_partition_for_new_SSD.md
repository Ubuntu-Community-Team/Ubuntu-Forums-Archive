---
title: "Swap partition for new SSD?"
date: 2011-06-17
forum: General Help
---

### Post by sylvainrb on 2011-06-17
Hello,

I am getting a new SSD for my laptop and I have been researching the different tweaks for an SSD. I still have a question regarding the swap partition: is it better to not have one for an SSD? (I have 4GB of RAM...)

If I don't, how would I specify it during the installation process for 10.04?

Thanks!

---

### Post by pqwoerituytrueiwoq on 2011-06-17
since a ssd has a write limit i would not use a swap partition on it
sadly most laptops do not have a slot for a second hard drive like a desktop does so using the ssd as a boot disk is not very piratical for a laptop
i would put /tmp onto a ram disk (fstab:* tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0* ) and use a ram disk for firefox's profile
also 10.04 does not have trim support out of the box if the ssd is your only drive you will need that or the speed will fall on the drive
i recommend you back up the ssd once a month and keep the receipt in a safe place (not that special place you will will never find it) so if it fails you can use the warranty

i have a ssd in my desktop i put / on my ssd and /home, /var, and /tmp on my standard hdd to prevent wearing the ssd out

---

### Post by sylvainrb on 2011-06-17
Ok so is there an option/tick mark that I can check so it does not create a swap partition during the installation? Or does it have to be done manually? (I am not really comfortable with partitions...)

If I keep the swap partition, I could just disable hibernate... 4GB of RAM should suffice for the rest.

Thank for the TRIM tip, but I am planning on updating the kernel after installing 10.04.

I am also keeping the old hard drive as an external drive. It won't be plugged in 24/7 but I'll have it handy nearby. I want to try the SDD for the read speed and will have all my projects on the old drive.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
i always to the advanced mode but i just make my partitions with gparted before opening the installer
so much easier that way
how much does the ssd hold?

---

### Post by sylvainrb on 2011-06-17
It's a 64GB SSD

---

### Post by pqwoerituytrueiwoq on 2011-06-17
i would give / about 12gb
and then put a extended partition next to it with a /home partition inside it
then edit the fstab file after installing and make /tmp a ram disk

---

### Post by sylvainrb on 2011-06-17
Ok I will try that once I get it. One question though: how do I specify which block / and /home go to? Does it happen with gparted or during the install process in the advanced mode?

Thanks for the help and prompt replies!

---

### Post by pqwoerituytrueiwoq on 2011-06-18
durring install
go to advanced and set the mount point

---

