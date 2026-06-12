---
title: "Live CD Frankensin"
date: 2009-11-19
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2009-11-19
As you might have guessed I'm in the process of making a custom live cd... I just realized that the some of the packages I'm installing aren't going to start at boot and I've never changed the startup apps in a command line. So where would I find the startup config? I looked in /root for a .config folder but nothing there. Also I assume the default manager is going to be metacity and would like to make it compiz (nvidia drivers installed). Would the best method be adding compiz --replace to that startup when I find it?

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
Man... I've got this thing almost perfect. The Live CD I produced is now a Live DVD for it is 1.9GB, which actually surprises me because I installed a LOT of stuff. I have a DVD+RW for this project though. Anyway... still having trouble getting things to run on boot. I even made a .config file in root... well... I actually copied most of my home folder over to the root of the disk and still none of the apps I want start at boot nor do my configurations apply. I also have some trouble with modules. I got most of the ones I want to not use out using modprobe -r and started the nvidia drivers using nvidia-active or something like that (which killed any chance of using virtualbox to test) and when checking lsmod everything I set is coming up except ndiswrapper. With the nvidia drivers working though I'm still figuring out how to go about setting up ccsm and emerald. I need to tell the CD to start compiz at boot along with emerald. I copied things like fstab and blacklist.conf over to get some desired effects and that worked out quite nicely to get my drives mounted where I'd like and unneeded modules blacklisted. Also when I sudo -i I get my Killmandline prompt... guess I need to find where the cd copies configs for ubuntu@ubuntu user from or make a root log in for the disk make it default. If anyone has any insight on what to look into or where in the configs to look to make these changes I would appreciate them much.

---

### Post by Sin@Sin-Sacrifice on 2009-11-21
Welp... I got her done finally by realizing making my settings system wide defaults was the way to go. Felt like a moron when I figured it out. The DVD comes out at a whopping 1348MB and takes about 8 min to get to the desktop too but now I have a live cd to rule them all. It surprises me to see that, aside from loading programs, the install icon on the desktop, and the modules for my sensors not loading, I absolutely can't tell the difference between the live cd and my desktop. The performance is spectacular.

---

