---
title: "list of services on boot"
date: 2011-07-23
forum: General Help
---

### Post by quequotion on 2011-07-23
I spent a few minutes googling this, but I am not even sure what to search for. I suspect I'm looking at part of **upstart**, but it could also be **sysvinit**, **plymouth** or something else entirely.

Every time I reboot, just between plymouth's splash screen and gdm loading, I am shown a list of services starting.

The list shows the names of the services and [**OK**] if they started sucessfully or [[COLOR="Red"]**fail**[/COLOR]] if they did not (only **apport** ever fails and only occasionally).

I don't need or want to see this list. It also interrupts the transition from Grub to GDM (the background color should be the same shade of purple from grub all they way to the desktop, but this list is presented as ordinary terminal output: white text on black background)

Is there any way to hide it?

---

### Post by ajgreeny on 2011-07-23
This list does not normally show at all.  Have you made any changes to your /etc/grub/default file where such things can be changed?

Here's what mine is like, though I've made a few changes to timeouts, and added the kernel option of **radeon.modeset=1** to the line that you may have edited.  The **quiet splash** is the part that may have disappeared in yours for some reason.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=1"[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by quequotion on 2011-07-25
> **ajgreeny said:**
> This list does not normally show at all.  Have you made any changes to your /etc/grub/default file where such things can be changed?


You probably mean **/etc/default/grub**...

I have made numerous, frequent changes.

I have not removed the parameters **quiet** or **splash**.

After each edit I make sure to **update-grub** and also **update-initramfs -u -k all**, just in case.

I have done a lot of tinkering because I use the proprietary nvidia drivers and plymouth for boot splash (eg, I'd like to have my cake and eat it too). Also, I have had various troubles with clocksources (affecting pulseaudio, etc). At the moment, I have it set to hpet and this seems to keep my computer out of chaos.

**/etc/default/grub**```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="clocksource=hpet quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_VIDEO_BACKEND=vbe


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by ajgreeny on 2011-07-25
Sorry!  Yes that was my typo.  However, I am even more sorry that the suggestion got you nowhere nearer to a solution.

---

### Post by quequotion on 2011-08-14
> **ajgreeny said:**
> Sorry!  Yes that was my typo.  However, I am even more sorry that the suggestion got you nowhere nearer to a solution.

Don't fret!

Good news and bad news:

I am no longer having this issue.

...because I had to build a new computer from scratch after coolant leaked into my CPU and I started with a fresh install of Natty this time...

---

