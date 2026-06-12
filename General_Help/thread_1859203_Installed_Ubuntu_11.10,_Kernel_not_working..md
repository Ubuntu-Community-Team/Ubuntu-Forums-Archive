---
title: "Installed Ubuntu 11.10, Kernel not working."
date: 2011-10-13
forum: General Help
---

### Post by galacticaboy on 2011-10-13
I just upgraded to Ubuntu 11.10 from 10.10. It installed the new Kernel 3.x, when I try to boot into the new kernel, it just goes to a purple screen and will not boot, but in GRUB if I select the older version of the kernel, the one I had before updating, it will boot right up into 11.10 with the old kernel, why is that?

---

### Post by sikander3786 on 2011-10-13
First of all, are you sure you've successfully upgraded to 11.10? Please post the output of this command from a Terminal:

```
lsb_release -a
```

And for upgrading 10.10 to 11.10, you first need to upgrade to 11.04 and then to 11.10, step by step. Was it like this?

---

### Post by effenberg0x0 on 2011-10-13
Likely plymouth problem, due to incorrect setup of video drivers.

On boot, hold shift to see grub options. select the recovery option and drop to a root shell prompt. 

```
sudo nano /etc/default/grub
```

make sure you remove "quiet" and "splash" from this file and that the line below only has "nomodeset".

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Press CTRL+X, Y and <ENTER> in sequence to save the file and exit to prompt.
Now run:

```
sudo update-grub
sudo reboot now
```

Report back.

Regards,
Effenberg

---

### Post by galacticaboy on 2011-10-13
> **sikander3786 said:**
> First of all, are you sure you've successfully upgraded to 11.10? Please post the output of this command from a Terminal:

```
lsb_release -a
```

And for upgrading 10.10 to 11.10, you first need to upgrade to 11.04 and then to 11.10, step by step. Was it like this?

I put that into my terminal and got this

```
david@David-Ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
```

---

### Post by galacticaboy on 2011-10-13
> **effenberg0x0 said:**
> Likely plymouth problem, due to incorrect setup of video drivers.

On boot, hold shift to see grub options. select the recovery option and drop to a root shell prompt. 

```
sudo nano /etc/default/grub
```

make sure you remove "quiet" and "splash" from this file and that the line below only has "nomodeset".

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Press CTRL+X, Y and <ENTER> in sequence to save the file and exit to prompt.
Now run:

```
sudo update-grub
sudo reboot now
```

Report back.

Regards,
Effenberg


I did this and tried to boot back into the 3.x kernel and it brought me to this black screen that displayed a bunch of words and numbers. It sorta looked like the screen you get when you have a Kernel Panic, but it said nothing about a Kernel Panic, I am now back on the old kernel.

The last few lines of that message look like this

kernel_init+0xaa/013b
start_kernel+0x358/0x358
kernel_thread_helper+0x6/0x10

There is more preceding it, but its way to much to write down.

---

### Post by galacticaboy on 2011-10-13
I fixed it, I had to edit my Grub file to read "acpi=off" and it works just fine, I am just hoping I don't have to do that everytime! lol Thanks for all the help though!

---

### Post by ZING on 2011-10-14
> **galacticaboy said:**
> I fixed it, I had to edit my Grub file to read "acpi=off" and it works just fine, I am just hoping I don't have to do that everytime! lol Thanks for all the help though!

Where and how do you edit that to gwet it to work? I am having the same problems... but even when changing to nomodeset I still get a blank purple screen

---

### Post by galacticaboy on 2011-10-14
I did:

```
sudo gedit /etc/default/grub
```

Then where you put the "nomodeset" at, delete "nomodeset" and make it look like this

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

Make sure to delete nomodeset, that is how I got it to work. Good luck to you!

---

### Post by ZING on 2011-10-14
> **galacticaboy said:**
> I did:

```
sudo gedit /etc/default/grub
```

Then where you put the "nomodeset" at, delete "nomodeset" and make it look like this

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

Make sure to delete nomodeset, that is how I got it to work. Good luck to you!



I tried that also with the same thing... just a purple screen

---

### Post by DanClegg on 2011-10-15
Hi, same issue with me. Just upgraded to 11.10 and that ls command for distro version confirms this.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

Hangs on purple/black screen with no response to any keys whatsoever. When restarted in recovery mode from grub option in main menu it goes from starting initramfs to a screen with larger text and hangs there simmilarly with no response. various log entries are shown each time. Attached photos show these.
One has a kernel oops, another two EID problems or something...

Editing and updating grub with the acpi=off has no effect and neither does nomodeset.

Can boot into previous linux versions from grub no problem.

/etc/X11/default-display-manager contains only:
/usr/sbin/lightdm

however, I thought I chose gdm at distro upgrade...

any help appreciated!
Thanks!

---

### Post by jtuchscherer on 2011-10-17
Update:

I obviously had two big issues

1.) I had to add nohz=off to my GRUB_CMDLINE_LINUX_DEFAULT line

and

2.) I had to reinstall the proprietary ati driver for my video card.

After that everything is fine again.



Hi DanClegg, 

I have the exact same symptoms (except, that I even cannot boot into older kernels). If you find a solution, please let me know. Likewise, I will post here, if I find out what's wrong with my machine.

It is hard to diagnose when even the recovery console does not work.

---

### Post by DanClegg on 2011-10-17
Will do.
Seems to be different from this thread [http://ubuntuforums.org/showthread.php?t=1860359](http://ubuntuforums.org/showthread.php?t=1860359)
as there's no response to keyboard on blank screen and solutions mentioned in my first post didn't have any effect. I'm new here, does this thread need to be marked as 'unsolved' or something now that I've posted my unsolved case here?

---

### Post by DanClegg on 2011-10-17
SOLVED!
found ACPI message in hanging panic screen and so did the above posted directions about acpi:
sudo nano /etc/default/grub
and changed these lines to look like:
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"
GRUB_CMDLINE_LINUX=""

I had tried 
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
and
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
to no avail. 
but 
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"
worked like a charm except isn't as pretty on startup cause of the logging stuff showing.

thanks galacticaboy!
good luck jtuchscherer!

---

### Post by bie on 2012-01-04
Had the exact same problems, after updating to 10.11 kernel did not boot anymore.

changing /etc/default/grub line
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"

did the trick. For updating the grub I used a live cd and chroot. According to this help:

[http://www.linuxquestions.org/questions/linux-software-2/grub2-rewrite-from-livedvd-878892/](http://www.linuxquestions.org/questions/linux-software-2/grub2-rewrite-from-livedvd-878892/)

---

