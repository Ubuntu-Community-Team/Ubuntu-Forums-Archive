---
title: "i deleted my /etc/default/grub by accident , can anyone upload it for me please?"
date: 2012-02-10
forum: General Help
---

### Post by r9tysix on 2012-02-10
Hello,
I'm using ubuntu 11.10 amd
I deleted my /etc/default/grub by accident
Can anyone upload it for me?
Thank you.

---

### Post by r9tysix on 2012-02-10
my thread is falling down and no reply

anw i have another question
2.14 Ubuntu 11.04[COLOR=Red] (Natty Narwhal)[/COLOR]
2.15 Ubuntu 11.10 [COLOR=Red](Oneiric Ocelot)[/COLOR]
2.16 Ubuntu 12.04 LTS[COLOR=Red] (Precise Pangolin)[/COLOR]

who are those (marked in red)?

---

### Post by lisati on 2012-02-10
If you have a LiveCD, you *might* be able to do some repair work on grub from there.

As for the names you've highlighted in red, those are "code names" for various releases of Ubuntu.

---

### Post by JRV on 2012-02-10
Here is mine, I hope it helps.

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="splash quiet"

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

The names in red are the names of the releases.
11.04 was released in the 4th month of 2011. The names are an adjective followed by an animal in alphabetical order. The next release is 12.04 Precise Pangolin in April of 2012. The October 2012 release will have an adjective and animal name that begin with Q.

---

### Post by savanna on 2012-02-10
% cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=6
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
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

