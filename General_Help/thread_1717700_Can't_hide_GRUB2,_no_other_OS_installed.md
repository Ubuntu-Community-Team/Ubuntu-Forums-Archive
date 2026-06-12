---
title: "Can't hide GRUB2, no other OS installed"
date: 2011-03-30
forum: General Help
---

### Post by sherl0k on 2011-03-30
I'm running 10.04.2 LTS and I can't make the GRUB menu hidden, or timeout to automatically boot the first option in the menu.

Here is my /etc/default/grub :

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text vga=791"
GRUB_CMDLINE_LINUX=""
```

Every time I reboot I get the GRUB2 menu. I don't want that. I just want it to boot normally! I've tried setting GRUB_DEFAULT to saved but that doesn't work either.

---

### Post by andrewthomas on 2011-03-30
> **sherl0k said:**
> I'm running 10.04.2 LTS and I can't make the GRUB menu hidden, or timeout to automatically boot the first option in the menu.

Here is my /etc/default/grub :

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text vga=791"
GRUB_CMDLINE_LINUX=""
```Every time I reboot I get the GRUB2 menu. I don't want that. I just want it to boot normally! I've tried setting GRUB_DEFAULT to saved but that doesn't work either.
What happens when you set the grub timeout to 0?
```
GRUB_TIMEOUT=0
```

---

### Post by oldfred on 2011-03-30
I have never understood the timeouts, as I have not had to change anything. Do not change it to 0 as then you will have trouble using shift to get to menu if you really need it.

See comments by drs305 and the many links he has in his signature.
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)


The real problem may be because you are creating an error with the VGA setting.

"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)
vga=xxx is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)

VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

---

### Post by mikewhatever on 2011-03-30
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=3
GRUB_HIDDEN_TIMEOUT_QUIET=true
#GRUB_TIMEOUT=10

```

...then 'sudo update-grub'

---

### Post by sherl0k on 2011-03-30
I tried that Mike, no dice.

Fred, the vga=791 is for setting the resolution when the kernel boots, not for GRUB. I removed it anyway though, to no avail.

The only other options I have in my GRUB menu are older kernels and their recovery modes; I would rather not remove everything because I still would like to access recovery mode if needed.

---

### Post by drs305 on 2011-03-30
sherl0k,

To see if this is a 'recordfail' problem, edit grub.cfg and disable the recordfail check:
```

gksu gedit /boot/grub/grub.cfg
```

Comment the following lines to prevent a 'recordfail' from stopping the boot. Leave the timeout at least one second or more for now.
> 
[COLOR="Red"]**#**[/COLOR]if [ "${recordfail}" = 1 ]; then
[COLOR="Red"]**#**[/COLOR]  set timeout=-1
[COLOR="Red"]**#**[/COLOR]else
  set timeout=[COLOR="Red"]**3**[/COLOR]
[COLOR="Red"]**#**[/COLOR]fi
Do NOT update grub, as it would overwrite this change.

If this now lets you to boot the way you want we can provide a more permanent fix. (It will show the menu for 3 seconds, then boot. I agree with *oldfred*, let it display for at least 1 second so you can interrupt it.)

---

### Post by sherl0k on 2011-03-30
Indeed, commenting that out gives me a 3 second timeout at the GRUB menu, and boots the first option by default. This is a great solution. :)

I am afraid that the next time I upgrade my kernel and GRUB regenerates I will have to redo this, unless a permanent solution is possible? I'm assuming in 00_header lies the change required?

edit: yep, found the same lines in 00_header and made the changes there, ran update-grub and now it's permanent.

Odd that it happened in the first place, though.

---

### Post by drs305 on 2011-03-30
Finding out exactly what triggered the recordfail event is something I've tried in the past without success. I know some of the reasons but there are many more I haven't found. 

In any case, disabling the recordfail check is something that will work as long as you don't mind that the system will continually reboot if there is a problem, rather than wait for you to select something else. 

Of course, the SHIFT key interrupt should still be available to stop the boot as long as you are there when it reboots. This depends upon the presence of the keystatus check in your grub.cfg file. There are a few configurations which eliminate the keystatus check, which is one of the reasons I recommend displaying the menu for at least a second or two (so you can interrupt it).

---

### Post by sherl0k on 2011-03-30
One would think that a function named "recordfail" would do just that, record the fail :) I don't mind the reboots, I highly doubt that would happen in my scenario here so it's perfectly acceptable.

Thanks for the help, you've assisted me greatly!

---

