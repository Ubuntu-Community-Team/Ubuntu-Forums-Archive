---
title: "Serious 64-bit Problems"
date: 2010-08-17
forum: General Help
---

### Post by kshawkeye on 2010-08-17
Hello, this is the third time I have had to reinstall Ubuntu 10.04 LTS 64-bit. Here are the steps I have taken each of the three times.

   1. Download the very latest Ubuntu from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
   2. Burn the image to a disc
   3. Reboot and boot from the disc
   4. Install Ubuntu along side Windows 7
   5. Finish the install and reboot
   6. Once Ubuntu loads for the first time, open the update manager
   7. Update everything
   8. Restart as asked after the update
   9. After restart, install device drivers
  10. (here is where everything is shot to hell) Random things are not opening (such as gedit) I will save a gedit document, then go to double click it, gedit will flash but not open
  11. I can't open the network manager at all, no window flashes, nothing seems to happen
  12. I reboot in the hopes that Ubuntu just needs to restart
  13. After reboot tons of pop up windows show up saying "the panel encountered a problem while loading "OAFID:GNOME....." blah blah blah, tons of those, so now all of my menu is gone

This has happened 3 times, and right now I am downloading the 32-bit edition in hopes that it doesn't run into the same problems. Keep in mind that this is on a fresh install, completely new and up to date system.

---

### Post by philinux on 2010-08-17
Which device drivers?

---

### Post by kshawkeye on 2010-08-17
My display drivers. It installed "NVIDIA Accelerated drivers" or something, sorry if that's not even close to what they are, but seeing that Ubuntu doesn't work I can't tell for sure.

It was my display drivers for my two GeForce 9800 GTX+ cards

---

### Post by kshawkeye on 2010-08-17
Well, I left a few steps out that I didn't think would effect the outcome, but now that I got the same problem with Ubuntu 32-bit I'm fairly sure that it has to do with Apache httpd.

I just now installed Ubuntu 10.04 32-bit to see if it was just a 64-bit problem, it isn't. Now my 32-bit Ubuntu is also broken. Here is what I did on the 32-bit install right after Ubuntu finished updating.

1. Download and install zlib with ./configure; make; sudo make install;
2. Downloaded and installed httpd with ./configure --prefix=/prefix/ --enable-mods-shared=all --enable-modules=all; make; make install
3. After httpd is done and installed I try and run:

sudo /path/to/httpd/bin/apachectl start 

and that I believe is when Ubuntu decides it doesn't feel like working anymore.

Any ideas?

---

### Post by ed-koala on 2010-08-17
I have the same graphics card setup you do, 2 9800 GTX cards, and they work fine for me.  Looks like Apache is the problem, somewhere.  Sadly, I know nothing about Apache but I wanted you to know it most likely isn't the dual cards.

---

### Post by kshawkeye on 2010-08-17
Thanks a lot, anything to narrow it down helps

---

### Post by Ub28 on 2010-08-17
Have you run hardware diagnostics for the CPU, RAM and hard drive?  If these diagnostics can be run for a long time i.e. 24 hours for CPU, 24 hours for RAM and the longest test mode for the hard drive, hopefully that could eliminate a hardware fault?

The slightest fault in hardware can cause unexplained problems.

---

### Post by kshawkeye on 2010-08-18
No, I haven't done that, it's something to deal with Apache httpd killing ubuntu

---

### Post by kshawkeye on 2010-08-19
Does no one have any ideas? Is it impossible to build and run the latest httpd (v2.2.16) on Ubuntu 10.04?

---

### Post by kshawkeye on 2010-08-20
I really would like some help with this...

---

### Post by kshawkeye on 2010-08-22
Any ideas?

---

### Post by Ginsu543 on 2010-08-22
Do you have separate / and /home partitions? And are you by any chance reinstalling the OS in the / partition without formatting your /home partition? If so, you may be getting those errors because all the config files still in your /home folder are expecting their respective programs to be installed, are looking for them in the / partition but not finding them.

---

### Post by hotrodder on 2010-08-22
Try burning the discs at 4X or slower and make sure that you check the md5 sum.

That's all I got.

---

