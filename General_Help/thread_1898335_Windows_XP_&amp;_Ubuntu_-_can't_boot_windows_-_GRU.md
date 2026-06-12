---
title: "Windows XP &amp; Ubuntu - can't boot windows - GRUB problem?"
date: 2011-12-21
forum: General Help
---

### Post by llygad ebrill on 2011-12-21
I've installed ubuntu on my PC, which used to run windows XP (I installed 11.10, but I'm using LXDE rather than the resource-heavy unity desktop environment) - my intention was to be able to use it as a dual boot, but I can't seem to access windows at all now!

I can see the windows partition from ubuntu, everything seems fine there, but when I boot the PC, there is no option to choose OS. Holding down shift during the BIOS brings up "LOADING GRUB", but grub does not appear, rather the screen goes off for several seconds and then the ubuntu 11.10 splash screen appears (where I can choose the desktop environment but not the OS). Could this be a problem with GRUB, and if so any idea how to fix it?

I want to continue using ubuntu as my main OS, however there are some programs I have installed in XP that I really need access to from time to time, so I'd really like to regain access to it.

I've tried using the windows XP install CD, but I'm nervous that I'll inadvertently wipe ubuntu so I'd like to check GRUB is working correctly first.

I've attached the list of partitions in case that helps.

Many thanks,

Robin

---

### Post by BC59 on 2011-12-21
First check the Grub menu:

```
gksu gedit /etc/default/grub
```

post the result here

---

### Post by llygad ebrill on 2011-12-21
many thanks for the fast reply. I get the following (doesn't make much sense to me at this stage TBH)

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=6
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

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

### Post by BC59 on 2011-12-21
Looks Ok

Now install the Boot-Repair tool. It's described how [here]("https://help.ubuntu.com/community/Boot-Repair")

Better install it in Ubuntu directly and not to a Live CD.
So open a terminal CTRL+ALT+T and run:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```

This is installing boot-repair to Ubuntu. Then execute boot-repair (search it on the dash). Then follow the instructions of the link.

---

### Post by llygad ebrill on 2011-12-21
many thanks for pointing me to boot-repair! but... still exactly the same problem. I've run boot repair and rebooted, but I still get the same behaviour ("GRUB LOADING" then black screen, then 11.10 splash). boot-repair gave me this, any clues there?
[http://paste.ubuntu.com/777232/](http://paste.ubuntu.com/777232/)

---

### Post by BC59 on 2011-12-21
Run

```
sudo update-grub
```

---

### Post by llygad ebrill on 2011-12-21
I've tried that, it didn't help. Exactly the same behaviour on boot.

update-grub gave the following output, in case it's relevant:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

---

