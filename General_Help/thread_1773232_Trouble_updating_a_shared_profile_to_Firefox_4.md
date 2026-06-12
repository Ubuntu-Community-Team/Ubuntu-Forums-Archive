---
title: "Trouble updating a shared profile to Firefox 4"
date: 2011-06-01
forum: General Help
---

### Post by zorblek on 2011-06-01
I dual-boot Windows XP and Ubuntu Maverick. I share my Firefox profile between both operating systems. When I upgraded to Firefox 4 on Windows, a bunch of my extensions didn't work, and since Firefox 4 is pretty different, I decided to just start from scratch with a new profile. That worked well, and I now have a setup that works on Windows. However, I'm having problems on Ubuntu. I upgraded to Firefox 4 using the Firefox Stable Channel PPA. Firefox 4 won't run at all with the old profile. I downloaded the new standalone Mozilla profile manager for Linux and used that to create a new profile using the same folder as my new profile on Windows, However, when Firefox starts, it acts like I have a completely blank profile, with none of my bookmarks or extensions from the new profile.

What's going on here? Is it no longer possible to share Firefox profiles? I'm confused, and I'd really appreciate any guidance.

---

### Post by lovinglinux on 2011-06-01
It could be a problem with permissions, caused by AppArmor.

Where are you saving the profile? If you are saving on a NTFS shared partition, try to create a new profile on Ubuntu, but don't start Firefox. Copy the contents of the Windows profile into the new Ubuntu profile folder. Start Firefox and test if it works. If yes, then you will know the problem is not in the profile configuration or extensions, but in the location you are saving it.

You can then delete the Ubuntu profile contents, redirect the profile location to the original shared partition and look into the AppArmor configuration, to disable the Firefox profile.

---

### Post by zorblek on 2011-06-01
Actually, I just discovered the problem: my profiles.ini file had somehow gotten screwed up. I think the profilemanager app messed it up somehow; I'm not sure exactly what happened. Anyway, I fixed the profile entry by hand and it worked.

Thanks for the suggestion, though, I really appreciate it!

---

### Post by lovinglinux on 2011-06-01
You are welcome.

---

