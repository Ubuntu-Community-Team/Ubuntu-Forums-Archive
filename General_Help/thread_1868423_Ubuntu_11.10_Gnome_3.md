---
title: "Ubuntu 11.10 Gnome 3"
date: 2011-10-24
forum: General Help
---

### Post by PsyclonJohn on 2011-10-24
Hey,

This is just something I was wondering about since I couldn't find much information about. I been looking around on what Gnome 3 looks like because I have the GUI set to Gnome 3 and mine looks a lot different. It looks almost like Gnome 2, like for example... In Gnome 3, it's supposed to say 'Activities' in the menu, and mine still says 'Applications'. Is this supposed to be like this in Ubuntu or is this some kind of weird bug?

--
John

---

### Post by collisionystm on 2011-10-24
> **PsyclonJohn said:**
> Hey,

This is just something I was wondering about since I couldn't find much information about. I been looking around on what Gnome 3 looks like because I have the GUI set to Gnome 3 and mine looks a lot different. It looks almost like Gnome 2, like for example... In Gnome 3, it's supposed to say 'Activities' in the menu, and mine still says 'Applications'. Is this supposed to be like this in Ubuntu or is this some kind of weird bug?

--
John

Sounds like a bug.

Did you install gnome-shell

---

### Post by crokett on 2011-10-24
Your Gnome-3 may be in failback-mode.  If your video card doesn't support 3D, (or gnome 3 doesn't think it does) this will happen.  Log out, then when you log in click the * next to your username before you enter your password.  You should have options for Gnome and Gnome-failback.  Make sure 'Gnome' is selected.

---

### Post by Gatemaze on 2011-10-24
If you have installed the gnome-shell then make sure you select gnome on logon and not gnome-failback if i recall well it is called...

---

### Post by kurt18947 on 2011-10-24
You might try to find "additional drivers" and see if there's anything listed. It may be under user name -> system settings.  Your video system may require proprietary drivers to display Unity or Gnome Shell.  You could check that the package "gnome-shell" is installed. I don't know if it's installed by default in 11.10 or not.   That's the package that enables Gnome 3 (shell).

---

### Post by PsyclonJohn on 2011-10-25
Hey, thanks for the replies!

It seems like the issue is only happening on the main administrator account. All other accounts created work fine with Gnome 3, so it sounds like a bug to me too.

---

