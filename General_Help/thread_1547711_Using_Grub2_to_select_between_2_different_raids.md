---
title: "Using Grub2 to select between 2 different raids"
date: 2010-08-07
forum: General Help
---

### Post by ApolloRover on 2010-08-07
I am currently running a system that has Windows 7 and Ubuntu 10.04 running on separate raids.  Here is an outline of my system.

Raid 1: 
OS: Windows 7
Raid Controller: Intel ICH5R
Raid Type: 1 (Mirror)
# of Disks: 2
Disk Type: Sata HDDs

Raid 2:
OS: Ubuntu Lucid Lynx 10.04
Raid Controller: Rosewill 212 Raid PCI Card (The raid function is disabled, so the computer recognizes the drives as being hooked up to a normal IDE port)
Raid Type: 1 (Mirror, Softraid configured via the Alternate Installation CD)
# of Disks: 2
Disk Type: IDE HDDs

I would have liked to put both raids on the same controller but Windows XP/Vista/7 will sometimes throw up a blue screen when a single controller handles two independent raids.  My setup prevents this issue.  The good news is that I was able to get both of the raids up and running without much difficulty.

Right now I can only access my Ubuntu raid by going into the bios on startup and changing the boot order.  Needless to say, this has become somewhat tiresome.  It would be much simpler if I could use Grub2 to select between operating systems upon boot.  While I know the process of installing Grub2 on a dual-booted system is relatively painless, I imagine my setup would be more complex.

If someone could let me know what I would have to do to get Grub2 working on my setup, I would be very thankful.

---

### Post by dino99 on 2010-08-07
have searched a little but failed to find something usefull about your issue

might be a good reason to send your request to grub2 dev:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-06-04-hacking-on-grub2](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-06-04-hacking-on-grub2)

and/or open a bug on launchpad: 

into a console, run:
ubuntu-bug grub-pc

---

