---
title: "Error Message after Bootloader"
date: 2010-06-10
forum: General Help
---

### Post by OB099 on 2010-06-10
Hi, 
when i select Ubuntu from the boot menu (I'm dual Booting with win7) I get an error message see the attached file for the message. it then takes about 3-5 minutes until i get to the Ubuntu log in screen 

any help would be much appreciated 

Cheers

OB

---

### Post by oldos2er on 2010-06-10
Which version of Ubuntu are you using?

---

### Post by OB099 on 2010-06-11
Ubuntu 10.4

---

### Post by philinux on 2010-06-11
> **OB099 said:**
> Ubuntu 10.4

Have you modified grub manually or with startupmanager?

---

### Post by drs305 on 2010-06-11
The reason for the "error" message is that you most likely have "vga=788" as an option on the GRUB_CMDLINE_LINUX_DEFAULT= or GRUB_CMDLINE_LINUX= line in /etc/default/grub.

The way to remove the message is to remove the vga reference from the line. The message also indicates that you use the 'gfxpayload' line to set the graphics mode. There has been mixed success with using gfxpayload settings for your *post-boot* screen resolutions and I will leave that for later or others to discuss.

For just the Grub2 menu resolution, uncomment and use this entry in /etc/default/grub:
> GRUB_GFXMODE=640x480
You can find out the resolutions supported by entering the command line from the Grub2 menu (press "c") and running the command "vbeinfo". It will list the resolutions which you can use in the above setting.

---

### Post by OB099 on 2010-06-11
[[COLOR=#D40000]**philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083")- I have modified via the startup manager but the problem persttied before i tried to changed anything. 

When i open/etc/default/grub i cant edit it i only can read. how do i edit? and what excatly do i need to change see below:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=2
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=788"

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

---

### Post by oldfred on 2010-06-11
You have to use sudo and for graphical applications gksudo.

gksudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX=" [COLOR=Red]vga=788[/COLOR]"

Delete the vga entry.

"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

Says 788 is 800x600 16 bit.

---

### Post by OB099 on 2010-06-11
ok i have now deleted the VGA reference after working out how to get in at root. i still have an error message after i selected Ubuntu on the boot menu see attached for my new error message 

any more help would be cool

---

### Post by oldfred on 2010-06-11
That is not an error message. I see that when I boot. Does it continue or did you not give it a chance.

If you want to see all the detail remove the quiet splash from the linux line in the menu. Use e to get to edit and change the line then control x to boot.

---

### Post by GeekGirl1 on 2010-06-15
oldfred - Thanks. Your instructions helped me. Perhaps OB099 has not run update-grub?

I was getting the same error, but with VGA=795. Your link to 
[Boot Windows first in GRUB... ("VGA Deprecated" Message on Boot)]("http://ubuntuforums.org/showthread.php?t=1453524") had the info I needed, including a link to the GRUB2 docs.

First, edit the grub file:

gksudo gedit /etc/default/grub

My file below. I like to add comments and preserve the original commands (start line with #, which converts command to comment) in case I need to revert.

This section removes the old command:

#deprecated
#GRUB_CMDLINE_LINUX=" vga=795"
GRUB_CMDLINE_LINUX=""

This section sets the VGA mode to 1600x1200. It looks like 1280x1024, so I'll have to double-check this later.

# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1600x1200

This section tells GRUB to not show the splash screen, just the text.

#Comment out below to see text processing, just "splash" will show condensed text + splash
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

#Comment out below to see text processing, just "splash" will show condensed text + splash
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

#deprecated
#GRUB_CMDLINE_LINUX=" vga=795"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1600x1200

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```Save changes.

Update GRUB:

sudo update-grub

It should do some stuff, then say "Done."

Restart to check your work.

---

