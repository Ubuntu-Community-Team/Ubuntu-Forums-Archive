---
title: "dual boot ubuntu 11.04 and backtrack5"
date: 2011-08-26
forum: General Help
---

### Post by koxx.dta on 2011-08-26
after using ubuntu demo for a while i finally gave up on windows....while booting windows 7, ubuntu and backtrack 5 worked in windows 7.....i cannot figure out how to dual boot inside ubuntu.....
 linux noob in need, please help

---

### Post by koxx.dta on 2011-08-27
dual boot 2 linux distros? no windows...anyone?

---

### Post by saltmarshlamb on 2011-08-27
If you've already installed ubuntu then you'll need to boot your lovecd/usb and resize the / partition to give enough space from the new install.

Once you've done that you can then install to the new partition. Never even looked at backtrack but I have to assume it gives you the option to install to a specific partition. It's likely that it'd recognise the existing swap so you should only need a single partition to install to.

---

### Post by koxx.dta on 2011-08-27
thanks for reply....just got it.......is there a way to change which os boots automatically

i had ubuntu only now backtrack5 is at the top of the list so that boots auto, any way to switch?

---

### Post by saltmarshlamb on 2011-08-27
Yes there is. 

If you're likely to remove backtrack and leave ubuntu then I would reinstall grub to ubuntu - if you don't and then remove backtrack you'll end up with a grub error. 

However - boot backtrack and edit the grub file 

This assumes that backtrack uses grub2 - if the file opened for editing is empty then it doesn't ;) You'll have to come back.

```
gksudo gedit /etc/default/grub
```

Add this to the bottom 

GRUB_SAVEDEFAULT=true

save and close gedit.

When you reboot pick ubuntu and it will default to that until you change. 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

But - I would be inclined to reinstall grub to ubuntu and then run a grub update from there to pick up backtrack. 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

I've used the boot repair tool recently and reinstalled grub2 from these instructions many times in the past.

---

### Post by koxx.dta on 2011-08-27
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
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
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by saltmarshlamb on 2011-08-27
To clarify

> If you're likely to remove backtrack and leave ubuntugrub was installed by backtrack - if you remove backtrack you will remove grub. 

This will leave you needing to reinstall grub before you do anything else. 

Thus if ubuntu is going to be a constant then I would reinstall grub in ubuntu and then update IT to include backtrack, which should be as simple as running the update command 

```
sudo update-grub
```

---

### Post by koxx.dta on 2011-08-27
starting fresh....installed ubuntu 11.04 works great wanted to dual boot backtrack5 sometimes so installed alongside ubuntu....i use ubuntu 90% of the time so i would like ubuntu to load automatically in grub, 1.98, but right now backtrack is at the top and highlighted so it loads.

for us noob / retards how do i get ubuntu to top of list or make it boot auto when i turn on pc

thanks in advance

---

### Post by saltmarshlamb on 2011-08-27
Reboot into ubuntu - unless you are already there, install bootrepair. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Run bootrepair and let it reinstall grub to the ubuntu drive. 

Further boot repair information - 

[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

Alternatively reinstall grub from the livecd.

[https://help.ubuntu.com/community/Grub2#Methods%20of%20Reinstalling](https://help.ubuntu.com/community/Grub2#Methods%20of%20Reinstalling)

Backtrack is at the top because you are using backtrack grub at the moment.

---

### Post by koxx.dta on 2011-08-27
solved again lol thanks and +1 for easy noobfriendly instructions

---

### Post by saltmarshlamb on 2011-08-27
welcome :)

---

### Post by Gringo.Frenzy on 2011-08-30
Awesome!  This really helped.  I was about to wipe my HDD and try installing BackTrack first, THEN Ubuntu to see if it worked haha :P

Now I just gotta work out how to get rid of the pointless 2nd swap partition I created when installing BT *sigh*

---

### Post by war.ace on 2011-08-31
How do I remove backtrack 5? I've edited my grub to boot ubuntu 10.04 first ( by putting it first on the list). I don't know how to remove backtrack 5. please help.

---

### Post by saltmarshlamb on 2011-09-01
Boot ubuntu livecd/usb.

Use the partition editor to remove the one with backtrack on it. 

If you installed backtrack last and did not reinstall the grub to ubuntu - do so now. 

The links for reinstalling that are in one of the posts above.

---

