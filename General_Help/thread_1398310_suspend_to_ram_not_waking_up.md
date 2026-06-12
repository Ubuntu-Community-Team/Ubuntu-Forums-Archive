---
title: "suspend to ram not waking up"
date: 2010-02-04
forum: General Help
---

### Post by fiestytom on 2010-02-04
when I put my lappy to sleep, it looks as if it sleeps well....

the light blinks, just like when it did on windows when it slept

but when I try to wake it up, it powers up the fan and hdd and i see nothing on my screen, it doesn't even light up!!

I am always forced to do a hard reset

I followed a debug tutorial and got this out of it:

[    1.355059]   Magic number: 0:291:740
[    1.355065]   hash matches /build/buildd/linux-2.6.31/drivers/base/power/main.c:419

do I need to blacklist a driver or something?

thx

---

### Post by tgalati4 on 2010-02-04
What is the make and model of your laptop?  My crystal ball isn't working today.

In a terminal, post the output of:

cat /etc/default/acpi-support

---

### Post by fiestytom on 2010-02-04
I am using an HP pavilion ze4200 Model: XT236

Here is the output:

# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=false

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf.

---

### Post by fiestytom on 2010-02-04
bump?

---

### Post by tgalati4 on 2010-02-05
Try changing this switch:

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

Just uncomment it by removing the #.

In a terminal:

gksudo gedit /etc/default/acpi-support

Then reboot and try to sleep and wake.  If that doesn't work then:


# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf.
__________________

In a terminal:

sudo apt-get install laptop-mode-tools

Then output the following:

cat /etc/laptop-mode/laptop-mode.conf

You will have to do some work on your part to get sleep to work correctly.  It works out of the box on some machines.  On other machines, it requires tweaking.

---

### Post by bama7474 on 2010-02-20
What if no file or directory is indicated for acpi-support?  I have the same suspend issue and have tried to edit that file but there was no such file.

Running UNR 9.10 (Karmic) on a Toshiba NB305 -N410BL...Blank screen when lid is closed works but doesn't save on batt usage.  Let me know if there is any information you'd like to see on my system to help fix this problem, thank.

---

