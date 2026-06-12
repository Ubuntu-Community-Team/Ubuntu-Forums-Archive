---
title: "sudo dpkg --configure -a how do I proceed?"
date: 2009-07-20
forum: General Help
---

### Post by thatsdaniel on 2009-07-20
I was trying to launch synaptic however I got the messagen run sudo dpkg --configure -a so I did and here is the result:

sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-rc1-custom
Cannot find /lib/modules/2.6.31-rc1-custom
update-initramfs: failed for /boot/initrd.img-2.6.31-rc1-custom
dpkg: subprocess post-installation script returned error exit status 1

How do I solve this? :D
Thanks in advance!

---

### Post by regala on 2009-07-20
> **thatsdaniel said:**
> I was trying to launch synaptic however I got the messagen run sudo dpkg --configure -a so I did and here is the result:

sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-rc1-custom
Cannot find /lib/modules/2.6.31-rc1-custom
update-initramfs: failed for /boot/initrd.img-2.6.31-rc1-custom
dpkg: subprocess post-installation script returned error exit status 1

How do I solve this? :D
Thanks in advance!

you have a kernel package (that you built) installed, but seems like you purged at least some parts of it manually without purging the package from the package management system. find which one it is and do ```
dpkg --purge --force-all package_name
```.

---

### Post by thatsdaniel on 2009-07-20
Im trying to search after it in aptitude, however im not in much luck.
I also searched for it by: dpkg -S /lib/modules/2.6.31-rc1-custom
Is there any other way I can search for it? :)

UPDATE: Apparently it was solved by running sudo apt-get install initramfs-tools so now it works just fine. "Weird", but IT works.

---

### Post by rokky on 2009-07-25
I had this same problem hit me tonight when I wanted to use Synaptic to install a new package.  However, my dpkg --configure error referred to /boot/initrd.img-2.6.24-21-generic which is leftover on my /boot partition from when I was running Ubuntu 8.04 on a different root partition from the one I recently installed Mint 7 (based on Ubuntu 9.04) onto.  

I have had this Mint 7 installation running for the last few weeks, and have done a few package update runs in that time, but don't remember exactly when the last one was.  

One possible suspect is, as with the 8.04 installation, the PC, a Fujitsu Lifebook P5020 with Intel graphics (getting to hate that video ...), occasionally refuses to shutoff, and the shutdown process jumps almost immediately to a blank screen and makes the fan come on full speed like the CPU is suddenly running flat-out.  The 1 or 2 times I left it alone for over a 30 minutes, it never let up and shutdown, so now I always just hold the power button down 6 seconds to force the PC to power off.  The next boot after that, often, but not always, it runs a fsck on at least my /home partition.  It became almost standard with the 8.04 shutdowns, and has just started happening on this 9.04 installation - creeping cruft?

uname shows this version:  2.6.28-11-generic .
That is what Mint 7 has right after an install and the initial "catch-up" update (just did that today on another machine).

Where is that old 8.04 reference, and how can I get rid of it in favor of the correct 9.04 setting?

thatsdaniel's solution of running "sudo apt-get install initramfs-tools "  just gave me the same error that synaptic originally did:
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

Catch-22...

TIA,
r

---

### Post by hansdown on 2009-07-25
Hi rokky.

Please, please, please, Try not to do hard resets. You may lose your valuable data.

In 8.04 you can use the "magic system request keys"

[http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html)

---

### Post by rokky on 2009-07-26
> **hansdown said:**
> Hi rokky.

Please, please, please, Try not to do hard resets. You may lose your valuable data.

In 8.04 you can use the "magic system request keys"

[http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html)
Thanks!  I have been working with PC's since the first IBM's came out in '81, and Linux since the days when I installed on a 386 with a bunch of floppy disks, so am keenly aware of the dangers of hard power offs, but have also seen enough times when there was no other option.   

Although I am running 9.04, I will try the "Alt+PrintScreen+R,S,E,I,U,B" trick next time to see what happens (altho, as I wrote, the screen blanking and fan startup are so sudden, I have my suspicions that this is one of those hard lockups, also might be tricky on a notebook keyboard since PrtScr is a shifted function key ... ). 

R

---

### Post by hansdown on 2009-07-26
My apologies rokky.

I don't know if  that combo works in 9.04.

It was broken in 8.10, but promised to be fixed in 9.04.

Just tested it. Works great!

---

### Post by rokky on 2009-07-27
> **rokky said:**
> I had this same problem hit me tonight when I wanted to use Synaptic to install a new package...
r

FIXED!   

I decided to look at /boot since it had the initrd.img files with current and older versions including the initrd.img-2.6.24-21-generic mentioned in the error message (oldest version there, from the prior/alternate 8.04 installation).  I noticed that version was referenced by the symlink, initrd.img, as well as the corresponding link for vmlinuz.  I deleted both of those sym links, and re-created them pointing to the latest versions that correspond to what Mint installed, and EUREKA! Fixed the issues with 'sudo dpkg --configure -a', which seems to have enabled allowing me to again use synaptic for updates as before (although before what seems to be a mystery...).  

That experience certainly implies interesting connections/dependencies behind the scenes.

Whew!

HTH,
r

---

### Post by rokky on 2009-07-27
> **hansdown said:**
> My apologies rokky.

I don't know if  that combo works in 9.04.

It was broken in 8.10, but promised to be fixed in 9.04.

Just tested it. Works great!

Not for me - just had the lockup after posting my 'FIXED' message, and shutting down  (posting this from my Nokia n810).  Maybe it is just the extra contortions of trying to also hold the Fn key while pressing all those others - will get my wife to literally lend an extra hand (or both ;-) ) next time it happens.

r

---

