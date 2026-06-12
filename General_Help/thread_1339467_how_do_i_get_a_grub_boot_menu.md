---
title: "how do i get a grub boot menu?"
date: 2009-11-27
forum: General Help
---

### Post by sdowney717 on 2009-11-27
one of my pc's just boots to ubuntu with no grub listing. ubuntu is the only os on it.
how do you setup a grub list?
I also dont have boot/grub/menu.lst
which i need, i want to add in a kernel parameter (memmap)when it boots

---

### Post by Arwen17evenstar on 2009-11-27
why do you need a boot menu, if ubuntu is the only OS on the computer?

---

### Post by sisco311 on 2009-11-27
Hold down the Shift key during the boot.

Karmic uses Grub2.

[uhelp]community/Grub2[/uhelp]

---

### Post by sdowney717 on 2009-11-27
i want to add a kernel parameter when it boots
memmap=54M$970M

how can it write this in somehow since grub menu.lst is no where to be found?

---

### Post by sdowney717 on 2009-11-27
I had no grub installed and it booted ubuntu. I installed grub2 and ran sudo update-grub, it claimed to find kernels etc, but on rebooting it just boots ubuntu.

so i installed grub and it removed grub2. How can i generate boot menu with grub?

---

### Post by sisco311 on 2009-11-27
> **sdowney717 said:**
> i want to add a kernel parameter when it boots
memmap=54M$970M

how can it write this in somehow since grub menu.lst is no where to be found?

Edit the /etc/default/grub file.

To unhide the menu set GRUB_HIDDEN_TIMEOUT_QUIET to false.

You can add your kernel parameter to the GRUB_CMDLINE_LINUX_DEFAULT line.

i.e.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=**false**
GRUB_TIMEOUT="**10**"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **memmap=54M$970M**"
GRUB_CMDLINE_LINUX=""


```

save the file and run:
```
sudo update-grub
```

EDIT: grub2 guides:
[thread=1195275]The Grub 2 Guide[/thread]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]

---

### Post by sdowney717 on 2009-11-27
thanks, sounds good, i will give it a try later

i have a 512mb stick with bad memory, memtest shows it from 971mb and up, so instead of tossing it i thought i would give it a try, block memory use from 970MB.

[http://ubuntuforums.org/showthread.php?t=860631](http://ubuntuforums.org/showthread.php?t=860631)

---

### Post by sdowney717 on 2009-11-28
I had to do a reinstall of the os.
When you put 
memmap=54M$970M into the kernel line with grub2 in /etc/default/grub and 
run the command sudo update-grub, 
it writes only 'memmap=54MM' into the kernel line.
SO, when you boot, all you get is 54megabytes of usable ram.

ok, thinking how to fix, so i boot the live cd, 
make /boot/grub/grub.cfg writable
edit /boot/grub/grub.cfg to take out 54MM and replace it with 54M$970M

restart and still no good. computer is beating on the hard drive and unresponsive.

so I just want to know what is wrong with the memmap command i tried?
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-03/msg05303.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-03/msg05303.html)

---

### Post by sisco311 on 2009-11-28
> **sdowney717 said:**
> I had to do a reinstall of the os.
When you put 
memmap=54M$970M into the kernel line with grub2 in /etc/default/grub and 
run the command sudo update-grub, 
it writes only 'memmap=54MM' into the kernel line.
SO, when you boot, all you get is 54megabytes of usable ram.

ok, thinking how to fix, so i boot the live cd, 
make /boot/grub/grub.cfg writable
edit /boot/grub/grub.cfg to take out 54MM and replace it with 54M$970M

restart and still no good. computer is beating on the hard drive and unresponsive.

so I just want to know what is wrong with the memmap command i tried?
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-03/msg05303.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-03/msg05303.html)

damn bash scripts. :)

You have to quote the $ sign: 54M\$970M in /etc/default/grub.

---

### Post by sdowney717 on 2009-11-28
ok, i will try it before reinstalling.

also, on another pc running grub2 my grub file says this
GRUB_HIDDEN_TIMEOUT_QUIET=true

not false, yet i see the grub menu at boot time. 

The only time i saw the grub menu on the other pc, was when i had installed grub not grub2


> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by sdowney717 on 2009-11-28
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

found a guide, you have to put a # in front of the line

> GRUB_HIDDEN_TIMEOUT=0

    * The menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    * The setting may depend on the presence of other operating systems.

---

### Post by sisco311 on 2009-11-28
You can also try to reinstall grub legacy and run *sudo update-grub* to generate a menu.lst file.It will only create a menu entry for your Ubuntu installation, you will have to add the other OSs manually.

---

### Post by sdowney717 on 2009-11-28
thanks, i got it working with memmap=54M\$970M

I still dont get the grub menu using grub2. No matter what I do!
I tried putting the # sign on the line. but I did not yet run sudo update-grub. I just wanted to see if it would boot properly again.

(edit running update-grub gave me the menu)


Would I use the same memmap=54M\$970M or memmap=54M$970M on the kernel line with legacy grub?

ok for grub2, sudo update-grub may have a bug. running that let me see the menu when the line was commented out,
BUT, it writes in memmap=54M$\970M not what you want which is memmap=54M\$970M
So, you have to edit /boot/grub/grub.cfg by hand to get it to work.


the line memmap=54M\$970M  tells the kernel to ignore memore (reserve, not use) memory starting at 970MB and going for 54MB.
I did this because I have a bad memory module and memtest86 will tell you where it is failing.
Now i can use the module and I only lose 54MB out of 512MB

---

