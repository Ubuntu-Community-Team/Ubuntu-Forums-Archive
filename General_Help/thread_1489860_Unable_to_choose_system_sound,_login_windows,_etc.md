---
title: "Unable to choose system sound, login windows, etc"
date: 2010-05-21
forum: General Help
---

### Post by kaotik2003 on 2010-05-21
I am having a problem with my Lucid L.

I installed Mac4Lin and when trying to change login window, grub window, splash screen, or even system sounds, I simply don't have the option.

I go to the application like System-Preferences-Sounds and simply don't have the option to change the system sounds, all I have is 5 tabs without that option.

Login widows is the same thing, I can only choose if I want a login sound or not and that's all, I can't even choose to make auto login since it does not give a user as option.

I tryed also with art manager, but the "Install" button is greyed, and startupmanager does not give me any of those options too.

Is this normal, is it a bug, does any one know a solution???

---

### Post by charlie cat on 2010-05-21
You may want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=1300133")...
So far as I can tell, they've removed the login sound dialog from 9.10+.
As for configuring GRUB type stuff, I'd think you'd just go into the "Appearance" tab in Startup-Manager.

---

### Post by kaotik2003 on 2010-05-21
> **charlie cat said:**
> You may want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=1300133")...
So far as I can tell, they've removed the login sound dialog from 9.10+.
As for configuring GRUB type stuff, I'd think you'd just go into the "Appearance" tab in Startup-Manager.

Thanks for the reply.

Regarding the Startup-Manager that is the issue. I don't have am Appearance tab, it simply isn't there

---

### Post by charlie cat on 2010-05-21
Is startup-manager up to date?  You should install any updates in update-manager or possibly re-install it in Synaptic.  Of course, this might be another package they've stolen features from in 10.04, although it says I have the latest version and the appearance tab's still there.
Note: I am running a 32-bit computer, so the packages might be slightly different.

---

### Post by charlie cat on 2010-05-22
If this is a clean install (from LiveCD) or you have manually updated to GRUB2, this problem may be due to Lucid using GRUB2.  Take a look at [this article]("https://help.ubuntu.com/community/Grub2"), specifically under the title ["Splash Images and Theming"]("https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming").  If this is not the case (still on original GRUB), look at [this article ]("https://help.ubuntu.com/community/GrubHowto")under[ "Boot splash images"]("https://help.ubuntu.com/community/GrubHowto#Boot%20splash%20images").

---

### Post by kaotik2003 on 2010-05-23
In fact I use Grub2 and following your link I was able to change the Grub splash image. Thanks

Startup manager is also uptodate and no other tabs present.

However I still can't change GDM Login window. I am not sure if this is 64 bit related or not since my brother running 32 bits does not have the same issue.

---

### Post by charlie cat on 2010-05-23
Check out [this thread.]("http://ubuntuforums.org/showthread.php?t=1490784")
I think ubuntu-tweak may be exactly what you're looking for.  Follow the link in post 4; you can't get it just from Synaptic.

---

