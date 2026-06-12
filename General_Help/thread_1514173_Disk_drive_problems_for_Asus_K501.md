---
title: "Disk drive problems for Asus K501"
date: 2010-06-20
forum: General Help
---

### Post by joeyfixit on 2010-06-20
So I have an Asus K501J, which I've had for about eight months and have always had ubuntu on. Periodically this problem comes up: I put a DVD in the disk drive, and the drive spins for a couple of seconds, then stops and that's it. Can't find the disk under places, can't open files with video programs like vlc. The disk ejects fine, but it's as if the laptop doesn't believe there's anything in the drive. 
This problem seemed to go away after I updated to Ubuntu 10.04, but now it's back. Before the upgrade I took it to my computer expert friend, but (like some other laptop problems) it never seems to manifest in his presence, and he therefore has no suggestions. 

This is really frustrating; any ideas?

---

### Post by davidmohammed on 2010-06-20
I have come across other threads mentioning similar non-mounting issues for DVD drives.  Common thread is that installing the 2.6.34 kernel works.

If you don't feel comfortable doing this - then don't...

But if being brave then

go to this [site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/")

now download the following links:
linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38 675K 
linux-headers-2.6.34-020634_2.6.34-020634_all.deb 17-May-2010 20:27 9.6M 
linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38 30M 

check they have downloaded to your Downloads folder

then

cd Downloads
ls *.deb --> should list the 3 files above
sudo dpkg -i *.deb --> this will install all three deb files

if you see any errors being reported then the install hasn't worked.

reboot

---

### Post by joeyfixit on 2010-06-20
Thanks for the help.

ls *.deb
ls: cannot access *.deb: No such file or directory

What's this about? I see them in my download folder.

---

### Post by davidmohammed on 2010-06-20
type 

pwd

it should display that you are currently in your Downloads folder

if it doesn't

cd ~/Downloads

---

### Post by joeyfixit on 2010-06-20
Thanks for your patience.
I tried what you suggested. Nothing's changed.

---

### Post by joeyfixit on 2010-06-20
anyone else have ideas?

cds seem to work fine, btw

---

