---
title: "grub2 boot menu not showing"
date: 2010-11-24
forum: General Help
---

### Post by Mr Nemo on 2010-11-24
After upgrading to 10.10 the grub boot menu stopped showing up. I made a custom menu in grub.d and update grub finds everything, but when I restart my system the boot menu never shows. I should have two kernels. How do I get the boot menu to show every time I restart my system?

---

### Post by sikander3786 on 2010-11-24
> **Mr Nemo said:**
> After upgrading to 10.10 the grub boot menu stopped showing up. I made a custom menu in grub.d and update grub finds everything, but when I restart my system the boot menu never shows. I should have two kernels. How do I get the boot menu to show every time I restart my system?
Please post the output of

```
cat /etc/default/grub
```

---

### Post by Mr Nemo on 2010-11-24
Here ya go...

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

### Post by Quackers on 2010-11-24
Do you have just the one installation (with 2 kernels) or 2 installations?

---

### Post by Mr Nemo on 2010-11-24
One install with two kernels

---

### Post by Quackers on 2010-11-24
The default behaviour for grub2 is to hide the grub menu when there is only one Linux installation. To show the grub menu you can hold down the shift key during boot.
Was this not the case previously for you?

---

### Post by Mr Nemo on 2010-11-24
I did have a windows OS installed previously, but got rid of it when I upgraded to 10.10. I guess that's the reason. Is there any way to have the grub2 menu show every system boot even though I only have one OS installed?

---

### Post by Quackers on 2010-11-24
I'm not sure there is.
Maybe have a look in this thread and see if anything jumps out at you :-)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by sikander3786 on 2010-11-24
Edit your /etc/default/grub and make a change.

```
gksudo gedit /etc/default/grub
```

Comment this line with a # at the beginning.

```
GRUB_HIDDEN_TIMEOUT=0
```

So it looks like,

```
#GRUB_HIDDEN_TIMEOUT=0
```

Save, close and exit. Run update-grub

```
sudo update-grub
```

Reboot and let us know about your progress.

Good Luck!

---

### Post by garvinrick4 on 2010-11-24
#Run this in a terminal and will show you what your menu looks like that is not showing:```
grep menuentry /boot/grub/grub.cfg
```# I do believe quackers is right with one install it defaults to booting into OS without showing menu. Below is from :[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 
**GRUB_HIDDEN_TIMEOUT=0**  on single operating system computers. 

[LIST]
[*]No menu is displayed. The system is immediately booted to the default OS.
[*]This is the default setting with only one identified operating system.
[LIST]
[*]To display the menu under this condition, place a **#** symbol at the start of the line and ensure the GRUB_TIMEOUT setting is a positive integer.
[/LIST]
 
[*]If the value is set to **0**, a *keystatus* check is performed to determine if the *SHIFT* key is depressed. If GRUB 2 determines the *SHIFT*  key is depressed during the boot process, the menu will be displayed.  This gives the user a method of interrupting an automatic boot which  would normally not display the menu.
[/LIST]
```
gksudo gedit /etc/default/grub
```##Make changes to this file as described above and save and:
```
sudo update-grub
```

---

### Post by Mr Nemo on 2010-11-24
Yup that worked, just found it on Google too.

Thanks Sikander!

---

### Post by Quackers on 2010-11-24
I forgot about that :-)
Nice one Sikander3786 and garvinrick4

---

