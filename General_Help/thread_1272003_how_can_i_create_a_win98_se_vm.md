---
title: "how can i create a win98 se vm?"
date: 2009-09-21
forum: General Help
---

### Post by kooley on 2009-09-21
i have read on a few other sites that u can run a vm of windows and iv been wondering if its possible to have one for win98se so i can play my old games from the 90's that require dos. and all the vmware stuff i come across has been for xp and vista. i installed a version of vmware a while ago and could never get it to open, and i never understood how to make the virtual macien. so i was wondering if anone could teach me how to make a vm of win98se(i have the os disk for it) if its possible.


thnx

---

### Post by badger_fruit on 2009-09-21
There are a number of steps to do this;

Install the Virtual Machine software (Virtual Box, VMWare or whatever)
Install the "Guest" operating system

This guide --> [http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu) will help you perform the installation of the VMSoftware, in this case Virtual Box.

All you need to do then is create a virtual machine.
Basically it's wizard-driven - point and click - asks you for the name of the VM (so you can identify it later on), and a few other bits and bats.

The wizard usually kicks off by asking what OS you wish to install, it will set up some defaults for that OS (such as amount of memory and recommended virtual HDD space).  A Virtual HDD is a file on your local PC which the Guest OS recognises as an actual Hard-drive.  You can have as many of these as you have space on your actual HDD (although creating a 70GB Virtual HDD on an 80GB Actual HDD is NOT recommended!)  

Anyway, follow the wizard and you'll be up in no time at all, generally for a first run and first time user, the defaults are good enough.

Then when done, start the virtual machine.  It will boot as if you were using another computer, recognise if there is a CD in the drive and attempt to boot from that, if no CD then it will try to boot from the virtual HDD which, if blank will result in "no OS found" or if you've completed an installation of an OS, it should boot.

That's pretty much the basics, once the OS is installed you can use it as if it were a real PC although with it being virtual, there are some restrictions.  The particular project's home page 

[www.vmware.com](www.vmware.com)
[www.virtualbox.org](www.virtualbox.org)

will detail these for you.

---

### Post by kooley on 2009-09-21
alright thnx m8

---

