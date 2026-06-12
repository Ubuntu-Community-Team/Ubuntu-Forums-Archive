---
title: "Stupidity with my video driver. Help"
date: 2009-10-18
forum: General Help
---

### Post by dcates1 on 2009-10-18
When looking thru  the add and remove I found the ati binary x.org driver and check marked it( very stupid as it applied it after down loading). Now when I boot I have a black screen with lines across the top and no gui.

As I really have this computer set up the way i want it I really would not like to have to reload. 

What command can I invoke at the command line (from the recovery mode kernel) that will let me revert to the default drivers in Ubuntu.I'm not very good at the command line, but I can cut and paste with the best of them.

Any help would really be appreciated.

System is
GateWay Amd Quad Core
8 Gig ram
Ati onboard video
750Gig hard drive
dual boot
Windows vista:(
Ubuntu 9.04 32bit:P
PAE server kernel

---

### Post by mike555 on 2009-10-18
if you can I suggest getting "envyNG " and running it ......... I think there is a way to get it without x running -not sure

---

### Post by philinux on 2009-10-18
> **dcates1 said:**
> When looking thru  the add and remove I found the ati binary x.org driver and check marked it( very stupid as it applied it after down loading). Now when I boot I have a black screen with lines across the top and no gui.

As I really have this computer set up the way i want it I really would not like to have to reload. 

What command can I invoke at the command line (from the recovery mode kernel) that will let me revert to the default drivers in Ubuntu.I'm not very good at the command line, but I can cut and paste with the best of them.

Any help would really be appreciated.

System is
GateWay Amd Quad Core
8 Gig ram
Ati onboard video
750Gig hard drive
dual boot
Windows vista:(
Ubuntu 9.04 32bit:P
PAE server kernel

No need to reinstall.

Boot up and press esc at grub. Use the down arrow key to select recovery mode. When you hit the recovery menu choose xfix. When its done choose resume normal boot.

---

### Post by dcates1 on 2009-10-19
Many thanks.
I'll give this a try when i get home tonite.

---

### Post by dcates1 on 2009-10-20
When I get to my recovery menu "xfix" is not an option.

 I can get to the root command line or I can run the live cd but I don't know how to revert to the default video driver.

Still looking for some help please.

---

### Post by dcates1 on 2009-10-21
bump:)

---

### Post by akakingess on 2009-10-21
I believe 'xfix' is the command to enter into the command line once you get to it within recovery mode. Get into recovery mode and choose to open a terminal or something that will give you a command line. When you get there, type in " xfix " and that should fix your x.org file. Also, if it doesn't work with just xfix you may need to do sudo xfix.

---

