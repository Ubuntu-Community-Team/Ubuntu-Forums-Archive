---
title: "Ubuntu 10.04 startup problems"
date: 2010-10-20
forum: General Help
---

### Post by Damascus Ventica on 2010-10-20
Hello, I am still new to Ubuntu and today when I started up my laptop and selected Ubuntu a black screen opened up saying:


GNU GRUB version 1.98-1ubuntu6
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>


Can somebody please help me?

---

### Post by Rubi1200 on 2010-10-21
Hi and welcome to the forums :)

Is this a regular install to the drive or via Wubi?

---

### Post by Damascus Ventica on 2010-10-21
Rgular install

---

### Post by Rubi1200 on 2010-10-21
If you have a LiveCD, boot the computer and post the results of the boot-script linked at the bottom of my post.

Please paste the text between the code tags (#) which can be generated from the menu when starting a new post.

Thanks.

---

### Post by Damascus Ventica on 2010-10-21
To be honest I'm just going to uninstall it and then reinstall it and hope that work Ubuntu 10.04 never really gave me any problems. Then I updated and crap got real.

---

### Post by jaddle on 2010-10-23
I'm seeing the same thing after an update a couple of days ago. There was a kernel upgrade in there, but I don't think that's the culprit, since the old kernel is still there and has the same problem. Probably the libc upgrade is to blame. I think I'll try downgrading to see if it does any good.

---

### Post by jaddle on 2010-10-23
Yup, that was the problem. Turns out there was already a new version of libc6, so I upgraded it and the problem was solved!

I don't know if I did the upgrade properly though - I booted to a live CD (older version of ubuntu - all I had handy!) downloaded the new deb and its dependencies, and then chrooted to my hard disk root partition, then did the 'dpkg -i libc6*deb'.

It didn't really install properly, complaining that the installed libc6 (i.e. the one on the live CD) wasn't managed by dpkg, and then there were a bunch of errors about creating devices in /dev. But it got far enough into the install that the reboot worked, so I could finish installing them in the real system.

Luckily, it didn't leave the computer in a worse state! Is there a better approach to take for installing packages to a system from a liveCD?

---

