---
title: "run windows in ubuntu 8.04"
date: 2009-09-17
forum: General Help
---

### Post by gishaust on 2009-09-17
Hi

I need to run windows for IE 7 and 8 for web development. But I only run Ubuntu. What I want to do is create a virtual machine so that I start the 
virtual machine occasionally to do some testing. How am I able to use kvm to do this? I need it to be able to run inside the desktop so that I can see
the Ubuntu desktop and the windows desktop.


gishaust

---

### Post by quixote on 2009-09-18
I use Virtualbox for exactly the application you mention.  You can install it using Synaptic.  Just be sure to get the Sun version and not virtualbox-ose, because the latter has rather deficient usb support.  

Is there a reason you want to use kvm?  I don't know anything about it.

---

### Post by skatinjj on 2009-09-18
> **gishaust said:**
> Hi

I need to run windows for IE 7 and 8 for web development. But I only run Ubuntu. What I want to do is create a virtual machine so that I start the 
virtual machine occasionally to do some testing. How am I able to use kvm to do this? I need it to be able to run inside the desktop so that I can see
the Ubuntu desktop and the windows desktop.


gishaust

[URL="http://www.howtoforge.com/installing-windows-xp-as-a-kvm-guest-on-ubuntu-8.10-desktop"]found this for you
[/URL]

---

### Post by gdonwallace on 2009-09-18
I do this all the time at work.  I have win XP installed in virtual box so that I can run IE 7 / 8.

Also, you can try Wine.  You don't have to install windows; wine runs a windows enviro so that you can install windows programs into it.  Search for winehq to look through their forum list of all the programs that they have tested and that work successfully.

---

### Post by Darkwing-Duck on 2009-09-22
I agree with Virtual Box. If you need some help with Virtual Box you can find some good information here.

[http://gwos.org/udsf/doku.php/software:virtualbox](http://gwos.org/udsf/doku.php/software:virtualbox)

Let us know if you need more help.

---

### Post by GoldenSun on 2009-09-22
install some non ose virtual box and dl a tiny xp.  Then you're set.  I think you can also install ie7 or 8 in wine.

---

