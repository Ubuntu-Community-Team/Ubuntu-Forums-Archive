---
title: "Have Ubuntu and Linux Mint use same programs"
date: 2012-02-23
forum: General Help
---

### Post by hanzj on 2012-02-23
We plan on installing Ubuntu Ocelot and Linux Mint 12 side by side. Is it possible for them to use the same instances of programs (for example, Gimp, VLC, Chrome)? 

Also, what must we do during installation to optimize this side-by-side installation? By the way, we plan on keeping the Windows 7 installation.

---

### Post by agillator on 2012-02-23
Yes, it is possible although whether it is worth the effort depends on why you want to do it. Be advised I speak from theory here, it has been a long time since I have actually done this. In other words, BACK UP YOUR DATA BEFORE DOING ANYTHING, but then you will do that anyway, WON'T YOU! 

The secret is how you partition your disk. Manually create a partition for the shared programs/files. When you install the systems, select the installation partitions manually so you can be sure the installation program does not format that partition. After each installation edit /etc/fstab if necessary so that partition will be automatically mounted at system boot. Be sure you put that mount point in your system path so the programs can be found. Remove them, if necessary, from the new installation (you might just change the names at first in case it doesn't work) so they can only be found in your special partition. You may/will probably have to do some further tweaking since the programs will not be where the system expects them to be, but you should be able to solve those problems with by putting links where the system expects them if nothing else. It might be possible to have /usr/local/bin, for example, shared (i.e. in its own partition) which would make things easier, but be cautious. I don't know if a new installation would overwrite programs on that or not and I am not in a position to test it. If the program is one that is not installed by the installation program there should be no problem. Of course configuration files will also be a problem. If the program uses them they will also need to be in a shared partition.

I trust this helps. However, I question why you would want to do this. For programs installed by the distribution installation it seems like a lot of trouble for little return. Disk space is relatively cheap these days so . . . . Perhaps all you need to do is share configuration files? Of course for programs you manually install sharing may make sense. It sounds as if you are going to be doing multiple machines, so take one machine and experiment. See if it is worth the effort.

---

### Post by HeroOfCanton on 2012-02-23
Have to agree with agillator, unless you are really pressed for disk space it's probably not worth the extra setup work. If you're looking to keep files and settings consistent a shared directory for just those things would probably be a lot easier that actually sharing the software installs.

---

### Post by mastablasta on 2012-02-23
why not simply install for example Ubuntu, add the mint desktop interface and their specific programmes (for example mint backup tools, software manager...) and that's it. then on loging in select the user interface you like and you the programmes you like.
 
why use a dual boot?

---

