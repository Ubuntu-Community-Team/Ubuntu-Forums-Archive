---
title: "Graphical Installation ad other issue's"
date: 2011-07-26
forum: General Help
---

### Post by nankura on 2011-07-26
hey guys

ok i have abit of a gripe with ubuntu and past experiences with 10.04 and 10.10.

At the moment im using fedora 15 because its been simple and quick for me, graphic drivers are a simple 
yum [COLOR=#c20cb9]**install**[/COLOR] akmod-nvidia xorg-x11-drv-nvidia-libs command

a tool called AutoPlus takes care of everything codec wise, programs, necessitys and the software center 

Now im not trying to promote fedora Btw

Im considering trying 11.04 but im wondering if the following things have changed

1. Is there a way to edit unity, like the gnome-extension thing will it work with unity as well as gnome 3

2. Is there a way yet to automatically install nvidia drivers, my biggest annoyance with ubuntu was the constant need to stop X servers and do command lines/updates/etc just to install a driver, yes theres the recommended driver, but its always a "tested" version , if you wanted the latest version, it was annoying to get it

3. Is there a tool that does your codecs, or does restricted extras take care of everything

these are all situations that have caused my massive headaches in the past. ubuntu claimed to be the simple distro, easy to switch to from windows but it was a pain, i found fedora much easier

---

### Post by Frogs Hair on 2011-07-26
Gnome 3 is PPA at the moment  and Unity runs on top of Gnome 2.xx . It may be worth waiting for 11.10 which will have Unity on top of Gnome 3. 

I have used the drivers jocky to install the Nvidia current driver and have never had to stop the Xserver. If you download from the Nvidia site you will still have this problem unless you use a PPA . Can notice a difference between Nvidia current and the one from the site ?  Drivers should  only  be  updated if they include  changes that make your hardware work better . [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")


Codecs are installed as needed by the user from the software center . The reason they are restricted is because they are not legal to use in all areas .

---

### Post by nankura on 2011-07-26
i dont understand that "restricted" or "illegal but free you can still use software"

If its illegal why are we still using it

im not having a go. i just dont understand it

---

### Post by JC Cheloven on 2011-07-26
> **nankura said:**
> i dont understand that "restricted" or "illegal but free you can still use software"

If its illegal why are we still using it

im not having a go. i just dont understand it

It's legal for you (the end user) to download and install for your own use that stuff. 
It isn't legal for a company (like Canonical in this case) to ship with their products that suff.
Installing ubuntu-restricted-extras from the medibuntu repository will give you such codecs and stuff.

I'd suggest you to try Linux Mint. It's based on Ubuntu but includes all the stuff.

Hope to have made it clearer.

---

### Post by nankura on 2011-07-27
Thankyou for the help guys, but your answers lead me to more questions :P


This was all very helpful and it seems alot of headaches from the past have solutions now with 11.04 and mint 11 sounds very interesting

But my gripe with mint 11 in the past was the fact that it had so much come with it, it made it very bloated, now i have a very high grade pc

but mint 11 was back when i had my ATi graphics card ( ive got an nvidia now and ive had less issues and i havnt tested mint on it )

i recieved alot of problems with games

With fedora 15 so far gamings been a dream. smooth and nice

and alot of people said my ATi card had issues with mint 10's and ubuntu 10.04's kernal along with my AMD processor

So im wondering what kernel mint 11's using and if theyve fixed there bloated issues

---

