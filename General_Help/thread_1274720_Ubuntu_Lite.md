---
title: "Ubuntu Lite"
date: 2009-09-24
forum: General Help
---

### Post by foremannz on 2009-09-24
Is there an option in Ubuntu to install the bare essentials to do things like browse the internet, manage files, and preview pictures.  It seems that when I install Ubuntu, I have to also install openoffice, fspot, gimp, a whole suite of games, and lord knows what else!

---

### Post by Riaku on 2009-09-24
Why don't you just install normal Ubuntu 9.04?

---

### Post by Simian Man on 2009-09-24
Not really.  Most distros give you an option for what software you want to install, but Ubuntu gives you basically 2 options:

 - The LiveCD which, as you said, installs a bunch of crap
 - The mini.iso cd which installs just the base system from which you install everything else with apt - and I mean everything it comes with no X server or anything.

---

### Post by foremannz on 2009-09-24
The LiveCD certainly sounds more appealing than the no X server!!!

---

### Post by BAMF1501 on 2009-09-24
UBuntu alone i find lite due to only being 700 mb i mean thats great way better than sh*tty windows 3 gig :popcorn:

---

### Post by DeMus on 2009-09-24
> **BAMF1501 said:**
> UBuntu alone i find lite due to only being 700 mb i mean thats great way better than sh*tty windows 3 gig :popcorn:

I agree, but how about Suse, Fedora, Mandrake? They also fill up a complete DVD.

---

### Post by credobyte on 2009-09-24
[Ubuntu Minimal CD image]("https://help.ubuntu.com/community/Installation/MinimalCD") and [tutorial on how to set everything up]("http://disambiguation.wordpress.com/2008/08/17/a-minimal-ubuntu-install-the-basics/") ;)

> **DeMus said:**
> I agree, but how about Suse, Fedora, Mandrake? They also fill up a complete DVD.

You can choose, what to install and what not ( I hope Ubuntu will have that feature in the next few versions ).

---

### Post by Sean Moran on 2009-09-25
> **foremannz said:**
> The LiveCD certainly sounds more appealing than the no X server!!!

If you are willing to do a little work from the terminal with your running installation, it is possible to customise a 'Lite' version of the LIve 699Mb Ubuntu-9.04-desktop.iso and remove the games and OpenOffice, and I suppose GIMP also.

I have been messing around with both Xubuntu and Ubuntu for these past five weeks now, and have removed gnome-games and OpenOffice (but not GIMP as yet) but decided that the system is probably close to perfect at 699MB and so decided to keep things as close to standard as possible.

However it can be customiised and 'Litened' in many ways.  Off the shelf,  Xubuntu also takes up only 617Mb in .iso.  It uses AbiWord rather than OpenOffice, as far as I remember.  Thunar rather than Nautilus, MousePad rather than gEdit.  It's 'lite' from the start!  

So there's another possible option.  Use standard Xubuntu rather than Ubuntu.

Alternately, perhaps use Synaptic Package Manager to remove what you don't want after install?  I have come to understand that the losses of some customising techniques outweigh the gains, and no matter what I have tried, each new CD I burn still costs the same from the shop, even if I put less on it, so it might be simpler just to install the standard and then use Synaptic to remove the applications that you do not use., unless you like to tweak things, as I do.
 Best of luck in finding a cure for chronic curiosity if you do 9-).

You willl need to **apt-get install squashfs-tools** if not already installed on your system.
It is a very small and speedy download.

Summarily, withiin a clean working directory with at least 4GB of space: 
1. create two new subdirectories: IN and OUT (any name and lowercase is fine but this it for clarity)

2. mount the standard .iso image to IN and copy the 24 odd Mb of running-gear to OUT. 

3. unsquash IN/casper/filesystem.squashfs to a third subdirectory eg. PRO 
(squashfs-tools will create the dir and will fail gracefully if it already exists, so do ensure that it doesn't.)

4. chroot PRO and then from the terminal add or remove packages using apt-get or aptitude. 

5. clean up the PRO filesystem and exit from the chroot session.

6. squashfs the PRO filesystem to OUT/casper/filesystem.squashfs

7. make a new .iso image from the filesystem and CD running-gear in OUT.

It's around a half hour job from mounting the .iso to burning a custom CD once you've practiced it a few hundred times.  I found the details on these steps right around here on the Ubuntu forum, but I can't remember the URL fot the excellent instructions that were given.  

There is also a need to transfer the /etc/hosts and etc/resolv.conf to the PRO filesystem before you chroot into it if you want to download packages to add, so RSVP if this looks like the sort of thing you are wanting to achieve, and I willl double-check on the command-line syntax before posting things that might be erroneous if I am relying on memory alone.

In the end, this way of customising the standard probably does take a long time to achieve not very much that couldn't be done fairly sweetly from Synaptic after installing, but that's taken me five weeks to discover, so I hope this might save some extra time on your part.

---o0o---

A related thread in the Cafe forum that may or may not *two-birds-one-stone* on this topic:

[http://ubuntuforums.org/showthread.php?t=1273665](http://ubuntuforums.org/showthread.php?t=1273665)

---

