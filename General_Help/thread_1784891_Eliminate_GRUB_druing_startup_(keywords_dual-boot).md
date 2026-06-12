---
title: "Eliminate GRUB druing startup (keywords: dual-boot)"
date: 2011-06-17
forum: General Help
---

### Post by 3602 on 2011-06-17
I don't know why its called "GRUB 2" while it is actually GRUB 1.98 or 1.99. Anyway.
So here's the thing. Due to the fact that I am dual-booting Ubuntu + Windows XP, my GRUB menu would show up during boot with or without me holding down SHIFT. This takes several seconds. What I'd like to do is that GRUB does not show up at all during "normal" boot and only shows up when I hold down the SHIFT right after BIOS POST.

Also I've successfully flashed my BIOS. So there's that.

Thank you very much.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
gksu gedit /boot/grub/grub.cfg
turn hide menus off

---

### Post by Elfy on 2011-06-17
You'd be better editing /etc/default/grub and running sudo update-grub

If you edit /boot/grub/grub.cfg you'll need to do so each time a call is made to update that file - kernel upgrades for instance.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

I think this line is the one you need to enable, that is remove the #

#GRUB_HIDDEN_TIMEOUT=0

---

### Post by pqwoerituytrueiwoq on 2011-06-17
opps jot the wrong file in my 1st post (i still use legacy grub since grub 2 hates my computers)

---

### Post by Elfy on 2011-06-17
> **pqwoerituytrueiwoq said:**
> opps jot the wrong file in my 1st post (i still use legacy grub since grub 2 hates my computers)

:) Just got back to using grub2 after using grub real myself ...

---

### Post by 3602 on 2011-06-17
> **forestpiskie said:**
> You'd be better editing /etc/default/grub and running sudo update-grub

If you edit /boot/grub/grub.cfg you'll need to do so each time a call is made to update that file - kernel upgrades for instance.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

I think this line is the one you need to enable, that is remove the #

#GRUB_HIDDEN_TIMEOUT=0
Thanks but this line in my grub file is already enabled (un-commented).

EDIT: Just tried SUM. Not enough options. If I change GRUB_TIMEOUT to 0 then even holding down SHIFT won't call it.

---

### Post by Elfy on 2011-06-18
Can you post the whole /etc/default/grub file please.

---

### Post by 3602 on 2011-06-18
> **forestpiskie said:**
> Can you post the whole /etc/default/grub file please.
Right.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1600x900-24,mtrr=3,scroll=ywrap"
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
GRUB_GFXMODE=1600x900-24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by 3602 on 2011-06-19
Bump.

---

### Post by Elfy on 2011-06-19
mmm - looks right to me.

I'll have a think about it and maybe ask someone I know.

---

### Post by drs305 on 2011-06-19
To get the Grub 2 menu not to display, change the timeout in /etc/default/grub to:
> GRUB_TIMEOUT=0

The tricky part is being able to display the menu when the timeout is set to 0. The "SHIFT" key display is activated by a subroutine called "keystatus". Unfortunately, this check is not always incorporated into the Grub configuration file. 

If the keystatus check isn't performed, and you leave the timeout at 0, you won't be able to select another OS, even if you hold down the SHIFT key. Fortunately there is a workaround.

First, make the change to the GRUB_TIMEOUT= line, save the file, then update Grub. Next see if the "keystatus" check is included in /boot/grub/grub.cfg:
```
grep "keystatus" /boot/grub/grub.cfg
```
If you get no return, the 'keystatus' check must be added to the menu. The best way to do this is to add the following to /etc/grub.d/40_custom. That way it will be added to grub.cfg whenever 'update-grub' is run.

Open 40_custom for editing:
```
gksu gedit /etc/grub.d/40_custom
```
Add the following below the existing lines:
> 
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi

Save the file. The file should be executable (it is by default unless you have changed it) and update-grub.
Now run the grep command again to ensure the keystatus check is present in grub.cfg.

Note: Yes, Grub 2 is currently at 1.99 (in Natty), but Grub legacy never got past 0.97 ...  ;-)

Note 2: I'd recommend leaving the timeout at 1 second just so you can stop the menu by pressing a key should the keystatus check not work, but that's just me. What I've posted should do what you want.

---

### Post by Elfy on 2011-06-19
> **drs305 said:**
> complicated grub2 stuffs
Thanks drs305 - saves me thinking or asking you :)

---

### Post by 3602 on 2011-06-19
Thank you drs305! Only if I knew how to program code such as the piece you provided.

---

### Post by drs305 on 2011-06-19
> **3602 said:**
> Thank you drs305! Only if I knew how to program code such as the piece you provided.

To be clear, I certainly didn't write it; I just copied it. My wishes are simpler, such as knowing why the 'keystatus' check isn't *always* included in the grub.cfg file. I understand it may not always be needed, but it would make things so much simpler!

Anyway, hope it's doing what you wanted.

Happy Ubuntu-ing !

---

