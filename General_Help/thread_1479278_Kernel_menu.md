---
title: "Kernel menu"
date: 2010-05-10
forum: General Help
---

### Post by Dave Otter on 2010-05-10
I have installed 10.04 from a downloaded cd but am unable to get any kernel menu either on pressing escape or shift!

      Any help appreciated.

          Many thanks.

---

### Post by mikewhatever on 2010-05-10
You'll need to edit a Grub config file in your Ubuntu installation, /etc/default/grub, to be precise. 
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

It should look something like this, and I highlighted the changes. When done editing, run **sudo update-grub**.

```
GRUB_DEFAULT=0
[COLOR="Orange"]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0
[COLOR="Orange"]#[/COLOR]GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=[COLOR="Orange"]-1[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

---

