---
title: "Text Terminal Unreadable"
date: 2010-07-09
forum: General Help
---

### Post by Gibbs on 2010-07-09
My terminal text is unreadable. Where as the default output would usually fill half the screen it probably fills around 1/20th now. Basically it looks like the text is 1px in size.

I was about to install a graphics driver (nvidia) but doh I can't see what I'm typing... I can't start gdm even after memorising the process of logging in and starting gdm (I think gdm is failing to start anyway) :P

I'm using the default xorg.conf provided with the LiveCD;
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Here's my GRUB config
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I'm pretty stuck so any suggestions appreciated. I'm using Lucid btw.

Cheers

---

### Post by gordintoronto on 2010-07-09
Can you click the button to run the terminal in full-screen?

Don't use the terminal to install a graphics driver. Administration/Hardware Drivers is the place to go.

---

### Post by Gibbs on 2010-07-10
> **gordintoronto said:**
> Can you click the button to run the terminal in full-screen?

Don't use the terminal to install a graphics driver. Administration/Hardware Drivers is the place to go.

I couldn't see anything and had to use the terminal (as GDM wouldn't start). I sorted it by changing the vga setting in GRUB and then used jockey-text to install my graphics card.

Thanks

---

