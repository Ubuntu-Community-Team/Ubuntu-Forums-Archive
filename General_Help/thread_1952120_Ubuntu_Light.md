---
title: "Ubuntu Light"
date: 2012-04-03
forum: General Help
---

### Post by carmenin87 on 2012-04-03
I was searching for the various versions of Ubuntu Linux and got a hit for Ubuntu Light ( [http://www.canonical.com/engineering-services/oem-services/why-ubuntu/products](http://www.canonical.com/engineering-services/oem-services/why-ubuntu/products) ).

To get more details, it seems you need to send an email.  Does that mean that this version is not available for the general public?

Ubuntu has in some ways become bloatware and I am looking for a "light" version that has no extra apps installed, something that would run straight from RAM.  Maybe not quite as compact as Dam Small Linux or Puppy Linux, but still a small distro that I can customize from the ground up.

---

### Post by papibe on 2012-04-03
Hi carmenin87.

You have a couple of options: [Xubuntu]("http://xubuntu.org/") and [Lubuntu]("http://lubuntu.net/") (the lightest).

If you can't make your mind, we would gladly make suggestions if you share your hardware, and more details on what you are looking for.

Hope that helps.
Regards.

---

### Post by sffvba[e0rt on 2012-04-03
> Ubuntu Light, powered by Unity, is a simplified version of Ubuntu. It's perfect as a companion to Windows for a fast web experience or as a standalone operating system for use in mobile or embedded devices. Typical startup times are seven seconds on a device with a solid state disk drive (SSD). Boot times can extend up to 20 seconds on hard disk drive (HDD) machines. PC OEMs can get Ubuntu Light now. Contact Canonical for more details. You can also test Unity on Ubuntu 10.04 LTS now.

This is something aimed at OEM's and people that create embedded devices etc. (Typical application would be as a fast on alternative on a laptop rather than loading the full OS it will load a stripped down version for listening to music and/or surfing the web etc.)

As was posted above the lightest you can go with Ubuntu is to run Lubuntu (which uses the light LXDE).  


404

---

### Post by carmenin87 on 2012-04-03
> **not found said:**
> This is something aimed at OEM's and people that create embedded devices etc. (Typical application would be as a fast on alternative on a laptop rather than loading the full OS it will load a stripped down version for listening to music and/or surfing the web etc.)

As was posted above the lightest you can go with Ubuntu is to run Lubuntu (which uses the light LXDE).  


404

If Canonical doesn't provide a light version, is there a way for me to make my own "OEM" version.  What you describe above is pretty much what I need, a browser and the ability to serve the net.

I'd like to stay with Ubuntu then move to one of the offshoot distros that are based on Ubuntu.

---

### Post by kaldor on 2012-04-03
> **carmenin87 said:**
> If Canonical doesn't provide a light version, is there a way for me to make my own "OEM" version.  What you describe above is pretty much what I need, a browser and the ability to serve the net.

I'd like to stay with Ubuntu then move to one of the offshoot distros that are based on Ubuntu.

Try the Ubuntu [Minimal]("https://help.ubuntu.com/community/Installation/MinimalCD") CD. It's a text-based installer and gives you options when installing Ubuntu regarding packages.

---

### Post by QIII on 2012-04-03
For your DE you could use Enlightenment 17, which is lighter still than LXDE or Xfce.

---

### Post by carmenin87 on 2012-04-04
> **kaldor said:**
> Try the Ubuntu [Minimal]("https://help.ubuntu.com/community/Installation/MinimalCD") CD. It's a text-based installer and gives you options when installing Ubuntu regarding packages.

Thanks for the suggestions everyone.  I was following the tutorial over at [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) and it worked quite well.

There are a lot of things I'm not sure how to manually install and I'll probably start a new thread once I figure out exactly what it is I need help with.

But right off the bat, near the bottom of this tutorial, it says to run this line of code. 

sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic

I'm not exactly sure what this code does, but it obviously installs Firefox.  Is there another line of code that instead of installing Firefox, Chromium browser would be installed?

---

### Post by Cheesemill on 2012-04-04
Check out this script:
[http://andyduffell.com/techblog/?page_id=396](http://andyduffell.com/techblog/?page_id=396)

It asks questions about what you want installed on a minimal system and then goes ahead and installs it all for you.

---

### Post by mastablasta on 2012-04-04
> **carmenin87 said:**
>  
 
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic
 
I'm not exactly sure what this code does, but it obviously installs Firefox. Is there another line of code that instead of installing Firefox, Chromium browser would be installed?
 
replace firefox with chromium in the ocmmand,.
 
the ocmmand installs basic X (graphic interface), terminal (xterm), gdm, a menu, icewm (light window manager), synaptic (package manager) and gksu (i think this is graphical sudo). just the very basics i believe.

---

