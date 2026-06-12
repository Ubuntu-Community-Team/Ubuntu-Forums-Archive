---
title: "Bootmbr Problem"
date: 2011-07-17
forum: General Help
---

### Post by cclloyd9785 on 2011-07-17
When I installed, I accidently installed the bootloader to the mbr of my hard drive instead of the Ubuntu partition.  Is there any way that I can make it so that it shows the Windows bootloader first? (Windows partition is set to active, Windows is on hdd0,sda1, Ubuntu is on hdd0,sda4 with sda5 as swap)

---

### Post by lmarmisa on 2011-07-17
What Windows and Ubuntu versions are you using?.

---

### Post by Gremlinzzz on 2011-07-17
if you want windows to be default startup OS,just install startup-manager 
[http://ubuntuforums.org/attachment.php?attachmentid=197703&stc=1&d=1310954750](http://ubuntuforums.org/attachment.php?attachmentid=197703&stc=1&d=1310954750)
then choose windows as default.

---

### Post by cclloyd9785 on 2011-07-17
Its not that I want windows to be the default OS, but I want the bootloader for Windows to show first.  And Im using Windows 7 and Ubuntu 11.04 both x64.

---

### Post by lmarmisa on 2011-07-17
> **cclloyd9785 said:**
> Its not that I want windows to be the default OS, but I want the bootloader for Windows to show first.  And Im using Windows 7 and Ubuntu 11.04 both x64.

If both operating systems Windows 7 and Ubuntu 11.04 are stored in the same hard drive, you have to use GRUB as first loader. Windows 7 bootloader is unable to boot into Ubuntu.

I like a Grub configuration that remembers the last user selection and define it as default option until the user selects a different one.

If you wish to use this option, open a terminal and type these commands:

```

sudo cp /etc/default/grub /etc/default/grub.old
sudo gedit /etc/default/grub

```Now change the lines marked in blue:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

[COLOR=Blue]GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true[/COLOR]
[COLOR=Blue]GRUB_HIDDEN_TIMEOUT=0[/COLOR]
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=Blue]GRUB_TIMEOUT=5[/COLOR]
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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```Save & Exit.

Type this command:

```

sudo update-grub

```Reboot your system and select windows as the system for booting in the Grub menu. If so, Windows will be the default system until your chage to Ubuntu and so on.

Best regards,

Luis

---

