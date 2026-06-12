---
title: "Grub 1.97 beta on Karmic not timing out..help please"
date: 2009-11-21
forum: General Help
---

### Post by gordong11 on 2009-11-21
When I boot my machine up, Grub boot loader is not choosing the default OS unless I press it. It normally waits 10 secs and chooses Karmic (which is highlighted still), unless i choose otherwise within that 10 secs.

I have Startup Manager app installed and set to 8 seconds, but that didn't help either.


Then I tried 

gksu gedit /etc/default/grub

and got this output (top 10 lines only)

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

But still not timing out....I did not make changed to this menu, so i did not save it.

Sny ideas?

---

### Post by gordong11 on 2009-11-21
anyone?

---

### Post by Uncle Spellbinder on 2009-11-21
Same here. Just started happening today. Was fine yesterday. No updates applies or changes made.

---

### Post by gordong11 on 2009-11-21
Same thing, was working fine...how weird is that.

---

### Post by Uncle Spellbinder on 2009-11-21
Hmmmmmm. My laptop is now doing the same thing. Two different computers, to dual-boot scenarios (Win 7 and Ubuntu Karmic). I wonder if a new bug has popped up with Grub 2?

---

### Post by Uncle Spellbinder on 2009-11-21
Anyone else with this issue?

---

### Post by gordong11 on 2009-11-21
I re-installed grub2 and still have the issue. That so weird. Totally lost grub in process too.

I had to boot into LiveCD to fix and re-install, and use Gparted to make patition bootable again. Then I had to use Windows DVD to recover my windows boots. was a nightmare. All this and still doesn't time out.

---

### Post by Uncle Spellbinder on 2009-11-21
Well this seems to be turning into something quite nasty. Seems odd that this would start seemingly out of nowhere. I mean there were no recent updates or app installs on my part.  

I'm backing up my important Windows and Ubuntu info ASAP in case.

---

