---
title: "How to solve ureadahead..(336) proc. term. with status 5?"
date: 2010-06-26
forum: General Help
---

### Post by sentinella86 on 2010-06-26
How to solve ureadahead-other main "(336)" process terminated "with status 5"??? help??

I have ubuntu 10.04 64 bit, normal install(no different directory or partition)

---------------FOR SOLVE!!!!!!!!-----------------

 sudo sed -i 's+^start on starting mountall+start on mounted MOUNTPOINT=/var+' /etc/init/ureadahead.conf

---

### Post by dino99 on 2010-06-26
try into a console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure ureadahead

---

### Post by sentinella86 on 2010-06-26
> **dino99 said:**
> try into a console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure ureadahead

Nothing. :-(  now is : ureadahead..(343) proc. term. with status 5

---

### Post by dino99 on 2010-06-26
an other way:

goto synaptic, search "ureadahead", right click on it to completly remove it (dont worry about ubuntu-minimal, you will reinstall it later),validate then reinstall ureadahead & ubuntu-minimal

reboot

---

### Post by sentinella86 on 2010-06-26
> **dino99 said:**
> an other way:

goto synaptic, search "ureadahead", right click on it to completly remove it (dont worry about ubuntu-minimal, you will reinstall it later),validate then reinstall ureadahead & ubuntu-minimal

reboot

No. now (322) status 5!!

Any solutions??

---

### Post by sentinella86 on 2010-06-26
solutions?

---

### Post by Fisaulerod on 2010-07-01
I have the same problem, and the boot it's very slow.

---

### Post by sentinella86 on 2010-07-06
> **Fisaulerod said:**
> I have the same problem, and the boot it's very slow.

Is the floppy disk?

---

### Post by sentinella86 on 2010-07-06
FOR SOLVE!!!
USE THIS COMMAND :
```
 sudo sed -i 's+^start on starting mountall+start on mounted MOUNTPOINT=/var+' /etc/init/ureadahead.conf

```

---

### Post by dragonsouce on 2010-11-13
Hi, Have a similar problem after a update to 10.04.
init. ureadahead mainprocess (2555) terminated with status 5
when i tried your solution 

sudo sed -i 's+^start on starting mountall+start on mounted MOUNTPOINT=/var+' /etc/init/ureadahead.conf 

It said that *ureadahead.conf* was read only even logged in at root.

so what am i doing wrong???

---

### Post by ozzman2 on 2011-01-02
> **sentinella86 said:**
> FOR SOLVE!!!
USE THIS COMMAND :
```
 sudo sed -i 's+^start on starting mountall+start on mounted MOUNTPOINT=/var+' /etc/init/ureadahead.conf

```


Thank you!   This worked for me.

If anybody else is running 10.04 on an ASUS M3N78-VM motherboard, you probably get a second error message to go with this too.  Here's what fixed that one for me:

use "sudo gedit /etc/default/grub"

on the line that has:
[COLOR=#595959]GRUB_CMDLINE_LINUX=""
change it to:
[/COLOR][COLOR=#595959]GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax[/COLOR]"

save and exit

then run "sudo update-grub"

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440780)

---

### Post by Bucic on 2011-02-17
> **sentinella86 said:**
> FOR SOLVE!!!
USE THIS COMMAND :
```
 sudo sed -i 's+^start on starting mountall+start on mounted MOUNTPOINT=/var+' /etc/init/ureadahead.conf

```
That didn't work for me. The ureadahead errors are still there during the boot process.

---

### Post by chris_gs on 2011-03-31
:D
Just wanted to add that the original solution worked a charm for me.  Running a mythbuntu 10.10 box, so all the recordings are stored on var -so i don't want it to overfill, and boot time is very important because every time you turn the TV on it has to boot (if you're watching through it..)
Thanks!

---

