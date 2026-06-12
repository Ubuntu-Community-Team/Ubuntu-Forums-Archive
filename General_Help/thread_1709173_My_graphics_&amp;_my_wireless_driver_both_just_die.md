---
title: "My graphics &amp; my wireless driver both just died after an update"
date: 2011-03-17
forum: General Help
---

### Post by LibmasterLib on 2011-03-17
I installed a routine update through the update manager this morning and when the next time I turned my laptop on neither my graphics driver or my wirless driver were working.

When I turned my laptop on I got an error saying:

**Ubuntu is running in low graphics mode**
The following error was encountered.  You may need to update your configuration to solve this.
[I](EE) NVIDIA:  Failed to load the NVIDIA Kernel module.  Please check your
(EE)  systems Kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available[/I]

After clicking ok to this message I get another with a series of options about how to resolve this ranging from troubleshoot to restart to run in low graphics just once.
Once I open the session my wireless won't load up, but I can still connect to ethernet.

Has anyone else run into this problem & resolved it?
Does anyone know what I should do to fix this?

I'm using a 3 year old HP pavilion laptop running Lucid Lynx.  I'm not sure if this problem is related to the update, but it's the only thing that happened out of the ordinary before I ran into this problem.  Unfortunately I cannot remember what was included in the update.

---

### Post by JC Cheloven on 2011-03-17
Have you tried to reinstall the drivers from system-administration-hardware drivers?

If yes (and didn't fix it), please try these comands in a terminal (one at a time):
```
sudo apt-get update
sudo dpkg-reconfigure -a
```
Reboot and see if it helped.

If not please post the output of those commands at a terminal
```
lspci
sudo lsmod
```
Perhaps we can figure out what module is missing, and probing it manually, or whatever.

---

### Post by LibmasterLib on 2011-03-17
Thanks for the help JC!
a quick reinstall of my graphics driver resolved both issues.

---

### Post by iamchichi on 2011-05-23
> **LibmasterLib said:**
> Thanks for the help JC!
a quick reinstall of my graphics driver resolved both issues.

Hi. How do you re-install your graphics driver?

---

### Post by linuxinstalledfromhdd on 2011-05-23
In gnome you would click System >> Administration >> Additional Drivers.

In unity you can just do a search for Additional Drivers I believe.

---

