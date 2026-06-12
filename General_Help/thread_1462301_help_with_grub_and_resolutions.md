---
title: "help with grub and resolutions"
date: 2010-04-25
forum: General Help
---

### Post by FreezWay on 2010-04-25
I need help getting my /etc/default/grub file to set my resolution for my tty1-6 to 1920x1080. I got grub at that resolution, but the tty's remain the same. Here are the content of the file currently.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=769"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1080
GRUB_PLAYLOAD=keep
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

also what does GRUB_CMDLINE_LINUX=" splash vga=769" do? if I dont want a splash screen how to I do that?

EDIT: I took out the splash and it boots faster. i also took out vga-769

---

### Post by quixote on 2010-04-26
I may not be understanding something, but I'm pretty sure grub settings are used only by grub.  If you want your ttys at a given resolution (i.e. I assume you don't mean anything GUI-related, since that would be in xorg.conf, and so on), then I'd expect that to be somewhere in the OS itself (setenv maybe??), not in the bootloader.

---

### Post by towheedm on 2010-04-27
> **FreezWay said:**
> I need help getting my /etc/default/grub file to set my resolution for my tty1-6 to 1920x1080. I got grub at that resolution, but the tty's remain the same. Here are the content of the file currently.

"VGA=xxx" was used to set the linux framebuffer's video mode.  It is now depracated and replaced with GRUB_GFXMODE=.

Also, it's **[COLOR=Blue]set gfxpayload=keep[/COLOR]** and not **[COLOR=Red]GRUB_PLAYLOAD=keep[/COLOR]** as is in your file unless of course you've set it up as a variable in your /etc/grub.d/00_header configuration file.  If it's a genuine mistake then [COLOR=Blue]**set gfxpayload=keep**[/COLOR] must be placed in your 00_header file just before **[COLOR=Blue]insmod gfxterm[/COLOR]**.

Could you paste the contents of your /etc/grub.d/00_header file?  This is pretty simple to fix.

---

### Post by FreezWay on 2010-04-27
ok, i'll try that, if it doesn't work I'll paste the contents

---

### Post by jbatista on 2010-05-25
[LIST=1]
[*]Leave /etc/grub.d/00_header and /etc/grub.d/10_linux alone. Instead, work with the file /etc/default/grub . There is a commented line there for GRUB_GFXMODE, I recommend you leave the commented line and put your own GRUB_GFXMODE. Also set a GRUB_GFXPAYLOAD_LINUX=keep line; see the 10_linux file I mentioned above.
[*]I've set GRUB_GFXMODE=1280x1024x24 (notice the third number, which means it's a 24-bit color-depth mode). I've also set GRUB_GFXPAYLOAD_LINUX=keep. Both in /etc/default/grub.
[*]Run update-grub (as root, of course, or by sudo'ing it). For good measure, if you're in Lucid use update-grub2; don't worry, it itself calls update-grub instead (I suppose this will be replaced in future releases?)
[/LIST]

HTH.

---

