---
title: "latest updates broke"
date: 2011-02-01
forum: General Help
---

### Post by buntunub on 2011-02-01
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up grub-pc (1.98-1ubuntu10) ...
/etc/default/grub: 18: Syntax error: newline unexpected
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by TeoBigusGeekus on 2011-02-01
```
gedit /etc/default/grub
```
Can you post us the contents of the file?

---

### Post by buntunub on 2011-02-01
Sure

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1600x900-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1600x900-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFX_PAYLOAD_LINUX=keep
```

---

### Post by Bucky Ball on 2011-02-01
Do you do 'sudo apt-get update' first?

You might try:

```
sudo apt-get autoremove
```

... and see if it offers further info.

---

### Post by buntunub on 2011-02-01
To fix this I commented out the line -

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
**GRUB_GFXMODE=>>1600x900-24<<**
```

This allowed me to continue with the upgrade at which point I got a grub configure screen complaining about a missing MBR uuid or somehow it got changed so I had to select the MBR manually and then it proceeded to complete the update-grub operation and overwrote my old grub.cfg file.

Its weird. What did todays updates do that required grub to have to be reconfigured and my MBR uuid's changed? What was the last kernel update all about that hosed up all my audio?.. What the heck are you guys doing over there in Ubuntuland?

---

### Post by Bucky Ball on 2011-02-01
You are using Kubuntu 10.04 Lucid Lynx and not 10.10?

---

### Post by buntunub on 2011-02-01
> **Bucky Ball said:**
> You are using Kubuntu 10.04 Lucid Lynx and not 10.10?

Yes.

---

