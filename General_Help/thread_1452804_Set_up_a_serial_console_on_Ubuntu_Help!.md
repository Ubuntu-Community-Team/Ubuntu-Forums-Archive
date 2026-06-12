---
title: "Set up a serial console on Ubuntu??? Help!"
date: 2010-04-12
forum: General Help
---

### Post by redrumloa on 2010-04-12
I tried to set up a serial console on Ubuntu 9.10 last night and ended up going to bed with a headache. I can navigate myself about in console, but am in no way an expert. Hopefully someone can lend a hand.

First thing I found out is /etc/inittab no longer exists. After some searching I see that I need to set up a ** /etc/init/ttyS0.conf **file and issue a **sudo start ttyS0**, so I do that. I try to log into a serial console, no luck. After some more digging it appeared that ttyS0 is restricted, so I changed the permissions. Still no luck logging into a serial console.

Any help is appreciated.

---

### Post by redrumloa on 2010-04-12
Ok I am looking at this again

---
redrumloa@redrumloa:/dev$ ls -l ttyS0
crw-rw---- 1 root root 4, 64 2010-04-12 15:26 ttyS0
---

Should this be "root dialout" instead of "root root"?

---

### Post by redrumloa on 2010-04-12
redrumloa@redrumloa:/dev$ sudo chgrp dialout /dev/ttyS0
redrumloa@redrumloa:/dev$ ls -l ttyS0
crw-rw---- 1 root dialout 4, 64 2010-04-12 15:26 ttyS0
---

Still no banana. Ideas?

---

### Post by redrumloa on 2010-04-12
In case this helps.

---
redrumloa@redrumloa:~$ dmesg | grep tty
[    0.002016] console [tty0] enabled
[    0.975473] 0000:03:0a.0: ttyS0 at I/O 0x8c00 (irq = 18) is a 16550A
[    0.975614] 0000:03:0a.1: ttyS1 at I/O 0x8800 (irq = 18) is a 16550A
---

---

### Post by redrumloa on 2010-04-12
Well I am talking to myself, but at least I can make a history of what I did ;-)

It appears permissions are not staying.

redrumloa@redrumloa:/dev$ ls -l ttyS*
crw------- 1 root root    4, 64 2010-04-12 16:49 ttyS0
crw------- 1 root root    4, 65 2010-04-12 16:48 ttyS1

Why defaulting back? Hmm...

---

### Post by redrumloa on 2010-04-12
Last bump. I tested the cable, null modem and other non-Ubuntu computer and it works fine. I cannot get any life out of the serial port. I am stuck.

Last bump on this site. Anyone?

---

### Post by bab1 on 2010-04-12
> **redrumloa said:**
> Last bump. I tested the cable, null modem and other non-Ubuntu computer and it works fine. I cannot get any life out of the serial port. I am stuck.

Last bump on this site. Anyone?

Is this a Gnome or KDE desktop host?

---

### Post by Chronon on 2010-04-12
I don't have anything direct to contribute other than to ask if you already consulted the community help page:
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

---

### Post by redrumloa on 2010-04-12
> **bab1 said:**
> Is this a Gnome or KDE desktop host?

Gnome.

---

### Post by redrumloa on 2010-04-12
> **Chronon said:**
> I don't have anything direct to contribute other than to ask if you already consulted the community help page:
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

Yes, thanks.

---

### Post by Mister.Vash on 2010-04-13
First question
After adding yourself to the dialout group, did you restart the system?  
If you have not, restart and log back in again.  Once done, what is the output of the command
```
groups
```
Does that list the dialout group?  You should expect to see that after adding your account in and restarting the system.


Second Question
If that looks good, have you checked the bios to make sure that the serial port is enabled?  If not, enable it and see if that makes a different.


Third Item
if your run
```
dmesg | grep tty
```do you see an output line similar to the following indicated that it found it:
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

If none of that seems to make any difference - I would say to start with one of the following:  Post all the items that you have changed to try and get it working and we can see if you were missing something

or we could go with a guess that something is wrong with the udev rules making it root:root instead of root:dialout and try fixing that

Here is an older link of adding a rule:
[http://ubuntuforums.org/showthread.php?t=782115](http://ubuntuforums.org/showthread.php?t=782115)
and here is one where the where changing the name of the group from dialout to nut
[http://ubuntuforums.org/showthread.php?p=8799392&nojs=1#goto_threadtools](http://ubuntuforums.org/showthread.php?p=8799392&nojs=1#goto_threadtools)

---

### Post by redrumloa on 2010-04-13
@Mister.Vash
Thanks for the reply!

> redrumloa@redrumloa:~$ groups
redrumloa adm dialout cdrom plugdev lpadmin admin sambashare


The bios has the serial port enabled. 

> redrumloa@redrumloa:~$ dmesg | grep tty
[    0.002018] console [tty0] enabled
[    0.974952] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.975206] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


As for sequence? I made sure the serial port was set up, then I created the /etc/init/ttyS0.conf, then I issued a "sudo start ttyS0". Next I added user to the dialout group with "sudo adduser redrumloa dialout".

I tried to change the permissions and the group. They would change, but it would not work. Upon reboot, the change goes away. I tried fixing this by adding this line KERNEL=="ttyS[0-9]", GROUP="dialout", MODE=" to /etc/udev/rules.d/40-permissions.rules. Didn't help. I think that is it.

I will check those other threads, thanks. See anything I did wrong in the above?

---

### Post by redrumloa on 2010-04-13
@Mister.Vash

Fro your 2nd link.

> The solution suggested in previous reply will not sustain re-installations or future upgrade of udev.

In order to resolve this, copy the /lib/udev/rules.d/50-udev-default.rules to /etc/udev/rules.d/52-udev-default.rules and change the following rule from
Quote:
KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout"
to
Quote:
KERNEL=="tty[A-Z]*[1-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout"
Below this add the following rule
Quote:
KERNEL=="ttyS0", GROUP="nut"
From /etc/udev/rules.d/README:
Quote:
Packages do not generally install rules here, this directory is for
local rules. If you want to override behaviour of package-supplied
rules, which can be found in /lib/udev/rules.d, you can do one of
two things:

1) Write your own rules in this directory that assign the name,
symlinks, permissions, etc. that you want. Pick a number higher
than the rules you want to override, and yours will be used.

2) Copy the file from /lib/udev/rules.d and edit it here; you
should generally only do this if you want to prevent a program
from being run. 

I followed this, but not to change group to "nut" rather to "dialout". No banana, still getting "root".

---

### Post by Mister.Vash on 2010-04-14
The rule it should be picking up to set the permissions should be in the file /lib/udev/rules.d/50-udev-default.rules

I have the following line in mine by default, which should cover setting the permission for ttyS0
```
KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout"
```

I'd say double check and see if that line is in that file, it is the first entry under the '# serial' section in mine.  If it is in there, try doing the following.

With the naming of your file, that rule would be processed prior to when the system sets it.  Rename the 
/etc/udev/rules.d/40-permissions.rules
to
/etc/udev/rules.d/90-permissions.rules

From the README in that folder, 'Pick a number higher than the rules you want to override, and yours will be used.'

As for the contents of that file, I'm not sure if the MODE= portion needs to be in it.  I think that can probably be left out for now and would only need to be revisited if the permissions are wrong once the group actually shows up.

---

