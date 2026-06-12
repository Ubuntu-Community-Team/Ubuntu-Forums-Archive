---
title: "bootable profiles &amp; disabling gdm / nvidia graphics chips?"
date: 2011-05-27
forum: General Help
---

### Post by as2003 on 2011-05-27
I have a Zotac Mag-ION - a tiny little "nettop" that runs headless 99% of the time, downloading legal ;) torrents, serving webpages, running cronjobs and the like. Generally being very useful.

It has a decent onboard graphics chips included.

Because I wanted to sometimes plug the thing into my TV, I installed Ubuntu Desktop (10.04 LTS), instead of Server.

The problem is that, as I say, 99% of the of the time it's running headless, and gnome will be consuming valuable resources and using the graphics chips.

I want to have two profiles that I can boot into. One that doesn't load gdm and perhaps disables all the graphics chips to keep the temperature / energy usage down.

The second one runs gdm as usual.

Is this possible? I don't really know what I'm talking about.

Cheers!

---

### Post by lmarmisa on 2011-05-27
If you wish to start your system in text mode, edit the file **/etc/default/grub**, comment the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** and insert a new line **GRUB_CMDLINE_LINUX_DEFAULT="text"**:

```

sudo gedit /etc/default/grub

```

These are the new contents of the file **/etc/default/grub**

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR="RoyalBlue"]#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="text"[/COLOR]
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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

```

Save & exit.

Then type the command:

```

sudo update-grub

```

The system will start in text mode after these changes.

If you wish to start **gdm**, type this command:

```

sudo service gdm start

```

---

### Post by as2003 on 2011-05-27
thanks very much, that's perfect!

That's saved me 100MB of RAM on a 1GB box.

I'm also going to try disabling the graphics card via the bios.

---

