---
title: "Login Manager"
date: 2006-04-18
forum: General Help
---

### Post by sinfreealex on 2006-04-18
I've searched throught the forums and have found no posts that help with my problem.

I resetup xorg to add two resolutions that my monitor supports.  I know they are supported because both resolutions 1024x768 worked in Winblows.  I hate 1024x768 on my 17" monitor.  Everything is way too big.  I have the drivers installed for my Ati Radeon 9600 Pro installed and working fine.  Now, everytime I reboot I have to "startx".  I liked gdm, which I was using before.

I tried > sudo /etc/init.d/gdm
as suggested in another post, but it did not help.

Also tried to use a backup xorg.config from a few days ago, which also did not work.  

Please help.

BTW, I've been through 5 distros to get to this one and I'm going to stick here for good.  Thanks to the Ubuntu team for making such a great distro.

---

### Post by jamesdodd on 2006-04-18
you need to check whether startx is being loaded upon boot

you might need some sort of boot manager application (really not sure what I have cos I'm on windows machine at the moment, but a bit of googling and apt-get etc will sort that for you...)

---

### Post by sinfreealex on 2006-04-18
[QUOTE=jamesdodd]you need to check whether startx is being loaded upon boot

you might need some sort of boot manager application (really not sure what I have cos I'm on windows machine at the moment, but a bit of googling and apt-get etc will sort that for you...)[/QUOTE]

OK, I grabbed 'bum'.  'bum showed 'gdm' in it's list and as inactive, which makes sense since I had to use startx to get into the gui.  I logged out of the session.  Once back at the prompt I proceeded to reinstall Gnome and then 'gdm' just to make sure.  Sure enough, once I restarted, everything was back to normal.  I hope this helps someone else on here.

Have a good one.

---

