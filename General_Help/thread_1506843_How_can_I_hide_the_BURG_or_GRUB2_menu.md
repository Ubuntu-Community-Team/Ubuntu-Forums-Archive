---
title: "How can I hide the BURG or GRUB2 menu?"
date: 2010-06-10
forum: General Help
---

### Post by cfalzone on 2010-06-10
I've been playing around with BURG lately and it's really making me happy.  I was trying it out because I don't like to see the text when dual-booting in the GRUB loader.

Anyway, BURG is very nice and all but I was wondering if there is a way that I may simply make the menu and countdown hidden.  Can this be done? I do recall reading that the GRUB2 developers made it so that GRUB2 would always be visible if the OS prober finds anything but 1 OS, but I only have Ubuntu installed anyway :p

What would be even better than GRUB2 would be if I could make the BURG menu hidden by default (instead of using GRUB2) and the only way to see the menu would be by holding "shift" at boot.  Any ideas?  My burg.txt file in /etc/default/burg looks like this (please note that while this is mostly default, I added the HIDDEN_TIMEOUT variables and I uncommented the rescue image probing):

```
# If you change this file, run 'update-burg' afterwards to update
# /boot/burg/burg.cfg.

GRUB_DEFAULT=0
GRUB_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT=true
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
GRUB_DISABLE_LINUX_RECOVERY="true"

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
# http://code.google.com/p/burg/wiki/ConfigurationVariables
```

---

### Post by apjone on 2010-06-10
Try Changing GRUB_TIMEOUT=10 to GRUB_TIMEOUT=0

---

### Post by cfalzone on 2010-06-10
Wonderful suggestion.  Only one question: won't this cause for a bit of an irritating flicker when the loader initializes?

I'm also wondering if this would prevent the loader from recognizing the "shift" key.

I'll try and post my success or failure.


[EDIT]

Yeah; no annoying flicker, but nothing happens when I press the "shift" or "esc" key at boot.  It simply boots.  I'd like this method if I could still access other OSes (if I were booting any haha)

---

### Post by apjone on 2010-06-10
Not sure to be honest. Just seems the quickest way to hide the menu.

---

### Post by drs305 on 2010-06-10
> **cfalzone said:**
> ... but nothing happens when I press the "shift" or "esc" key at boot.  It simply boots.  I'd like this method if I could still access other OSes (if I were booting any haha)

In the latest version of Grub2 (don't know about BURG) the keystatus check is dependent upon conditionals in /etc/grub.d/30_os-prober. One of the conditionals is:
> 
if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then

Since your setting for this variable is currently "true" and not "O" (zero), the keystatus check is omitted. (The rest of your existing choices meet the conditionals.)  Try changing the hidden timeout value to this in /etc/default/grub:
> GRUB_HIDDEN_TIMEOUT=0

Save the file, run "sudo update-grub" and see if you now have the ability to interrupt the boot with the SHIFT key.

---

### Post by cfalzone on 2010-06-10
Genius!  Instead of "shift" (in BURG) the key is "esc."

This leads to another question... the "esc" key causes an annoying beep when pressed during boot-time.  Can I change the keystatus key?  I couldn't find anything about it in the directory you mentioned.

---

### Post by dcstar on 2010-06-12
> **cfalzone said:**
> 
This leads to another question... the "esc" key causes an annoying beep when pressed during boot-time.

That is probably your BIOS.

---

