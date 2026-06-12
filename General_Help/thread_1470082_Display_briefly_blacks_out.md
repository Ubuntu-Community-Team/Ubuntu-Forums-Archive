---
title: "Display briefly blacks out"
date: 2010-05-02
forum: General Help
---

### Post by imbjr on 2010-05-02
This is a regression I used to see way back in 8.10. When totem was started, the screen would black out briefly and then the normal display would resume. Installing the propriety drivers fixed this.

After 8.10, my Radeon X1300 card became unsupported by ATI, but the open-source drivers did a good job. No blacking out.

Now with Lucid, I get the old black outs. They also occur when: 
1) System | Preferences | Monitors is selected.
2) Just after login, ever since Wine was installed.
3) When any Wine-ran application is started.

I installed the radeonhd driver, but that is horribly slow and in some cases I could not reboot into a normal session. When it did work, instead of a black out, there's be a few black bands flicking on the screen.

Googling has not revealed much, in fact my original 8.10 post here appears!

So do I: grit my teeth and bear it, jump back to Karmic, get a new card, or is there a fix?

---

### Post by imbjr on 2010-05-02
Mmm, disabling 3D acceleration:

WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Acceleration disabled

Still makes the screen black out.

---

### Post by imbjr on 2010-05-02
Of note too is whenever this occurs, more is added to Xorg.0.log. It starts with:

(II) RADEON(0): EDID vendor "DEL", prod id 40996
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:

as if the x server was reconfigured/restarted. Googling that idea however did not reveal any info.

---

### Post by imbjr on 2010-05-02
I'm currently trying to use the vesa driver, but ubuntu does not like to boot into that. It refers to it as a low-graphics mode and then lets you login. The right resolution is then set and there's no blacking out.

But ... is there a graceful way of booting up lucid with a vesa driver?

---

### Post by imbjr on 2010-05-02
Well vesa seemed unobtainable. Then I noticed that there was a xorg.conf.failsafe, with the following content:

> 
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fbdev"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


This does the trick. No blacking out when wine apps start.

Video playback:
totem is a little jerky
mplayer will no longer go full screen properly
vlc seems to be the best option so far

Still, tho, this is very unsatisfying.

---

### Post by imbjr on 2010-05-03
Well I tried Fedora 13 beta and it does the same black out!

Looks like I'm going back to Karmic. Hopefully, the Meercat will be better.

---

### Post by Dilutu on 2010-05-03
my display also briefly blacks out when starting a vdo,but oddly it does it only with fglrx driver and using vlc or mplayer.Using totem, only the totem window blacks out.My card is a hd 2600 pro agp....Karmic behaviour was the same as Lucid with fglrx.

---

### Post by imbjr on 2010-05-03
> **Dilutu said:**
> my display also briefly blacks out when starting a vdo,but oddly it does it only with fglrx driver and using vlc or mplayer.Using totem, only the totem window blacks out.My card is a hd 2600 pro agp....Karmic behaviour was the same as Lucid with fglrx.

My card is now too old for fglrx.

In the meantime, I've gone back to karmic. Crippling the video driver in the way I did just did not appeal. I might at some later day attempt a dual boot with lucid to see if any improvements occur.

---

### Post by imbjr on 2010-05-04
Well, I went back to karmic, then I set up a dual-boot with lucid to think about fixing the problem.

Then on reading up on my ATI card I uncovered a kernel boot parameter that fixed the problem:

radeon.modeset=0

At the moment, the only way I can see of applying this setting permanently in GRUB2 is by manually editing the grub.cfg file with:

linux /boot/vmlinuz-2.6.32-21-generic-pae root=/dev/sda8 radeon.modeset=0

but since this file is not meant to be edited by hand, every time there's a kernel update, I'm gonna have to go in there and fix it.

Looking at how GRUB2 generates this file is ... interesting. If I could get my head around how it works I guess I could figure how to inject the option automatically but it is not at all obvious how the commands are built up.

---

### Post by imbjr on 2010-05-04
And finally ...

To get around the fact that the GRUB config file will be overwritten every time the kernel is updated, you can create the file:

/etc/modprobe.d/radeon-kms.conf

with the contents:

options radeon modeset=0

---

### Post by efflandt on 2010-06-08
You should not really tamper with grub.cfg because that will be rewritten after any kernel updates or **sudo update-grub** for any other reason.

You can either put **radeon.modeset=0** (for a USB drive booted on multiple computers to just disable kms for radeon), or more simply **nomodeset** to disable kms for any video, in /etc/default/grub per [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

I had to disable kms for the X1300 in my desktop PC, because kms was sluggish and interfered with suspend/hibernate.  Either nomodeset or radeon.modeset=0 speeds up graphics and fixes suspend/hibernate.

I also had to disable kms for the Mobility X1300 on a laptop, because kms frequently resulted in graphic glitches during boot (lockup with colored pattern at top of screen).

---

### Post by imbjr on 2010-06-10
> **efflandt said:**
> You should not really tamper with grub.cfg because that will be rewritten after any kernel updates or **sudo update-grub** for any other reason.

You can either put **radeon.modeset=0** (for a USB drive booted on multiple computers to just disable kms for radeon), or more simply **nomodeset** to disable kms for any video, in /etc/default/grub per [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

I had to disable kms for the X1300 in my desktop PC, because kms was sluggish and interfered with suspend/hibernate.  Either nomodeset or radeon.modeset=0 speeds up graphics and fixes suspend/hibernate.

I also had to disable kms for the Mobility X1300 on a laptop, because kms frequently resulted in graphic glitches during boot (lockup with colored pattern at top of screen).

Thanks for this extra info, but I did not actually amend grub.cfg, I only created a new conf file with an overriding setting, one that can survive a grub update. So far, it's all been good.

---

### Post by wkulecz on 2010-06-10
Edit as root, /etc/default/grub and add your kernel option to:

GRUB_CMDLINE_LINUX=" splash vga=795"

so it becomes

GRUB_CMDLINE_LINUX=" splash vga=795 radeon.modeset=0"

Then as root run:
update-grub


This is supposed to survive kernel updates and appears to, I needed the option acpi=oldboot.

---

### Post by imbjr on 2011-04-28
Update: Natty Narwhal:

The problem still exists, only this time I can't disable modesetting like I did or I lose all of that Unity "goodness" (still debating whether I can accept some of the changes!).

---

