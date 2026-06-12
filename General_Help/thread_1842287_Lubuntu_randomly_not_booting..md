---
title: "Lubuntu randomly not booting."
date: 2011-09-11
forum: General Help
---

### Post by Gaygerbil on 2011-09-11
Hey guys I'm running Lubuntu 11.04 on an eMachine. 

My problem comes during booting, when the boot goes to Grub if I hit enter on the option I want instead of waiting it out I notice it will frequently start loading and just stay there.

I looked at what it was stopping at a lot of times it would be something with lmsensor, but other times it would be different. I can't quite remember.

The system is not frozen however as I can hit Alt-Ctl-Del and it'll restart. Anyone have/had similar problems to this?

---

### Post by decrepit on 2011-09-11
Yep,

[http://ubuntuforums.org/showthread.php?t=1838111](http://ubuntuforums.org/showthread.php?t=1838111)

I've got the same problem, I commented out "quiet splash" so I can see where it crashes, but since then it hasn't failed.

---

### Post by amjjawad on 2011-09-13
> **Gaygerbil said:**
> Hey guys I'm running Lubuntu 11.04 on an eMachine. 

My problem comes during booting, when the boot goes to Grub if I hit enter on the option I want instead of waiting it out I notice it will frequently start loading and just stay there.

I looked at what it was stopping at a lot of times it would be something with lmsensor, but other times it would be different. I can't quite remember.

The system is not frozen however as I can hit Alt-Ctl-Del and it'll restart. Anyone have/had similar problems to this?

Hi,

Is Lubuntu 11.04 the only OS installed on your machine?

What kernel are you using right now?

Is that a fresh new installation?

Have you checked MD5SUM for the iso you downloaded form Lubuntu before burning it to a CD?

What do you mean by:
> when the boot goes to Grub if I hit enter on the option I want instead  of waiting it out I notice it will frequently start loading and just  stay there.

---

### Post by Gaygerbil on 2011-09-14
I think I also have Vista leftover on here, I'm not really sure I haven't checked, I don't even want to boot it cuz it's so slow.

I'm using Linux kernel 2.6.38-11-generic on a 32 bit system.

No it's an upgrade, I started from 10.04 and kept upgrading, so it wasn't from a CD.

Grub gives me options to chose which kernel I want to boot with or Vista, I really have never tried choosing anything other than the standard first choice. But usually it takes 5 seconds to choose the highlighted selection by default.

Where can I find this quiet splash option?

---

### Post by amjjawad on 2011-09-14
> **Gaygerbil said:**
> I think I also have Vista leftover on here, I'm not really sure I haven't checked, I don't even want to boot it cuz it's so slow.

No need to login to Vista, I was just checking whether you're Dual-Booting or not :)

> No it's an upgrade, I started from 10.04 and kept upgrading, so it wasn't from a CD.
And this problem occurred right after the upgrade?
 
> Grub gives me options to chose which kernel I want to boot with or Vista, I really have never tried choosing anything other than the standard first choice. But usually it takes 5 seconds to choose the highlighted selection by default.1- What exactly happens when you select the latest Kernel? does your PC stop at that point? or it's just a matter of delay?

2- Could you please select another Kernel and see what will happen?
Just select another entry (2.6.38-8-generic for example).

---

### Post by decrepit on 2011-09-14
> **Gaygerbil said:**
> >>>>>>

Where can I find this quiet splash option?


Don't forget to update grub as instructed on the top line.

/etc/default/grub

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR="Red"]#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600x32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

