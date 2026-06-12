---
title: "boot menu disappeared after Starting ubuntu problem fixed"
date: 2011-07-19
forum: General Help
---

### Post by herwin on 2011-07-19
I recently installed Linux on a new computer. 

I started up with a boot menu. The options were: 

1. linux 2.6.38-10-generic-pae
2. the same but recovery mode
3. previous Linux versions
followed by the two mem tests

I always used the first option.

Earlier today something went wrong (I don't know what) when I shot down the computer. After that Ubuntu would not start anymore. I would get the boot menu, choose the first option and after a few seconds the screen went black and nothing more happened.

When I chose the recovery mode I went into another menu which first option was to continue normal boot process (I can't remember the other options). The arrow keys did not work to choose another options and after a few seconds the boot proces was continued and the same problems occured as described above.

When I chose the 3rd option 4-5 previous ubuntu versions were listed. The first 3 had the same problem as above but the 4th worked. 

In the terminal I typed: shutdown -rF now and the computer started up in 2.6.38-10-generic-pae. I have shutdown and then started again and it seems to work again.

The only difference: there is no bootmenu anymore.

Can anyone explain what happened? I realize I do not give a lot of details.

Is there anyway of getting the bootmenu back? In case there is a problem again it is helpful to be able to run an earlier version.

---

### Post by 2F4U on 2011-07-19
> **herwin said:**
> 

Can anyone explain what happened? I realize I do not give a lot of details.

Is there anyway of getting the bootmenu back? In case there is a problem again it is helpful to be able to run an earlier version.

Can you show us the content of your /etc/default/grub file?

There should be an option

GRUB_HIDDEN_TIMEOUT=0
If you want to see the boot menu, place a comment in front of this line.
Or change it to

GRUB_HIDDEN_TIMEOUT=5 GRUB_HIDDEN_TIMEOUT_QUIET=false  
and don't forget to do sudo update-grub[FONT=Verdana].[/FONT]

---

### Post by Mark Phelps on 2011-07-19
> **herwin said:**
> The only difference: there is no bootmenu anymore.
That's the NORMAL situation when only Ubuntu is installed on the PC.  It no longer shows a boot menu by default.

To see the boot menu (on demand), hold down one of the SHIFT keys when rebooting.

The edits provided will always show the boot menu from now on -- if that is what you want.

---

### Post by herwin on 2011-07-21
Thanks for the comments. It is all clear now.

FYI, here is the content of  /etc/default/grub  file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=20
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

