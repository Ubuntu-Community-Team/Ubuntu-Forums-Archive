---
title: "complete re-install of grub2"
date: 2010-02-01
forum: General Help
---

### Post by bowens44 on 2010-02-01
Is there a way to completely re-install grub2 , including re-installing everything in /etc/grub.d?

I am having a minor problem with grub2 that is really annoying me.

I want to see the boot process. This used to work. Now instead of seeing the boot process I see nothing but a black screen until the login box appears.

I want to get back to all default settings for grub2.

thanks

---

### Post by Leppie on 2010-02-01
if you want to see the output during boot, you don't have to re-install grub2.
open your grub defaults file with a text editor:
```
gksudo gedit /etc/default/grub
```
remove "quiet" from the variables "GRUB_CMDLINE_LINUX_DEFAULT" and "GRUB_CMDLINE_LINUX"
save and exit the file, then run update-grub:
```
sudo update-grub
```

you should now have a verbose output during boot

---

### Post by bowens44 on 2010-02-01
> **Leppie said:**
> if you want to see the output during boot, you don't have to re-install grub2.
open your grub defaults file with a text editor:
```
gksudo gedit /etc/default/grub
```
remove "quiet" from the variables "GRUB_CMDLINE_LINUX_DEFAULT" and "GRUB_CMDLINE_LINUX"
save and exit the file, then run update-grub:
```
sudo update-grub
```

you should now have a verbose output during boot

I already did this. This is why I want to re-install. I have tried everything to get back to verbose output (I had it at one point). I have had no luck. Something is wrong and I haven't been able to pin point it despite hours of googling and reading and re-reading every guide I could find. It worked out of the box. Now it doesn't work. 

I want to completely re-install. 

Here's my /etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
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

### Post by Leppie on 2010-02-01
to get a complety clean grub2:
```
sudo apt-get purge grub grub-pc grub-common
sudo rm -rf /boot/grub
sudo apt-get install grub-pc grub-common
```

---

