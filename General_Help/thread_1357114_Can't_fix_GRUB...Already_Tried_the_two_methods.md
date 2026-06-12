---
title: "Can't fix GRUB...Already Tried the two methods"
date: 2009-12-16
forum: General Help
---

### Post by kwabena39 on 2009-12-16
Hi,
I had Ubuntu 8.04 64-bit working on one drive and I wanted to install Mepis on the second drive.  

The reason why I got Mepis in the first place is because I wanted to run Rosegarden, which I thought would work better in a distro that did the KDE environment well.  Yet I wanted to keep my regular old Ubuntu, because I like alot of stuff there. (I tried Ubuntu studio stuff already in Ubuntu, but it was spotty).

When I tried to install Ubuntu Studio stuff, (which I had subsequently removed), it left "Ubuntu rt" as the first boot option, and I didn't want to boot into Ubuntu RT because it didn't work with my video card driver.

So when I started Mepis, the only option it gave me was to boot Ubuntu RT, **NOT Ubuntu Generic,** which I needed.  So I then tried to go and fix Grub with the Mepis CD, and then a SuperGrub CD, but it just messed everything up.

So then I tried the two methods described in these forums: I tried to use the Live CD manual install, but did not see ANYTHING  in there about mounting anything, and I couldn't get past the Partition stage; it was trying to force me to re-partition the drive.

So I then tried the command line stuff, you know, like sudo grub, followed by find grub, followed by root (hd0,0) and setup (hd0), and stuff.

That didn't work.  All it left me with was an error that boot menu did not exist or something like that.

Now, I can't get into either my old Ubuntu system OR my new Mepis system.

any help, please?

---

### Post by zvacet on 2009-12-17
You should be able to install Ubuntu by choosing manual way.Whan you are there remove existing ubuntu partition and on that free space install ubuntu again.

---

### Post by Tavarid on 2009-12-17
You could try using an ubuntu live-cd to run 'update-grub' if its available to you.  You can also do this through a root shell if you can manage that as well.  I'm not really sure how much this will help, but then again I've not used Ubuntu in ages. :)

---

### Post by Leppie on 2009-12-17
what do you get when your pc boots? is grub loading, or does it halt with errors before getting you to the grub menu?
if grub does load (not necessarily until the menu), you can try to boot manually from the grub shell.

---

