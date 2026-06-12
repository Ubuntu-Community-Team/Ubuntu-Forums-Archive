---
title: "Ubuntu Server Question"
date: 2011-04-08
forum: General Help
---

### Post by sister_mabel on 2011-04-08
Hello everybody,

I was just wondering if it was possible to run Ubuntu Server Edition from an External Hard Drive?

Thanks,

---

### Post by earthpigg on 2011-04-08
of course it is.

when going through the instillation process, make sure you specify were to install grub (on the external hard disk, not your computer's internal). 

if you want to be super safe when installing, you can always unplug your computer's internal hard drive.

---

### Post by seawolf167 on 2011-04-08
Sure, just select a different device when going through the installation prompts. As said above, if you install GRUB on your "main" hard drive and sometime later remove/reformat/etc. it, you'll have to reinstall GRUB

---

### Post by sister_mabel on 2011-04-08
Ah, thats good then.

Can the external hard drive act as the server?

[Im a noob when it comes to servers; i just dont get them. Sorry]

---

### Post by lisati on 2011-04-08
> **sister_mabel said:**
> Ah, thats good then.

Can the external hard drive act as the server?

[Im a noob when it comes to servers; i just dont get them. Sorry]
Sort of, but not really. If you choose to install the server edition onto the external hard drive, the computer you plug it into will act as the server, which happens to get its OS, software and other data off the hard drive.

---

### Post by earthpigg on 2011-04-08
> **sister_mabel said:**
> Ah, thats good then.

Can the external hard drive act as the server?

[Im a noob when it comes to servers; i just dont get them. Sorry]

*at literally the exact same time* as you are otherwise using the computer?

yes, you need to look into virtual machine solutions for that - or you need to look into running server services **on top of** the desktop operating system.

Option 1)

Use regular ubuntu, and install server software on top of it. ("sudo tasksel install lamp-server" would get you started)

Option 2)

Use ubuntu server, and install desktop software on top of it. ("sudo apt-get install ubuntu-desktop" would get you started)

Option 3)

Use any desktop operating system you want (including windows), and install ubuntu server in a virtual machine. this may sacrifice the stability of the server side of things, and it may make things more difficult (you may need to play with windows firewall, for example), but you do get to essentially run ubuntu server as a windows application.

Option 4) 

Combination of 1 or 2, and 3.


there are probably 50 other approaches to this problem. those are 4 off the top of my head.

if you just want to get started and mitigate the learning curve, then you would ideally have a dedicated computer to play with and learn on.

---

