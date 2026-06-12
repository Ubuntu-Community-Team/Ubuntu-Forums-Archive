---
title: "Dual Booting"
date: 2010-10-29
forum: General Help
---

### Post by ramhanuman on 2010-10-29
I did a fresh installation of Ubuntu 10.10 maverick meerkat, and then installed windows 7 on another partition afterwards. Everytime i boot up now it shows me the grub menu to ask me which os to load with 10 seconds to choose or else it picks ubuntu. How do i make it so that it boots by default to ubuntu without showing the menu but shows the menu when i hold shift so i can boot into windows whenever i need?

Thanks.

---

### Post by 666f6f on 2010-10-29
Hi there, you may want to check [this thread]("http://ubuntuforums.org/showthread.php?t=1302743").

---

### Post by ramhanuman on 2010-10-30
This is my grub.cfg:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT='Ubuntu, with Linux 2.6.35-22-generic-pae'
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=6
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=775 quiet"

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
```

I've tried everything, i looked through that thread even. But it either doesn't show up at all (which is what I want) but it doesn't open up when i hold shift either. When I hold shift it says grub is loading and then nothing happens. OR it shows the menu for the number of seconds i put next to grub_timeout, (which I don't want).

I just want it to boot ubuntu everytime unless i manually open the menu with shift to boot windows

---

### Post by Quackers on 2010-10-30
You can go to System > Admin > Synaptic Package Manager and in the search box enter Startup Manager. Choose to install it then go to System > Admin > Startup Manager where you can change your default operating system.
If you don't want to see the menu at all you can change GRUB_TIMEOUT= to 0

---

### Post by joshruehlig on 2010-10-30
> **ramhanuman said:**
> This is my grub.cfg:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT='Ubuntu, with Linux 2.6.35-22-generic-pae'
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=6
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=775 quiet"

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
```

I've tried everything, i looked through that thread even. But it either doesn't show up at all (which is what I want) but it doesn't open up when i hold shift either. When I hold shift it says grub is loading and then nothing happens. OR it shows the menu for the number of seconds i put next to grub_timeout, (which I don't want).

I just want it to boot ubuntu everytime unless i manually open the menu with shift to boot windows


	
To not have grub show up unless called to run
sudo gedit /etc/default/grub

change grub timeout to 0 and save file

run
sudo update-grub

It should now work

---

### Post by ramhanuman on 2010-10-30
> **joshruehlig said:**
> To not have grub show up unless called to run
sudo gedit /etc/default/grub

change grub timeout to 0 and save file

run
sudo update-grub

It should now work

I did that, and when I held shift during startup it says "Loading Grub..." and then goes away and nothing happens. Why is it doing that?

Btw, i'm using a Dell Latitude D830

---

### Post by joshruehlig on 2010-10-30
> **ramhanuman said:**
> I did that, and when I held shift during startup it says "Loading Grub..." and then goes away and nothing happens. Why is it doing that?

Btw, i'm using a Dell Latitude D830

did it boot to ubuntu at all?

Thats why I said until you call grub (not just hold shift) cause Im not sure what exactly the button is, sorry. Might be esc...

---

### Post by Quackers on 2010-10-30
Apologies ramhanuman, this is a quote from drs305's Grub Basics guide

# Caution: Holding down the "SHIFT" key will not display the menu if "GRUB_TIMEOUT=" is set to "0" .

So set it to 1 perhaps.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ramhanuman on 2010-10-31
Setting it to anything above 0 makes it show without me calling it so that didn't do what I needed. Is there really not a way for grub to show only when called?

---

