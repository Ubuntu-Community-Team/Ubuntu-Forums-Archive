---
title: "Fresh install of Lucid - Stuck at &quot;GRUB&quot; on first boot?"
date: 2010-09-21
forum: General Help
---

### Post by luciusthecanine on 2010-09-21
Hi all, I'm new  to the forums and Linux. I've been a Windows kiddie since Win3.1 and  have decided to make the change to Open Source after experiencing Ubuntu  on the computers at my local library two year ago.


I've tried to install both 9.10 and 10.04 (one at a time, not dual-boot) via Live CD.

Booting after install gives me the standard Manufacturer logo (HP), then I get "GRUB" text with a flashing Cursor.

I figured this was a prompt, but I can't enter any text.

I figured something got missed during install, so I re-installed and  manually set up partitions for each directory, making sure they all have  enough space allocated to them.

Same result.

I'm confused as to why the system stalls at this point. 
My research here has found some similar issues remedied by reinstalling  Grub to the MBR or running "fsck" command on the Root partition from a  terminal on the live CD. 
I will be trying this tonight and I'll post the results.

Does anyone else have suggestions as to a possible fix?


EDIT:

SPECS:
Older PC - HP Pavillion 502n
Processor - Intel Celeron 1.3gHz
RAM: 256MB of PC133 CL2 (MoBo originally designed for CL3, CL2 runs it faster with no issues I've found)
Output: Onboard Video & Sound.

---

### Post by Rubi1200 on 2010-09-21
Please post your computer specifications such as RAM, disk capacity, and graphics card as a start.

Awaiting your update too.

Thanks.

---

### Post by luciusthecanine on 2010-09-21
edited.

---

### Post by Dustin2128 on 2010-09-21
hm, I do believe that is inadequate for the gnome desktop environment that ubuntu uses by default. I'd install [xubuntu]("http://www.xubuntu.org/"), which is lighter on resources. I know for a fact it'll run on a machine with those specifications, but it might be a bit sluggish. If its too slow for you, you might consider swapping to the [openbox]("http://en.wikipedia.org/wiki/Openbox") desktop environment (can be done after install). It's a bit plain at first, but its insanely customizable. In fact, since you have onboard video in addition to those specs, I would highly recommend openbox over xfce.

EDIT: after a quick lookup, it turns out that your computer *is *below the minimum requirements for a gnome install, though not for xfce.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by luciusthecanine on 2010-09-21
Could have fooled me. Karmic calls for a minimum of 256MB ram on the sleeve of the live CD I received, I didn't check Lucid when I downloaded the ISO however....

I'll go ahead and upgrade the box to it's max capacity of 512MB Ram, I see that's the minimum. from the Ubuntu Wiki.

Even with the requirement issues I can load the live CD for BOTH Karmic and Lucid, but I still can't boot past GRUB on EITHER system install! Does GRUB detect RAM and just lock up when there's not enough to run from the HDD?

---

### Post by gordintoronto on 2010-09-21
With that configuration, you will probably be happier with Lubuntu.

---

### Post by luciusthecanine on 2010-09-23
Haven't had time to mess with Xubuntu yet, that'll probably wait for the weekend.

I did think of something when I woke up this morning though...

I was looking at the hardware the other day and completely failed to note that the 6GB drive is connected to the Master cable on the MoBo, and the 40GB is on the Slave...

When I installed the OS, I put the Root partition on the Slave drive. Looking at the boot order in my BIOS, I can see the primary Boot drive is the 6Gig...

This raises the question:
Could GRUB be looking for the partition on the wrong drive since Root is on the Slave drive, and therefore not finding an OS to boot up?

I'm going to swap the cables and try again... maybe with a fresh install of Kubuntu with Openbox or straight Xubuntu, since both run lighter than Ubuntu.

---

### Post by perspectoff on 2010-09-23
Graphics card? Most booting problems are due to Graphics incompatibilities.

I think your model has integrated Intel graphics. There are many threads on Ubuntu forums, now, about tweaking Intel integrated graphics for Lucid. Search for some of them.

Tweaks are needed, especially in Lucid (but also Karmic, for some users).

Although you can run a full desktop in 256 Mb RAM (maybe), the specs generally recommend 384 Mb RAM minimum for Ubuntu and Kubuntu. It is pretty painful if you don't. However, I would concentrate on solving the graphics problem, first, then trying again. If you find it painfully slow, try one of the others.

Try Lubuntu (runs in as little as 160 Mb RAM), Puppy (256 Mb RAM), or Xubuntu (256 Mb RAM), for example.

Lubuntu has a minimal installation option that requires less hard drive space for installation, too, (as does Puppy, I believe). If you are intending to install on the 6 Gb hard drive, you'd be wanting that.

Not a problem on the 40 Gb hard drive, of course.

---

### Post by luciusthecanine on 2010-09-27
I decided to start from scratch.

Installed XP on the 6Gig drive and Xubuntu on the 40gig.

Swapped cables so 40Gig drive was on Master end.

Booted up straight to XP - no GRUb screen.

First thing that came to mind: BIOS is booting from 6Gig as Primary Boot Drive regardless of cable selection.

Rebooted, hit the BIOS setup and sure enough - 6Gig was primary HDD.

Changed to 40Gig as Primary Boot Drive.

Rebooted

BEAUTIFUL GRUB SELECTION SCREEN!

Loaded Xubuntu 10.04 - took awhile due to lack of Memory. I'll fix that in time. :D

Ran some 218 updates. :D :D

Haven't touched it since... lol I'm a busy guy apparently.

I guess all this took was a little common sense and general knowledge of how the Boot Process works.

Thanks for the help guys.

@perspectoff, thanks for the tip, I'll look into that graphics issue, as the 

ANOTHER PROUD OWNER OF A LINUX MACHINE!!!


:guitar:

---

