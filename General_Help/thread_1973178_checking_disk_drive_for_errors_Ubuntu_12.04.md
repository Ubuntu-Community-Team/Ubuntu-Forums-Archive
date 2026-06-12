---
title: "checking disk drive for errors Ubuntu 12.04"
date: 2012-05-04
forum: General Help
---

### Post by martin72 on 2012-05-04
I have updated my netbook from Ubuntu 11.10 to version 12.04. Everything works fine except every startup (always shutdown my netbook) i get the message "Checking disk drives for errors. This may take several minutes" while the system is booting. I don't get this message before when i used the previous versions of Ubuntu. I checked my disk with "Disk Utility" but it says the disk is healthy.
Even if i pass the error check test, the next time i boot the system the same check will be performed.
So is it possible this is a bug, or has someone a solution for this?

---

### Post by artofsnow on 2012-05-05
Same thing for me ... not sure if it does it at every boot but it does very often.

If I cancel the disk check, it tells me that there are errors.

---

### Post by hipertrofia on 2012-05-06
Same thing here. Seems to be a bug!

---

### Post by smurphy on 2012-05-06
Try setting the interval between checks and mount count counters to 0.

```

tune2fs -c 0 -i 0 /dev/sda1

```
Should disable it for /dev/sda1 here

---

### Post by pascalio on 2012-05-07
Hi!
I have the same problem. (without the actual error message after cancelling though)
I've tried tune2fs -c 0 -i 0; the command does its job but the check will invariably be done at start up.
If I take away the splash screen at boot, there's a message from fsck (the program that decides whether to perform a check or not) : "[my boot partition] has not been unmounted properly: check forced" whereas I shut down the system regularly. I'm nothing of an expert in this matter but it seems that, on ext2 filesystems, the "dirty bit" is set when it's mounted and unset when unmounted so that if there's a crash or irregular shutdown, this bit is still set and check is due. So I checked my unmounted boot partition from a usb live session with tune2fs -l [my boot partition], and saw that even unmounted, that filesystem's state was : "not clean". Perhaps, the error lies here: the "not clean" bit is not unset by Ubuntu at shutdown...
Or perhaps, the error is somewhere else, but would you mind doing the same test too?
Thank you!

---

### Post by ezzy1980 on 2012-05-07
I had the same issue..  Ubuntu 12.04 LTS Server...

every ssh claimed that  needs to check my disk (only 1 drive in system...) 

got the following message:

```
*** /dev/sda1 will be checked for errors at next reboot ***

```

I did the:

```
sudo touch /forcefsck

```and then did another reboot:

```
sudo shutdown -r now

```
and it came back up and this time no  message about having to do a file system check...

Hope that helps....

---

### Post by pascalio on 2012-05-10
Hello!
I'm sorry, I don't really see the relationship with the problem... Do you mean that fsck check that appears to be done at boot is not actually done and we need to force it to be really done to solve the problem? In other words, did you also have a long and inexplicable disk drive check at every boot of the system, which you could fix by a "sudo touch /forcefsck" ?
In any case, thanks for the reply!

---

### Post by CharlesA on 2012-05-10
Running "sudo touch /forcefsck" will force a fsck on next boot.

It doesn't run every time.

---

