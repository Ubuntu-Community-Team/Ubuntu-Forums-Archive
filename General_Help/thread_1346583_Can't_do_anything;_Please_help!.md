---
title: "Can't do anything; Please help!"
date: 2009-12-05
forum: General Help
---

### Post by WolfRage on 2009-12-05
I added the repo for ultimate edition, I was enjoying the user interface, some updates came down this morning, and now all is bad. 
Ok seriously this is what I have ubuntu boots and works it's way towards the login, but instead of getting the login I get four overlapping screens that are not readable. Which I assume are xserver looking for me to reconfigure it. I can not read anything and just want to get back to the terminal so that I can vi the repo from my sources list and then reconfigure my xserver package. DOes any one know how I can drop to a terminal. By the way <alt>+<ctrl>+F** does not seeem to work. I think I need to kill xserver some how.

---

### Post by othiena on 2009-12-05
Have you tried to boot in safe mode?

---

### Post by WolfRage on 2009-12-05
You mean recovery mode? Yes on all of my available kernels.

I am currently downloading another iso, on the vista machine (Gag) so that I can boot in and hopefully reset the xserver conf file.

---

### Post by othiena on 2009-12-05
If you have a alternet install cd you can use the option on it to rescue a broken system.

---

### Post by WolfRage on 2009-12-05
Actually used an alternate install CD to try and rescue, used the shell on the root drive, but it appears to be generating errors when I make commands. So any major commands like apt-get and dpkg do not seem to be working. Keep trying though thank you!

---

### Post by othiena on 2009-12-05
have you tried to edit the sources.list while booting from it?

---

### Post by WolfRage on 2009-12-05
Yes actually I did manage to edit the sources.list via vi and removed the repo from the list, but apt-get update and upgrade do not undue the upgrade. no files get installed or removed. Also DPKG-reconfigure yields errors and no apparent fix. About to but in using a iso so I can do more in depth fixes. Also hoping to at least recover my home directory and then I can just do a clean install.

---

### Post by WolfRage on 2009-12-05
I booted in using a boot-able ISO of Ubuntu 9.10. I am currently making a new backup of my home directory, in case I have to replace the OS. I have now edited the xll conf file but have not been able to test the settings.

---

