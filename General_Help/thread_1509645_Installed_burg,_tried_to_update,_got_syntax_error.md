---
title: "Installed burg, tried to update, got syntax error"
date: 2010-06-14
forum: General Help
---

### Post by Deldo on 2010-06-14
Hi.

I just installed BURG and the installationguide told med to run sudo update-burg. When I do that, I get this message:
/etc/default/burg: 7: Syntax error: "(" unexpected

On another page, in the comments, I found out that deleting a line in the /etc/default/burg can fix it. But my problem is that I don't now which line. Could anyone tell me? 

My guess is about line number seven, but as I'm saying, I'm not sure. :-)
Here are the document:
# If you change this file, run 'update-burg' afterwards to update
# /boot/burg/burg.cfg.

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="sudo burg-install "(hd0)""
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
#GRUB_SAVEDEFAULT=true

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# In the boot menu, use hotkey 'r' to popup a resolution selection menu.
GRUB_GFXMODE=saved

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

# GRUB_THEME's value can be 'saved' or a specific BURG theme name, you can also
# set it to the pathname of a GRUB2 theme file.
# In the boot menu, use hotkey 't' to popup a theme selection menu
GRUB_THEME=saved

# GRUB_FOLD's value can be 'saved', 'true' or 'false'.
# In the boot menu, use hotkey 'F7' to show the full list, 'f' to toggle
# between folding modes.
GRUB_FOLD=saved

# Add user with burg-adduser, then use GRUB_USERS to config authentication.
# The following example means user1 can boot Ubuntu, no password is needed to
# boot Windows, user1 amd user2 can boot other OS. Superusers can boot any OS
# and use hotkeys like `c' to enter console mode.
#GRUB_USERS="*=user1,user2:ubuntu=user1:windows="

# For a complete list of supported variables, refer to this wiki page:
# [http://code.google.com/p/burg/wiki/ConfigurationVariables](http://code.google.com/p/burg/wiki/ConfigurationVariables)

---

### Post by sauma on 2010-06-16
Yours:
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="sudo burg-install "(hd0)""   <---problem.
GRUB_CMDLINE_LINUX=""

Mine:
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=

---

### Post by cneha on 2010-06-16
use sudo burg-install "(hd0)"
provide a space between install an ".
and the command will work.:guitar:

---

### Post by dcstar on 2010-06-16
> **sauma said:**
> Yours:
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="sudo burg-install "(hd0)""   <---problem.**
GRUB_CMDLINE_LINUX=""

Mine:
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
GRUB_CMDLINE_LINUX=

Exactly, someone who didn't understand what they were doing put rubbish in that field.

---

