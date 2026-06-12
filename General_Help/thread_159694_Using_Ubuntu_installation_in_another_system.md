---
title: "Using Ubuntu installation in another system"
date: 2006-04-13
forum: General Help
---

### Post by KenSentMe on 2006-04-13
I have a bedian web/file/mailserver running right now at home, but i want to start over from scratch and i want to use ubuntu breezy. Now i don't want the current server to go down for more than 15 minutes, until the new install is ready. So i was wondering if it's possible to install ubuntu on a harddisk in another machine, configure it and then swap disks when the new server config is ready for use.

On the machine that i will be using for configuring i have a ati radeon and a creative soundcard etc. When i install ubuntu on that system and then place the hd in my server machine (without both cards) does ubuntu goes looking for those cards and give me an error, or are both not used because i installed ubuntu with the server option (no graphical interface etc.)?

---

### Post by az on 2006-04-13
[QUOTE=KenSentMe]I have a bedian web/file/mailserver running right now at home, but i want to start over from scratch and i want to use ubuntu breezy. Now i don't want the current server to go down for more than 15 minutes, until the new install is ready. So i was wondering if it's possible to install ubuntu on a harddisk in another machine, configure it and then swap disks when the new server config is ready for use..[/QUOTE]

Sure.  Just make sure you have the correct grub menuélist and fstab in terms of the hard disk device names.

What about just dist-upgrading your debian box to ubuntu?


[QUOTE=KenSentMe]

On the machine that i will be using for configuring i have a ati radeon and a creative soundcard etc. When i install ubuntu on that system and then place the hd in my server machine (without both cards) does ubuntu goes looking for those cards and give me an error, or are both not used because i installed ubuntu with the server option (no graphical interface etc.)?[/QUOTE]

If you do not install X, you won't notice a thing.  If you do install X, it won't start;  it will look for the hardware that is not there.  You would boot into the console, but it would not make your box crash or anything.

The sound card is just another module that is loaded on boot by hotplug.  Don't worry.

---

### Post by KenSentMe on 2006-04-13
[QUOTE=azz]Sure.  Just make sure you have the correct grub menuélist and fstab in terms of the hard disk device names.

What about just dist-upgrading your debian box to ubuntu?

[/quote]

I want to start over again, and start with a clean install. The system is a bit messy and not everything works how i want it to. And i have a new hd.

> 
If you do not install X, you won't notice a thing.  If you do install X, it won't start;  it will look for the hardware that is not there.  You would boot into the console, but it would not make your box crash or anything.

The sound card is just another module that is loaded on boot by hotplug.  Don't worry.

And there's no difference in an install on a pentium 4 and a amd athlon xp?

---

### Post by az on 2006-04-13
[QUOTE=KenSentMe]
And there's no difference in an install on a pentium 4 and a amd athlon xp?[/QUOTE]
The default kernel is a 386.  You can install the 686 kernel on your surrogate box, but just don't boot it.  You have to change kernels yourself, it is not autodetected currently.

---

