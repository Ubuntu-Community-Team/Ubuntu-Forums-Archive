---
title: "grub file empty"
date: 2010-07-12
forum: General Help
---

### Post by mabtifro2 on 2010-07-12
i just upgraded to lucid from jaunty and some of the fn keys stopped working on my eeepc 1005ha. i found instructions to fix that by modifying the etc/default/grub file then updating grub, but my grub file was completely empty when i opened it.

sooooo... yea. what should i do about that?

---

### Post by Exp HP on 2010-07-12
The path should be /etc/default/grub
Make sure to include the initial slash in the filename when opening it, because otherwise it might be trying to open a file that doesn't exist (which will end up as an empty new file).

---

### Post by TechBeastie on 2010-07-12
/etc/default/grub is just a template.  It does seem somewhat odd that the file is totally empty, but the version present on my system doesn't contain anything particularly critical:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

If most /etc/default/grub files look like mine, I'd say a totally blank one isn't anything to worry about.

---

### Post by mabtifro2 on 2010-07-12
> **Exp HP said:**
> The path should be /etc/default/grub
Make sure to include the initial slash in the filename when opening it, because otherwise it might be trying to open a file that doesn't exist (which will end up as an empty new file).



yes, thats what i meant. it is the correct directory



> **TechBeastie said:**
> /etc/default/grub is just a template.  It does seem somewhat odd that the file is totally empty, but the version present on my system doesn't contain anything particularly critical:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

If most /etc/default/grub files look like mine, I'd say a totally blank one isn't anything to worry about.



well im not worried about the blank file, i just want to fix my fn key problem and in order to that based on the instructions for eeepc users, my file needs to contain the same attributes as the others. you see what i mean?

---

### Post by Exp HP on 2010-07-12
On my computer, in addition to /etc/default/grub are two files **/etc/default/grub.ucf-old** and **/etc/default/grub.ucf-dist**.  In fact, I'd consider it perfectly safe to replace the original with the -old one on my system because those two only differ in comments.   I don't know why these files are there, but do you have them?  You could probably copy one to replace /etc/default/grub.

Also, check /etc/default in Nautilus. I'm wondering if the grub file is empty or simply missing.

---

### Post by WorMzy on 2010-07-12
As far as I know, Jaunty used Grub legacy. If this is the case, then when you upgraded the upgrade may have left grub legacy as it is, and skipped the install of Grub2.

Do you have /boot/grub/menu.lst and/or a /boot/grub/grub.cfg? Also, what output do you get if you open a terminal and run 'grub --version'

---

### Post by mabtifro2 on 2010-07-12
> **Exp HP said:**
> On my computer, in addition to /etc/default/grub are two files **/etc/default/grub.ucf-old** and **/etc/default/grub.ucf-dist**.  In fact, I'd consider it perfectly safe to replace the original with the -old one on my system because those two only differ in comments.   I don't know why these files are there, but do you have them?  You could probably copy one to replace /etc/default/grub.

Also, check /etc/default in Nautilus. I'm wondering if the grub file is empty or simply missing.

i dont have either of those files you mentioned. it is possible that /etc/default/grub didnt exist before, and that i created it when i was trying to modify it, but i dont know for sure

> **WorMzy said:**
> As far as I know, Jaunty used Grub legacy. If this is the case, then when you upgraded the upgrade may have left grub legacy as it is, and skipped the install of Grub2.

Do you have /boot/grub/menu.lst and/or a /boot/grub/grub.cfg? Also, what output do you get if you open a terminal and run 'grub --version'

i do have /boot/brub/menu.lst, though i have no cfg files in that directory.

what is the difference between grub legacy and grub2?

thanks for helping me out btw.

---

### Post by Exp HP on 2010-07-12
I myself know little about grub-legacy and grub2, but menu.lst means you have grub-legacy.

**Edit**: Here's a resource for the difference between the two:
[http://www.gnu.org/software/grub/manual/grub.html#Changes-from-GRUB-Legacy](http://www.gnu.org/software/grub/manual/grub.html#Changes-from-GRUB-Legacy)
Also, again, I know little about grub, but from reading that, it seems that the /etc/default/grub file didn't exist in legacy (meaning it's normal that you don't have it).  I say this because /etc/default/grub is used to automatically generate grub2's /boot/grub/grub.cfg.

To sum that all up:  You're following instructions written for Grub 2, and I think that, unfortunately, you need to instead look for instructions written for Grub Legacy if you want to fix the Fn key.  :/

---

### Post by mabtifro2 on 2010-07-12
> **Exp HP said:**
> I myself know little about grub-legacy and grub2, but menu.lst means you have grub-legacy.

**Edit**: Here's a resource for the difference between the two:
[http://www.gnu.org/software/grub/manual/grub.html#Changes-from-GRUB-Legacy](http://www.gnu.org/software/grub/manual/grub.html#Changes-from-GRUB-Legacy)
Also, again, I know little about grub, but from reading that, it seems that the /etc/default/grub file didn't exist in legacy (meaning it's normal that you don't have it).  I say this because /etc/default/grub is used to automatically generate grub2's /boot/grub/grub.cfg.

To sum that all up:  You're following instructions written for Grub 2, and I think that, unfortunately, you need to instead look for instructions written for Grub Legacy if you want to fix the Fn key.  :/

thanks but i find that strange since the instructions were written and successfully executed by users with the same computer and same 10.04 operating system that all lost the fn key functions when they upgraded. so i dont know what to try next...

here are the instructions btw (post #2):

[http://georgia.ubuntuforums.org/showthread.php?t=1466802&highlight=fn+keys+grub](http://georgia.ubuntuforums.org/showthread.php?t=1466802&highlight=fn+keys+grub)

---

### Post by Exp HP on 2010-07-12
I think they probably upgraded from *Karmic*.

I have an interesting idea, though.  Can you please post the contents of your menu.lst?

---

### Post by WorMzy on 2010-07-12
It's probable that the users that enjoyed success with this method did not upgrade, but rather did a fresh install of 10.04. If I were you, I'd edit menu.lst with
```
gksu gedit /boot/grub/menu.lst
``` and add "acpi_osi=Linux" to the end of the kernel line options listed for your 10.04 entry(s) there.

---

### Post by mabtifro2 on 2010-07-12
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6822237d-99aa-418f-8907-91518e8ce577

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid		6822237d-99aa-418f-8907-91518e8ce577
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		6822237d-99aa-418f-8907-91518e8ce577
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid		6822237d-99aa-418f-8907-91518e8ce577
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid		6822237d-99aa-418f-8907-91518e8ce577
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid		6822237d-99aa-418f-8907-91518e8ce577
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid		6822237d-99aa-418f-8907-91518e8ce577
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		6822237d-99aa-418f-8907-91518e8ce577
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Exp HP on 2010-07-12
Alright, I just applied the changes suggested in the topic to my own grub files, and I'm looking at what changed in grub.cfg.  With any luck, I'll be able to figure out what changes you should make to menu.lst.

Or maybe not, but let's hope.

---

### Post by WorMzy on 2010-07-12
> title Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid 6822237d-99aa-418f-8907-91518e8ce577
[COLOR="Red"]kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro quiet splash[/COLOR]
initrd /boot/initrd.img-2.6.32-23-generic
quiet

This is the kernel line.

Add "acpi_osi=Linux" to the end of it, so it'll look like this:

[COLOR="Red"]kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=6822237d-99aa-418f-8907-91518e8ce577 ro quiet splash _acpi_osi=Linux_[/COLOR]

It's not guaranteed to work, but I think there's a good chance it will.

---

### Post by Exp HP on 2010-07-12
[s]Finished looking it over. WorMzy, you're right, the change is that simple.  The lines that say "quiet splash" are indeed the only ones that are changed.  But if you want the change to work regardless of which kernel you use, **you should modify *all three entries *that say "quiet splash"** (when I edited etc/default/grub, all three of my default kernels were changed). You could probably also add it to the ones that say "single" for the recovery modes, but following that guide to a T, those do not get changed.[/s]

See next post.

---

### Post by Exp HP on 2010-07-12
Actually, it looks like the stuff that's in etc/default/grub is actually in the big commented section after BEGIN AUTOMATIC KERNELS LIST.  So I take what I said back.  The safest way to do it would be to just edit this line:

# defoptions=quiet splash

This way, update-grub will work for you rather than against you (if you only edit the kernel lines and leave this alone, I think update-grub would end up undoing your work)

---

### Post by mabtifro2 on 2010-07-12
guys. im speechless. there is almost a tear in my eye im so happy. IT WORKED!!!!!!!!!!!!! i edited just the first kernel wormzy pointed me to, rebooted, and voila!!!

actually whats funny is it works exactly like it used to when i was using the previous version (all fn with the exception of f4 and f7), and when i did the upgrade, f7 was actually working while the other ones were not. now f7 (disables screen) stopped working, which is totally cool since i would never use it anyways. but just thought that was interesting.

i really wish you guys knew how much i appreciate this and how happy you have made me. THANK YOU!!!!!

---

### Post by mabtifro2 on 2010-07-12
> **Exp HP said:**
> Finished looking it over. WorMzy, you're right, the change is that simple.  The lines that say "quiet splash" are indeed the only ones that are changed.  But if you want the change to work regardless of which kernel you use, **you should modify *all three entries *that say "quiet splash"** (when I edited etc/default/grub, all three of my default kernels were changed). You could probably also add it to the ones that say "single" for the recovery modes, but following that guide to a T, those do not get changed.


> **Exp HP said:**
> Actually, it looks like the stuff that's in etc/default/grub is actually in the big commented section after BEGIN AUTOMATIC KERNELS LIST.  So I take what I said back.  The safest way to do it would be to just edit this line:

# defoptions=quiet splash

This way, grub-update will work for you rather than against you (if you only edit the kernel lines and leave this alone, I think grub-update would end up undoing your work)

just saw what you guys wrote. so should i go back and chang the other two also?

---

### Post by Exp HP on 2010-07-12
I suggest only changing the line that says "# defoptions" and then run **update-grub**. This hopefully should properly change the other two.  Back up the file before running the update-grub command, though, just in case.

The reason I suggest changing this line and letting update-grub handle the rest is because it seems that this is the one line you're *supposed* to edit; update-grub uses this line to change the other lines in Legacy. So this way, you won't break the Fn key if you ever need to run update-grub again.

---

### Post by WorMzy on 2010-07-12
If you ever boot into them, sure. It won't do any harm either way.

I'm not sure how 'update-grub' works for grub-legacy (I use grub legacy, but I've never used the command), but Exp HP's suggestion will probably make sure that if you do use 'update-grub', it will re-generate the correct kernel lines for you.

---

### Post by mabtifro2 on 2010-07-12
ok so i backed up the file, then removed "acpi_osi=Linux" from where i originally had it, then modified the  "# defoptions" line, and just ran update-grub, and this is what popped up (check attached screen shot. which option should i choose? should i take the first option then modify the  "# defoptions" line in that one??

---

### Post by WorMzy on 2010-07-12
> should i take the first option then modify the "# defoptions" line in that one?? 

Sounds like the best course of action to me. If it all goes wrong (somehow) just replace the new menu.lst with the backup you made.

---

### Post by Exp HP on 2010-07-12
Eek.  Maybe that's why grub2 made the decision to separate the defaults into a separate file from the current setup?
(though I think you won't need to make the change to defoptions again; from what I understand, update-grub won't change that line)

If you backed up the file, the best option would be the first option.  I'm sure option 1 will work.

[COLOR=Black](If it doesn't work out, though, copy the old file back, *keep* the changes you made to the three kernel lines, and *undo* any  changes you made to the defoptions line. This is the same as the first suggestion I made.  It should work fine for the most part, but you'll need to redo the changes when you  upgrade Linux)[/COLOR]


(I've got to stop being so trigger happy with the edit button...)

---

### Post by mabtifro2 on 2010-07-12
awesome awesome awesome awesomE!!!

so i chose the first option and when i went back to edit the file, i noticed that the  "# defoptions" line as well as ALL THREE lines below had the "acpi_osi=Linux" line added to them. so i did nothing, restarted and its still working perfect.

this case is officially [SOLVED!!!!!!!!!!]

thanks again fellows!

---

