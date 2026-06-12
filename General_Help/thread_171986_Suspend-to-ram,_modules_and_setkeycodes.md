---
title: "Suspend-to-ram, modules and setkeycodes"
date: 2006-05-07
forum: General Help
---

### Post by Dogmeat on 2006-05-07
Hello, I got suspend-to-ram (S3 from now on) working in Breezy but I'm having a few annoyances. Maybe someone knows how to fix some of these?

After waking up from a S3, the terminals (VC's) get all garbled up, but they're readable (my guess is they're running at the X resolution. I have a Nvidia card and am running the proprietary module). Would love a fix for this.

Now, the most annoying one is setkeycodes. I made a boot script for my keyboard which sets a few missing keycodes. As you know, setkeycodes has to run from a VC, after a resume from S3 mine are garbled but readable, I run the script and setkeycodes gives these errors: 

```
KDSETKEYCODE: Invalid argument
failed to set scancode 92 to keycode 180

```

I think I should reload or whitelist some module after the S3 but I can't figure out which one setkeycodes depends on, any tips?

Last but not least, Ubuntu doesn't autodetect my TV tuner card, so I have to manually load a module with some parameters every boot. The acpi scripts just reload the module with the default parameters after a S3 resume, so I have to remove and re-insert it with the correct parameters every time the computer wakes up. I haven't found how to add the module parameters in the acpi-support script. By the way, here is mine:

```

# Uncomment the next line to enable ACPI suspend to RAM
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
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
#DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="mysql"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```

One last thing, which is not that important but would be nice to have: I can wake up the computer with a left mouse click or the power button, but I would like to use the wake-up button on the keyboard. I suppose this isn't be hard to do but I just don't know how to! Thank you for your time and help!

---

### Post by Dogmeat on 2006-05-10
About the terminal getting garbled, I believe the problem is it is using the X resolution which is much higher, since when I use lower resolutions in X the terminal gets clearer, how do you manually change a VC resolution? I didn't find anything about in setterm or stty's manual.

Since no one answered in a couple of days, should I submit these bugs to launchpad?

---

