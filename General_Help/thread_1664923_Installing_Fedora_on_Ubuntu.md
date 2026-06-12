---
title: "Installing Fedora on Ubuntu"
date: 2011-01-11
forum: General Help
---

### Post by SquareRunner on 2011-01-11
I am trying to install Fedora alongside Ubuntu but have run into a bit of a snag.  I have the ISO burned to a disc, but it will not load on startup and doesn't have a prompt when the cd loads normally.  I have files on the cd, but Ubuntu cannot read them.  I am hoping someone here will have the answer to my query, if not then I would appreciate being re-directed to the appropriate support.

---

### Post by coffeecat on 2011-01-11
> **SquareRunner said:**
> I have the ISO burned to a disc, but it will not load on startup and doesn't have a prompt when the cd loads normally.  I have files on the cd, but Ubuntu cannot read them.

I'm having difficulty following that. It will not load on startup but doesn't have a prompt when it does load? Can you clarify?

Whatever. Did you burn the ISO as an image? What burning software did you use? What do you mean by "I have files on the cd, but Ubuntu cannot read them"? If you are running Ubuntu and you put the Fedora CD in the drive, do you see several folders and files, or do you see just one large .iso file? If the latter, you have not burnt it as an image and it will not be bootable.

When you do manage to boot the Fedora CD there are  a couple of things about the Fedora installer you need to know. It will detect Windows if you have Windows and will create a dual-boot grub menu, but it will not detect the presence of other Linux distros. Which means that (temporarily) you will not be able to boot into Ubuntu after installing Fedora. You have to either edit Fedora's menu.lst (it uses legacy grub), or repair Ubuntu's grub and run Ubuntu's update-grub to get Fedora onto the menu.

The first created user in Fedora has a UID of 500 - it's 1000 in Ubuntu - so you may run into permissions problems if you have shared files.

There are some other Fedora quirks you need to know about, but let's sort out the CD first.

---

### Post by bodhi.zazen on 2011-01-11
If it is a  Fedora CD you should try the Fedora Forums.

If the CD will not boot, check the integrity.

We need to know what version of Ubuntu / Fedora you are using, when version will not boot, and what CPU (32 or 64 bit) and what video card you have.

---

### Post by SquareRunner on 2011-01-11
I burned it as an image, but I just downloaded it again and I'm going to try it again because it matches your description as not having been burned as an image.

Ubuntu 10.10, Fedora 14; 32bit; integrated video card

Also, what's this about not being able to boot Ubuntu after booting Fedora from the disc?

---

### Post by SquareRunner on 2011-01-11
Wait, it has several folders and files, not one large ISO file.  So at this point I will assume I have burned the disc correctly.  Compatibility issues aside, how do I go about booting from the disc?  On startup all I get are the four 10.10 options and several 9.04 options from another issue I'm dealing with (the 9.04 startup options are there but should be gone as I have formatted the external drive containing that OS quite some time ago).  

Do I have to access something akin to the BIOS I would have accessed from a Windows OS to boot from a disc?  Or is it the same thing?

---

### Post by coffeecat on 2011-01-11
> **SquareRunner said:**
> Do I have to access something akin to the BIOS I would have accessed from a Windows OS to boot from a disc?  Or is it the same thing?

Yes. You cannot boot from a CD unless the BIOS is set to boot from the optical drive first. I usually make sure that all my machines are set to boot from the optical drive first, because it will simply skip this and boot from the hard drive if there is no CD/DVD in the drive.

You do not access the BIOS from Windows. There will be a key to press as soon as the POST screen appears to get into the BIOS. Often F2 or DEL, but sometimes something else. The POST screen may prompt you or it may be in your handbook/manual

The various 10.10 and 9.04 options are your grub menu from your hard drive install, so clearly the BIOS is not set to boot from the CD drive first.

---

### Post by SquareRunner on 2011-01-11
Ok, excellent.  Thank you both for your input, I was able to boot from the cd successfully but now all I have to deal with are issues with the partitions on my external drive and the 9.04 options that come up in my grub menu.

---

### Post by bodhi.zazen on 2011-01-11
Fedora should detect and configure Ubuntu as a part of the installation. If it does not, post back for assistance.

Take care , Fedora uses LVM by default, which you may or may not want. If you do not know what LVM is you can use it or not, not sure it matters.

---

