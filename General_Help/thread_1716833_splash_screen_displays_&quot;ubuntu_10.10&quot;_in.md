---
title: "splash screen displays &quot;ubuntu 10.10&quot; in terminal/dos text"
date: 2011-03-29
forum: General Help
---

### Post by lostmonster on 2011-03-29
Weird problem.  I'm running on a freshly installed win7 (first) ubuntu dualboot system.  Splash screen was absolutely perfectly dandy upon fresh install.  I updated ubuntu, then the problem occurred. 

I assume its a video card problem.  nVidia GeForce 9800 GTX+ is what I have in there.  Drivers installed fine and everything, don't know if this is an easy fix or not.

What's weird is that the animated dots remain, just in a lower resolution.

4gb RAM
intel i7 860
evga P55 SLI mobo

Didn't mess around much with ubuntu before the problem occurred.  I essentially let the updates run and then I restarted right back into Ubuntu and saw the new downgraded splash screen.

I'm new to ubuntu and terminal commands so if you suggest a terminal command fix, please be logical in your step by step fix suggestion.

---

### Post by stinkeye on 2011-03-29
The fix for text only showing in plymouth is to add 
```
GRUB_GFXPAYLOAD_LINUX="[COLOR="Magenta"]1680x1050[/COLOR]"
```
([COLOR="#ff00ff"]Using your native resolution[/COLOR].)

to (in terminal)
```
gksudo gedit /etc/default/grub
```

Save and close file.

and then run (terminal)
```
sudo update-grub
```


eg my /etc/default/grub file
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
**GRUB_GFXPAYLOAD_LINUX="1680x1050"**
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

---

### Post by m_duck on 2011-03-29
KMS is needed for the high resolution splash/frame buffer. Unfortunately, I don't think the proprietary nvidia drivers support this, only the open source nouveau ones. This is why after updating and installing the official drivers, you lost the high resolution splash.

---

### Post by lostmonster on 2011-03-29
> **m_duck said:**
> KMS is needed for the high resolution splash/frame buffer. Unfortunately, I don't think the proprietary nvidia drivers support this, only the open source nouveau ones. This is why after updating and installing the official drivers, you lost the high resolution splash.

This makes sense since I'm on a 1920x1200 monitor.

---

### Post by lostmonster on 2011-03-29
> **stinkeye said:**
> The fix for text only showing in plymouth is to add 
```
GRUB_GFXPAYLOAD_LINUX="[COLOR=Magenta]1680x1050[/COLOR]"
```([COLOR=#ff00ff]Using your native resolution[/COLOR].)

to (in terminal)
```
gksudo gedit /etc/default/grub
```Save and close file.

and then run (terminal)
```
sudo update-grub
```
eg my /etc/default/grub file
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
**GRUB_GFXPAYLOAD_LINUX="1680x1050"**
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

I'll try out the code you posted.  However, the last time grub updated, I  got a grub malfunction and had to wipe my harddrive.  Do you guarantee  that not to happen? (haha)

also, I'm new to terminal commands.  You suggest I enter in terminal  commands, but I don't know when I should be pressing enter to put in a  command.

---

### Post by stinkeye on 2011-03-29
> **lostmonster said:**
> I'll try out the code you posted.  However, the last time grub updated, I  got a grub malfunction and had to wipe my harddrive.  Do you guarantee  that not to happen? (haha)

also, I'm new to terminal commands.  You suggest I enter in terminal  commands, but I don't know when I should be pressing enter to put in a  command.

No guarantees or refunds. :-\"
Just copy and paste in the command and hit enter.
If it's a sudo command it will ask for your password.
When entering password you wont see any recognition, like asterisks, that your password is being entered.
Hit enter after putting in password.

---

### Post by lostmonster on 2011-03-29
Yeah, this fix didn't work.  I edited the grub resolution to 1920x1200 and the splash screen remained the same low res nonsense.  Is there a resolution limit to which I can set it?

---

### Post by matt_symes on 2011-03-29
Hi

You can get Plymouth to use a different frame buffer with

```
sudo bash -c "echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash"
sudo update-initramfs -u
```

Enter your password. It will not be echoed to the screen.

Does that fix it ?

Kind regards

---

