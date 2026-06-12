---
title: "Grub resolution wont change with grub_gfxmode"
date: 2010-10-12
forum: General Help
---

### Post by HydroDiOxide on 2010-10-12
Since running Maverick I'm not able to change the resolution of the Grub menu. Below is the output of /etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x800

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Line 8 is there to make the high-res splash work with my prop Nvidia drivers. any ideas on how to fix this?

---

### Post by HydroDiOxide on 2010-10-14
Bump.

Anyone experiencing the same problem, maybe?

---

### Post by HydroDiOxide on 2010-10-16
I noticed some error messages just before the Grub-pc menu loads. The messages are only there for a split-second, so I can read them. Is there a way to log these messages or to let Grub-pc hold on errors maybe?

---

### Post by HydroDiOxide on 2010-10-16
Ok, after pressing PAUSE for about 50 times my timing was good. The error messages are the following:

```
error: no module specified
error: no suitable mode found
error: unknown command 'terminal'
```

I have no idea if one or all of these errors contribute to the problem of not being able to have a 1280x800 grub menu. In Lucid my settings worked fine. Anyone any ideas?

---

### Post by dcstar on 2010-10-16
> **HydroDiOxide said:**
> Ok, after pressing PAUSE for about 50 times my timing was good. The error messages are the following:

```
error: no module specified
error: no suitable mode found
error: unknown command 'terminal'
```

I have no idea if one or all of these errors contribute to the problem of not being able to have a 1280x800 grub menu. In Lucid my settings worked fine. Anyone any ideas?

And you have enabled VESA module mode as per the various HOWTOs on this sort of thing?

---

### Post by HydroDiOxide on 2010-10-16
I don think so. Could you please point me to an HOWTO. Must have missed something.

I put in some lines to get a high-res splash. The posted settings did work on Lucid. but now they seem broken somehow.

---

### Post by spikoley on 2010-10-18
I missed this thread with my initial search and I created one [here]("http://ubuntuforums.org/showthread.php?t=1600233&highlight=GRUB_GFXMODE") regarding the same issue.

I think it is a bug since the OP has this issue and there wasn't an issue with Karmic.  I do run *update-grub* after making the changes.  Another thing I noticed is towards the end of the boot process it switches from the large font to a small one.

What information is needed to trouble shoot it or to submit a bug report?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
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
GRUB_GFXMODE=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by HydroDiOxide on 2010-11-02
Still no fix for this...?

---

### Post by spikoley on 2010-11-02
> **HydroDiOxide said:**
> Still no fix for this...?

We should get another confirmation that this is a bug and then submit a bug report.  Can somebody else test this?

---

### Post by DooBLER on 2010-11-03
Hello.

I have the same issue

I installed the template ([http://retro.apebox.org/grubthemes/directhex-grub-themes-00000010.tar.gz](http://retro.apebox.org/grubthemes/directhex-grub-themes-00000010.tar.gz) like README said) and want to change grub screen resolution.

But the change of GRUB_GFXMODE has no effect. 

My hardware:
MB: ASUS CROSSHAIR IV FORMULA
CPU: AMD Phenom II X6 1090T
Radeon 5850 Asus (EAH5850/2DIS/1GD5/A)

Kernel 2.6.35-22-generic-pae
grub 1.98+20100804-5ubuntu3

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=5
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_THEME=/boot/grub/themes/ubuntu-lucid/theme.txt

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"
```

I think GRUB_INIT_TUNE also don't work

---

### Post by dcstar on 2010-11-04
> **HydroDiOxide said:**
> Since running Maverick I'm not able to change the resolution of the Grub menu. Below is the output of /etc/default/grub:

```

.........
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# **you can see them in real GRUB with the command `vbeinfo'**
..........

```

Line 8 is there to make the high-res splash work with my prop Nvidia drivers. any ideas on how to fix this?

And **exactly** what does that command show when **you** run it at the Grub prompt?

---

### Post by DooBLER on 2010-11-04
Okay.

I think, i have solution.

In file "/etc/grub.d/00_header"

Change line 147, from:
```
set gfxmode=640x480
```
to:
```
set gfxmode=${GRUB_GFXMODE}
```

And it start to work :)

Please someone to submit a bug report,
my english is too weak to do this -_-'

---

### Post by spikoley on 2010-11-07
> **DooBLER said:**
> Okay.

I think, i have solution.

In file "/etc/grub.d/00_header"

Change line 147, from:
```
set gfxmode=640x480
```
to:
```
set gfxmode=${GRUB_GFXMODE}
```

And it start to work :)

Please someone to submit a bug report,
my english is too weak to do this -_-'

Which version of Ubuntu are you running.  I am running 10.10 Maverick Meerkat and it is already is *"set gfxmode=${GRUB_GFXMODE}"*.

/etc/grub.d/00_header
```
if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT_PATH}"` ; then
  set gfxmode=${GRUB_GFXMODE}
  load_video
  insmod gfxterm
fi
```

Can somebody else confirm this?

---

### Post by DooBLER on 2010-11-13
Like I said earlier:

Kernel 2.6.35-22-generic-pae
grub 1.98+20100804-5ubuntu3

10.10 Maverick Meerkat
downloaded and installed on a blank hdd, about 2 weeks ago.

---

### Post by thelibran on 2010-12-25
I got the same trouble and had to install the startup manager from SPM. It works from there but each time I open it and close it, It overwrites /boot/grub/grub.cfg with default menu entries removing all what i edited.

---

### Post by dcstar on 2010-12-25
> **thelibran said:**
> I got the same trouble and had to install the startup manager from SPM. It works from there but each time I open it and close it, It overwrites /boot/grub/grub.cfg with default menu entries removing all what i edited.

That is because **you should not ever** edit /boot/grub/grub.cfg.

---

