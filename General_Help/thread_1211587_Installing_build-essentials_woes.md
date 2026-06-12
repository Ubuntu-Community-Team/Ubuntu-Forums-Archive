---
title: "Installing build-essentials woes"
date: 2009-07-12
forum: General Help
---

### Post by gerbilburp on 2009-07-12
Hello,

I'm having trouble installing build-essentials on 8.04 hardy ubuntu

Installed from unetbootin usb stick and have no access to internet only through windows dial up =/
Is it possible to install build essentials from that usb stick?

Build essentials is required for my wusb600n wireless
Any suggestions anything will help!

Thanks everyone.

---

### Post by CatKiller on 2009-07-12
I don't know about whatever image you're using on that drive (I've never used unetbootin) but the build-essential package is certainly included on the standard Desktop image. It may already be there.

EDIT: Included, not installed. From the normal live cd environment you can do a sudo apt-get install build-essential to install it. The same may be true of the environment you're in from your USB drive.

---

### Post by twright on 2009-07-12
> **CatKiller said:**
> I don't know about whatever image you're using on that drive (I've never used unetbootin) but the build-essential package is certainly included on the standard Desktop image. It may already be there.

EDIT: Included, not installed. From the normal live cd environment you can do a sudo apt-get install build-essential to install it. The same may be true of the environment you're in from your USB drive.
I am almost certain it is not (why on earth include but not install it when space is so tight?). If the suggestion does not work you can try using packages.ubuntu.com to download its components/dependences but as they are many this will take a very long time/lots of effort. If you have the option of an ethernet cable or an external adapter this would be a lot easier.

---

### Post by gerbilburp on 2009-07-12
thanks for the reply

1.  The unetbootin file for the usb stick is the ubuntu 8.04 iso from the site (i do not have the physical cd)

2.  How do i access the usb stick to install build essentials?

twright - I'm certain the build-essentials are on the disc but not sure exactly why its not part of the installation 
Unfortunately my only access to the internet is through windows dial up on the same machine (dual boot vista)

---

### Post by twright on 2009-07-12
> **gerbilburp said:**
> thanks for the reply

1.  The unetbootin file for the usb stick is the ubuntu 8.04 iso from the site (i do not have the physical cd)

2.  How do i access the usb stick to install build essentials?

twright - I'm certain the build-essentials are on the disc but not sure exactly why its not part of the installation 
Unfortunately my only access to the internet is through windows dial up on the same machine (dual boot vista)
If you copy the .iso onto your new install you can rightclick to mount it like a cd, that might make things easier. Next you can try opening nautilus as root be pressing alt+f2 and typing in nautilus, right click on where the iso is mounted and create a link which you can then move to /media/cdrom. With that done the mounted iso should look exactly like a cd to the system and you can use System->Administration->Software Sources to setup installing programs from the (fake) CD. Now "sudo apt-get install build-essential" should work - good luck :-)

---

### Post by gerbilburp on 2009-07-12
alrighty im off to try wish me luck

---

### Post by CatKiller on 2009-07-12
> **twright said:**
> (why on earth include but not install it when space is so tight?).

In case you need it to get on the Internet, perhaps? Space isn't that tight, and the compilers aren't that big when they're compressed. Most new users aren't going to need a suite of compilers installed, and those that do are probably going to be able to install them themselves. The users that **do** need build-essential installed in order to get on the Internet, but don't need compilers for any other purpose, and so aren't going to necessarily be able to install them themselves, come here :)

Your suggestion of mounting the ISO to use as a local repository is a good one and should be pretty painless for the OP.

---

### Post by gerbilburp on 2009-07-13
got this error

[sudo] password for sara:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

---

### Post by CatKiller on 2009-07-13
After you've added the repository, don't forget to hit Reload (in Synaptic) or use ```
sudo apt-get update
``` (on the command line) to refresh the list of available packages to include the packages that are available from the new repository.

---

