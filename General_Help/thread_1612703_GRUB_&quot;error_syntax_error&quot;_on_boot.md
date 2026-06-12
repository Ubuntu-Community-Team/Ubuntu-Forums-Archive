---
title: "GRUB &quot;error: syntax error&quot; on boot"
date: 2010-11-03
forum: General Help
---

### Post by Xorlathor on 2010-11-03
Whenever I boot my laptop, I get the following three lines:

```
error: syntax error.
error: Incorrect command.
error: syntax error.
```

Right after I see the error messages for a couple seconds, the boot screen shows up and the rest of the boot progresses as normal. I'm on a Wubi 10.10 ubuntu install and I'm pretty sure this error has something to do with the GRUB_TIMEOUT line on 'etc/default/grub' file.

I was experiencing some weird glitches with the boot splash screen (it was in the wrong resolution and would not display some times) so I edited that file to make it work. Here is the file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=Red]_**GRUB_TIMEOUT=0**_[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
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
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

When I set GRUB_TIMEOUT to 5, I don't get the error messages on boot. Any help in this problem would be *greatly* appreciated. Thanks!

---

### Post by sikander3786 on 2010-11-03
Don't set it to 0. You need to set that to 1 or higher. Explained here.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

---

### Post by Xorlathor on 2010-11-03
> **sikander3786 said:**
> Don't set it to 0. You need to set that to 1 or higher. Explained here.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

If I set it to 1, doesn't it make it show the GRUB menu for 1 second?

I installed Ubuntu by Wubi, so I can choose whether to boot into Windows 7 or Ubuntu via the Windows bootloader (which appears before the GRUB menu in my boot).

I dont' want to see the GRUB bootloader at all - how can I do this?

---

### Post by Quackers on 2010-11-03
I'm just guessing here but shouldn't
mode_option=1280x1024-24 be
mode_option=1280x1024x24
or am I wrong?

---

### Post by Xorlathor on 2010-11-03
> **Quackers said:**
> I'm just guessing here but shouldn't
mode_option=1280x1024-24 be
mode_option=1280x1024x24
or am I wrong?

When I set it to 1280x1024x24, I get a weird greenish-colored screen with horizontal lines instead of the regular boot screen animation. The other way (1280x1024-24) works fine.

---

### Post by Quackers on 2010-11-03
Oh dear! Sorry about that, but it just looked odd to me. Ignore me, I'll eventually go away :-)

---

### Post by Xorlathor on 2010-11-03
> **Quackers said:**
> Oh dear! Sorry about that, but it just looked odd to me. Ignore me, I'll eventually go away :-)

Haha no problem, I just changed the line back and everything's fine now - except for the original problem. Any ideas on how to fix it?

---

### Post by Quackers on 2010-11-03
Unfortunately not. I am unfamiliar with wubi installs and I would not like to give dodgy information!
You know what the doctors say - first do no harm! :-)

---

### Post by Xorlathor on 2010-11-03
> **Quackers said:**
> Unfortunately not. I am unfamiliar with wubi installs and I would not like to give dodgy information!
You know what the doctors say - first do no harm! :-)

I don't think this is a Wubi-specific problem, but more a problem of GRUB.

---

### Post by sikander3786 on 2010-11-03
From the link in my previos post, it states,

> GRUB_HIDDEN_TIMEOUT=0 on single operating system computers.

    * No menu is displayed. The system is immediately booted to the default OS.
    * This is the default setting with only one identified operating system.
          o

            To display the menu under this condition, place a # symbol at the start of the line and ensure the GRUB_TIMEOUT setting is a positive integer. 
    *

      If the value is set to 0, a keystatus check is performed to determine if the SHIFT key is depressed. If GRUB 2 determines the SHIFT key is depressed during the boot process, the menu will be displayed. This gives the user a method of interrupting an automatic boot which would normally not display the menu. 

So all you need to do is set GRUB_HIDDEN_TIMEOUT=0, GRUB_TIMEOUT=5 or 10 and then run

```
sudo update-grub
```

Starup manager is another option.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by gabrielwangbati on 2010-11-11
> **sikander3786 said:**
> From the link in my previos post, it states,



So all you need to do is set GRUB_HIDDEN_TIMEOUT=0, GRUB_TIMEOUT=5 or 10 and then run

```
sudo update-grub
```

Starup manager is another option.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
I think I had exactly the same issue with Xorlathor, the problem shows up after the update to 10.10. By default, my **GRUB_HIDDEN_TIMEOUT=0** and **GRUB_TIMEOUT=10**(as I tried simply modify it to 5 and update won't give me the expected result), but I still have the syntax error and incorrect command error.

---

### Post by MartyMacGyver on 2011-03-14
> **Xorlathor said:**
> Whenever I boot my laptop, I get the following three lines:

```
error: syntax error.
error: Incorrect command.
error: syntax error.
```Right after I see the error messages for a couple seconds, the boot screen shows up and the rest of the boot progresses as normal. I'm on a Wubi 10.10 ubuntu install and I'm pretty sure this error has something to do with the GRUB_TIMEOUT line on 'etc/default/grub' file.
.....
Any help in this problem would be *greatly* appreciated. Thanks!

GRUB_TIMEOUT probably doesn't have a thing to do with this particular sequence of errors. I'm running 10.10 (just upgraded from 10.04) in a VMWare VM and this boot thing was bothering me, so I've been investigating this problem for a little while tonight.

Does the file */boot/grub/**video.lst* have anything in it? Is it even present? That was the root cause for me.

Now look at */boot/grub/grub.cfg*. I had the following (even after re-generating the file repeatedly):[INDENT]```
function load_video {
}
``` [/INDENT]From what I can see this is generated by */etc/grub.d/00_header*. Apparently, if video.lst is absent or empty that's what you get... and apparently it's bogus (in the sense that it's throwing the errors you see). *Something* must be present between the braces... simply having an echo in there was enough to fix it during my initial testing.[INDENT]```
function load_video {
   echo BLAH
}
``` [/INDENT]Of course what this REALLY needs is "insmod" lines with the appropriate video info. (Perhaps it would be useful to have an error check in */etc/grub.d/00_header *so that a more verbose error is generated when video.lst is absent or empty... but this may be just a weird boundary case for those of us who've upgraded in-place a few times.)

[B]_Solutions:_

[/B]
[LIST]
[*]You can create a *video.lst* file (using *sudo touch /boot/grub/video.lst*) and populate it with some appropriate entries (*vbe* and *vga* on separate lines should do for a start), then run *sudo update-grub* to re-generate */boot/grub/grub.cfg *(take a look afterward and you should see some *insmod* lines in the *load_video* function now.)
[/LIST]

[LIST]
[*]_**Or**_ you can reinstall grub (*sudo grub-install /dev/ZZZ* where *ZZZ*=your boot drive, such as *sda*) which will populate the *video.lst* file, and then run *sudo update-grub* to ensure */boot/grub/grub.cfg *is generated correctly. **Be sure you know what you're doing before you do this as it modifies the MBR.**
[/LIST]
After all this */boot/grub/grub.cfg* should have a block like this, and those three errors should no longer appear on boot:[INDENT]```
function load_video {
  insmod vbe
  insmod vga
}
```[/INDENT]

---

### Post by bcbc on 2011-03-15
In natty, they've modified 00_header so that it inserts "true" if it's empty...

i.e.
```
function load_video {
    true
}
```

That's required in Natty because if it fails a syntax check it won't generate the grub.cfg at all (or at least alpha2 was doing that)

---

### Post by MartyMacGyver on 2011-03-16
> **bcbc said:**
> In natty, they've modified 00_header so that it inserts "true" if it's empty...

i.e.
```
function load_video {
    true
}
```That's required in Natty because if it fails a syntax check it won't generate the grub.cfg at all (or at least alpha2 was doing that)

Thanks for the info! I wonder if that change will get backported? At least it doesn't lead to a failure case in Maverick.

---

