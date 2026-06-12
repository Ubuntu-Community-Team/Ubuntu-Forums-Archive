---
title: "GDM Starts - No Login Box - Can't Login"
date: 2010-05-01
forum: General Help
---

### Post by itiswhatitis on 2010-05-01
I was helping a friend of mine upgrade his system from 9.10 to 10.04.  The upgrade went okay and he was able to use Lucid last night.

He has a dual boot with Windows 7, which was broken during the upgrade.  I was able to help him fix that, using the instructions at [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

So the Grub issue is not the problem.  However, after fixing his Grub install, he now cannot log into Ubuntu.

He selects the current kernel from the Grub menu, and the system starts up as expected.  The splash screen that generally has the login box on it comes up - but no login box with user names and prompt for password never displays.

He can press CTRL-ALT-F2 and login from a terminal, but has no option to log into GDM.

I've gone through the usual dpkg-reconfigure gdm and had him reboot.  Still no luck.

I have spent the last hour searching forums and google, but cannot find any situations like this. (probably using the wrong search text...)

What should I be looking for?

---

### Post by itiswhatitis on 2010-05-01
Apparently having your TV hooked up as a second monitor, but turned off, does not stop Ubuntu from seeing it.  

Login box was on the TV.

*sigh*

---

### Post by Noccy on 2010-06-04
> **itiswhatitis said:**
> Apparently having your TV hooked up as a second monitor, but turned off, does not stop Ubuntu from seeing it.

Tried that, but apparently keeping the secondary monitor unplugged however does. Plugging it and rebooting renders the same problem for me, but on the other screen with the first screen disabled.

I get the backdrop and I hear the logon sound, but I never get a login box. Any idea what this could be due to?

Had to install kdm to be able to log on to xfce, but that's not too exciting, especially considering it comes with a load of kde dependencies.

---

