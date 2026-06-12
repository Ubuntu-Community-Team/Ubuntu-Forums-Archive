---
title: "reversing boot order 2 Ubuntus on GRUB 199"
date: 2011-11-05
forum: General Help
---

### Post by Finn bjerke on 2011-11-05
[FONT=Arial, Helvetica, Verdana, Sans Serif][SIZE=2][I]I have Ubuntu 10.10 and Ubuntu 11.10 on the same harddrive. GRUB 199  starts the Ubuntu 10.10 automaticly I want the Ubuntu 11.10 to start by default. I belive Ubuntu 11.10 is on dev1 while Ubuntu 10.10 is on dev. 

[/I][/SIZE][/FONT][FONT=monospace]sudo grub-install /dev/sda[/FONT]

The terminal order above worked on the machine where I have Linux mint and Ubutu dual booting, now Ubuntu starts first and linux mint later
[FONT=Arial, Helvetica, Verdana, Sans Serif][SIZE=2][I]
Is this the way to do it in Ubuntu 11.10 ?  [/I][/SIZE][/FONT]or should I  try this 
[FONT=monospace]sudo grub-install /dev/sda

Help much appreciated.

[/FONT]

---

### Post by drs305 on 2011-11-05
The "sudo grub-install /dev/sda" will make the OS you are currently running the controlling Grub 2 and should put it's OS at the top of the menu.

If you want the other OS to control and be first, boot into it and run the grub-install command.

If you want to keep the current OS as the controlling Grub but want the other OS to be the default selection (which can lead to some issues)  you can manually change the entry in /etc/default/grub using the instructions in the "Tasks" link in my signature line, or you can use an excellent GUI tool, Grub Customizer, to reorder the menu. There is a link for that in my signature line as well. I'd recommend using Grub Customizer for this latter setup.

---

### Post by dcstar on 2011-11-06
> **Finn bjerke said:**
> [FONT=Arial, Helvetica, Verdana, Sans Serif][SIZE=2][I]I have Ubuntu 10.10 and Ubuntu 11.10 on the same harddrive. GRUB 199  starts the Ubuntu 10.10 automaticly I want the Ubuntu 11.10 to start by default. I belive Ubuntu 11.10 is on dev1 while Ubuntu 10.10 is on dev. 

[/I][/SIZE][/FONT][FONT=monospace]sudo grub-install /dev/sda[/FONT]

The terminal order above worked on the machine where I have Linux mint and Ubutu dual booting, now Ubuntu starts first and linux mint later
[FONT=Arial, Helvetica, Verdana, Sans Serif][SIZE=2][I]
Is this the way to do it in Ubuntu 11.10 ?  [/I][/SIZE][/FONT]or should I  try this 
[FONT=monospace]sudo grub-install /dev/sda

Help much appreciated.

[/FONT]

Simply edit the /etc/default/grub file and change the "GRUB_DEFAULT" value to the appropriate menu item, then: ```
sudo update-grub
```

---

### Post by Finn bjerke on 2011-11-06
thank you. Now I start Ubuntu 11.10 directly no grub menu, so what do I do if I want to boot up Ubuntu 10.10

Here is the text in the grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
```

I tried this:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda6
done

```

---

### Post by dcstar on 2011-11-06
> **Finn bjerke said:**
> thank you. Now I start Ubuntu 11.10 directly no grub menu, so what do I do if I want to boot up Ubuntu 10.10


[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

---

### Post by Finn bjerke on 2011-11-06
[FONT=monospace]First this i Terminal 

sudo grub-install /dev/sda[/FONT]

Then This 
sudo update-grub
now it works. Ubutu 11.10 first and a few secunds to look on the dual boot menu. Im most gratefull

---

