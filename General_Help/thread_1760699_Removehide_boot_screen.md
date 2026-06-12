---
title: "Remove/hide boot screen"
date: 2011-05-17
forum: General Help
---

### Post by PierreRobiquet on 2011-05-17
Is it possible to either remove or hide Plymouth during boot? I notice if I attempt to remove Plymouth with apt-get it attempts to remove the whole system with it, however I don't really like a boot screen and I would much rather have the typical kernel output. I'm probably a small minority of people who want it this way, but I like to see what is happening and if something is delaying my boot time.

---

### Post by WorMzy on 2011-05-17
Remove "splash" from your kernel line options. I'm not 100% sure how you do this on Grub2, but this guide should tell you: [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

---

### Post by PierreRobiquet on 2011-05-17
Wonderful, I have a final question. I have my resolution set in the GRUB configuration file with the GRUB_GFXMODE setting. Typically the splash will always revert to a lower resolution 800x600 I assume which I think is caused by Plymouth. Will the Kernel inherit this resolution or is there a way I can set the resolution without having to do crazy recompiling :D

Also, is it possible to get Tux at the top during boot above the kernel output.

[IMG]http://img7.imageshack.us/img7/7286/bootoptim.png[/IMG]

You know you can't resist :)

---

### Post by PierreRobiquet on 2011-05-17
Don't worry about it, I found out it requires to be compiled with Tux enabled. I don't think I'm nearly at the level I would be able to correctly configure a kernel :D

---

