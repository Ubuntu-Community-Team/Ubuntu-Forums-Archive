---
title: "Virtualbox - unable to create allocate disk space."
date: 2009-10-31
forum: General Help
---

### Post by ww711 on 2009-10-31
Currently using KK9.10 - installed VirtualBox OSE. When I go through the steps to create a virtual machine, when I either try to create a either a dynamic or fixed hdd, the dialogue window shows 0% and even after leaving the laptop for hours, it still remains at 0%...any ideas on what could be causing this? Even creating a 5 gig dynamic or fixed hdd size, it doesn't seem to be doing anything...

---

### Post by akand074 on 2009-10-31
I don't quite understand the problem. Are you saying that after going through the entire set up to create a new hdd that it won't create it?

---

### Post by ww711 on 2009-11-01
Yeah, that's' right. I'm using the VirtualBox OSE 3.0.8 that was from the ubuntu software centre. Though i've not tried to install the newer version 3.1.0 yet.

---

### Post by akand074 on 2009-11-01
Very odd, completely remove the one you got from the ubuntu software centre, its the OSE (the open source edition), which is not as good as the closed source edition. 

Download it from:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You shouldn't have any problems. If you have a separate storage partition I would recommend you switch the default location for your virtual box files to that partition because it can eventually take up quite a bit of space on your EXT3 or EXT4 ubuntu partition.

---

### Post by ww711 on 2009-11-03
> **akand074 said:**
> Very odd, completely remove the one you got from the ubuntu software centre, its the OSE (the open source edition), which is not as good as the closed source edition. 

Download it from:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You shouldn't have any problems. If you have a separate storage partition I would recommend you switch the default location for your virtual box files to that partition because it can eventually take up quite a bit of space on your EXT3 or EXT4 ubuntu partition.

Yeah, I un-installed the OSE version and installed the latest deb pkg on my system, it still does the same thin. The progress bar stays at 0% but from doing a 'top' to check the processes there seems to be activity  it's creating something. Even going afk about 2-3hrs on return it still 'doing something'...the hdd size i'm creating is 5 gig.

I would really like to try and get this virtualbox to create a hdd so i can install another OS!

---

### Post by bbeatle on 2009-11-08
Same Problem but if you start Virtualbox with root privileges it seems to be working

---

### Post by ww711 on 2009-11-08
I added myself to the vbox users group and it started to work and was able to provision a virtual machine.

---

